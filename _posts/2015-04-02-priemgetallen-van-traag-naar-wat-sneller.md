---
id: 49
title: priemgetallen van traag naar wat sneller
date: 2015-04-02T21:34:29+00:00
author: Barld Boot
layout: post
guid: http://barld.nl/?p=49
permalink: /49/priemgetallen-van-traag-naar-wat-sneller/
videourl:
  - ""
categories:
  - parallel
tags:
  - 'C#'
  - parallel
  - priem
  - priemgetallen
  - tpl
---
Een priemgetal, in principe hele normale getallen behalve dan dat het de eigenschap heeft dat het alleen maar deelbaar is door zichzelf en door één. Toch vind ik het wel leuke getallen om wat mee te doen op websites als ProjectEuler wordt er regelmatig mee gewerkt en het is ook relatief makkelijk om er iets voor te programmeren. In deze blog wil opbouwen door te beginnen met algoritmes die zeer slecht scoren en dit steeds iets te verbeteren en daar uitleg bij te geven. Het laatste algoritme wil ik parallel maken met behulp van de TPL library van Microsoft.
  
Zoals ik al eerder zei is het niet zo moeilijk om priemgetallen te bereken. Je gaat alle getalen waarvan je het wil weten langs en kijkt of het niet deelbaar is door een getal dat lager is dan dat getal. Hieronder de makkelijkste uitwerking die ik kon bedenken

```cs
public List<int> Method1(int below)
{
    var priems = new List<int>();
    for (int i = 2; i < below; i++)
    {
        bool isPriem = true;
        for (int j = 2; j < i; j++) 
        {
            if (i % j == 0)
            {
                isPriem = false;
                break;
            }
        }
        if(isPriem)
        {
            priems.Add(i);
        }
    }
    return priems;
}
```

Zoals hierboven al beschreven staat zit dit vrij makkelijk in elkaar je hebt twee loops in elkaar de buitenste gaat alle getallen langs van 2 tot waar je de priemgetallen wilt hebben. In de tweede loop wordt vervolgens voor alle getallen die hieronder zitten gekeken of het een restwaarde heeft als je het probeert te delen. Zo nee dan is het geen priemgetal en kan je dus stoppen. Met deze methode kan ik op mijn laptop alle priemgetallen vinden onder de 70 000 in één seconde. 

Hier valt een makkelijke verbetering aan door te voeren. Als we de eerste paar priem getallen bekijken ({2,3,5,7,11,13,17,19}) dan valt op dat alle priemgetallen met uitzondering van de eerste oneven is. Als we de 2 handmatig aan de verzameling toevoegen kunnen we in het vervolg in onze iteraties alleen nog maar de oneven getallen langs gaan. Dit is natuurlijk logisch omdat alle even getallen deelbaar zijn door 2. Zie hieronder voor de verbeterde methode.


```cs
public List<int> Method2(int below)
{
    var priems = new List<int>();
    priems.Add(2);
    for (int i = 3; i < below; i+=2)
    {
        bool isPriem = true;
        for (int j = 3; j < i; j+=2)
        {
            if (i % j == 0)
            {
                isPriem = false;
                break;
            }
        }
        if (isPriem)
        {
            priems.Add(i);
        }
    }
    return priems;
}
```

Met deze voor de rest niet veel schokkende veranderingen heb ik op mijn laptop uiteindelijk kunnen bereiken dat alle priemgetallen onder de 100 000 konden worden berekend in één seconden in plaats zo’n 70 000.
  
Een tweede en veel grotere performance verbetering valt te bereiken als we gebruik maken van het wiskundige feit dat als een getal niet deelbaar door een getal lager dan de wortel van getal dat je wilt checken. Als je boven deze waarde komt en nog niks hebt gevonden dan kan je stoppen met controleren en het noteren als priemgetal. Laten we het getal 1 miljoen als voorbeeld nemen. De wortel hiervan levert 1000 op. Dit betekent dus dat we bij 1000 kunnen stoppen. Hoe groter het getal is ook hoe meer winst je kunt maken met deze truc. Zie hieronder de verbeterde methode.

```cs
public List<int> Method3(int below)
{
    var priems = new List<int>();
    priems.Add(2);
    for (int i = 3; i < below; i += 2)
    {
        bool isPriem = true;
        int sqrt = (int)Math.Sqrt((int)i)+1;
        for (int j = 3; j < sqrt; j += 2)
        {
            if (i % j == 0)
            {
                isPriem = false;
                break;
            }
        }
        if (isPriem)
        {
            priems.Add(i);
        }
    }
    return priems;
}
```

De toevoeging ten opzichten van de vorige methode is dat er telkens voor ieder getal dat er bekeken gecontroleerd wordt berekent wordt wat de wortel is. Met deze waarde wordt vervolgens in de for loop gekeken of er al gestopt moet worden. Hierdoor zal bij priemgetallen een stuk minder onnodig “geloopt” worden. Dit heeft uiteindelijk een enorme performance verbetering opgeleverd waar ik eerst alle getallen onder de 100 000 kon bepalen in een seconden is dat nu mogelijk voor alle priem getallen onder de 3,7 miljoen.
  
Zonder hier al te veel veranderingen op toe te passen kon ik nog een verbetering toepassen. Deze verbetering heeft er mee te maken dat je alle priem getallen die je al heb berekent onthoud. Alle niet priemgetallen zijn deelbaar door minstens 1 priemgetal. Dus in plaats van alle oneven getallen langs te lopen hoef je alleen nog maar alle voorgaand berekende priemgetallen langs te gaan om te kijken of het deelbaar. Hieronder zie je de verbeterde versie.

```cs
public List<int> Method4(int below)
{
    var priems = new List<int>();
    priems.Add(2);
    for (int i = 3; i < below; i += 2)
    {
        bool isPriem = true;
        int sqrt = (int)Math.Sqrt((int)i) + 1;

        foreach(var priem in priems)
        {
            if (priem > sqrt) break;
            if (i % priem == 0)
            {
                isPriem = false;
                break;
            }
        }
        if (isPriem)
        {
            priems.Add(i);
        }
    }
    return priems;
}
```

Je ziet dat hier de binnenste for loop wordt vervangen door een foreach loop. De check om te kijken of je al over de grens ben van wortel van i bent wordt in een if eronder gegooid met een break er achter. Deze verandering levert nog een flinke verbetering op want we gaan van alle priemgetallen onder de 3,7 miljoen naar alle priemgetallen onder de 4,6 miljoen in 1 seconde.
  
De laatste verbetering van het algoritme heeft mij vrij veel moeite gekost. Toen ik een toenemende interesse kreeg in parallel programmeren dacht ik het zou toch mooi zijn als ik voor zo’n vrij zware berekening gebruik kan maken van de complete processor in plaats van één van de 8 virtuele threads op mijn laptop. Door dat mijn laatste algoritme afhankelijk is van dat het op volgorde wordt uitgevoerd kan ik het niet zomaar parallelliseren en zal er het een en ander moeten veranderen. Uiteindelijk heb ik het weten op te delen door het feit dat als je eenmaal een bepaald aantal priemgetallen hebt daarmee alle priemgetallen kan bereken tot het hoogste bekende priem getal in kwadraat. Hieronder is de deze versie uitgewerkt met behulp van de TPL library.

```cs
private IEnumerable<int> GetRange(int from, int to)
{
    for (int i = from; i <= to; i += 2)
        yield return i;

}

public List<int> Method5(int tot)
{
    List<int> PriemList = new List<int>(new int[] { 2, 3, 5, 7 });
    object priemLock = new object();
    do
    {
        PriemList.Sort();
        int[] IteratePriems = PriemList.ToArray();
        //stop
        var lpriem = IteratePriems.Last();
        int stop = lpriem * lpriem;
        if (stop > tot || stop < 0)
        {
            stop = tot;
            int sqrt = (int)Math.Sqrt(tot) + 1;
            IteratePriems = IteratePriems.Where(x => x <= sqrt).ToArray();
        }

        Parallel.ForEach(GetRange(PriemList.Last() + 2, stop), (i) =>;
        {
            bool isPriem = true;
            int sqrt = (int)Math.Sqrt((int)i) + 1;
            foreach (int priem in IteratePriems)
            {
                if (priem > sqrt) break;
                if (i % priem == 0)
                {
                    isPriem = false;
                    break;
                }
            }
            if (isPriem)
            {
                lock (priemLock)
                {
                    PriemList.Add(i);
                }
            }
        }
        );

        if (stop == tot)
            break;
    }
    while (true);

    return PriemList;
}
```

Deze blog wordt waarschijnlijk te langdradig als ik hier iedere regel stuk voor stuk doorneem. Als je zo kijkt zal je waarschijnlijk wel opvallen dat de code die binnen de Parallel ForEach staat vrijwel hellemaal hetzelfde is behalve dan dat er rekening wordt gehouden met data racing en om dat tegen te gaan gebruik wordt gemaakt van locking. Door dit parallelle algoritme kon ik op mij laptop uiteindelijk alle priemgetallen onder de 13 miljoen bereken in een ongeveer een seconde. Dit is nog lang niet de verbetering van 8 keer die je in theorie zou moeten kunnen halen met 8 hreads maar het gebruik van dit threading heeft ook wel wat overhead. Als je de aantallen verhoogd dan is mijn verwachting dat de verschillen in verhouding nog verder nog zullen stijgen. Dit mede omdat de taken steeds wat groter worden en je dus minder hoeft te synchroniseren. Als er interesse voor is dan wil ik een stuk parallelle code nog wel een keer doornemen in een blog regel voor regel. Ik hoop dat jullie het interessant vonden en als er nog vragen zijn dan hoor ik dat graag.