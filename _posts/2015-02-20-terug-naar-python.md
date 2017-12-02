---
id: 28
title: Terug naar Python
date: 2015-02-20T16:28:11+00:00
author: Barld Boot
layout: post
guid: http://barld.nl/?p=28
permalink: /28/terug-naar-python/
videourl:
  - ""
categories:
  - Geen categorie
tags:
  - 'C#'
  - Project Euler
  - python
  - vergelijking
---
Python is de taal geweest waar ik aan het einde van de middelbare school mijn eerste regels programeer code heb geschreven. Het was toen leuk om te doen maar mijn mogelijkheden om er toen dingen mee te doen waren beperkt. Toen ik vervolgens ben begonnen met mijn beroepsopleiding ben ik niet actief verder gegaan met deze taal maar ik heb de interesse nooit compleet verloren. Ik blijf het wel een leuke en mooie taal vinden om mee te werken. Zo ook laatst ben ik weer eens wat gaan doen met Python dat inmiddels op versie 3.4 zit.

Er zijn verschillende bronnen die je kan gebruiken om python te leren of je kennis weer wat op te frissen. Een website die ik erg mooi vind is http://cscircles.cemc.uwaterloo.ca/ deze website is ontwikkeld door mensen op de Canadese “university of Waterloo” en is ook erg toegankelijk voor beginners. Toen ik deze website laatst weer bezocht kwam ik er zelfs achter dat ze een goede Nederlandse vertaling hebben.

Ik wist niet zo goed wat ik moest maken dus heb ik een makkelijke opdracht van “Project Euler” gemaakt als Console programma gemaakt. Ik heb het ook in C# gemaakt en zal hieronder de code vergelijken.

```python
#Problem 1 Project Euler Python
Som = 0

for i in range(3, 1000):
    if (i % 3 or i % 5) == 0:
        som += i

print(som)
```


```cs
//Problem 1 Project Euler C#
using System;

namespace p1
{
    class Program
    {        
        static void Main(string[] args)
        {
            int sum = 0;
            for (int i = 1; i < 1000; i++)
            {
                if (i % 3 == 0 || i % 5 == 0)
                {
                    sum += i;
                }
            }
            Console.WriteLine(sum);
        }
    }
}
```

Een van de eerste dingen die mij mij opvalt is dat python het gewoon toestaat om bij zo'n klein klein stukje het gewoon toestaat om niks te doen met OOP. OOP is een hele mooie techniek die overigens ook mogelijk is met behulp van python, maar het heeft bij zo'n klein programmaatje geen meerwaarde om er een class om heen te zetten. daarnaast valt op dat in mijn python code veel minder haakjes worden gebruikt en dat dubbele punt en inspringen vaak genoeg is. Een van de echte grootte opvallende verschillen is dat er in python geen klassieke for loop zit zoals die in veel andere talen wel zit. De for loop die in python zit is eigenlijk een soort foreach loop in veel andere talen. wanneer je een for loop wilt gebruiken dan zal je vaak genoeg hebben door de for loop te gebruiken in combinatie met de range methode maar het kan soms toch iets beperkter zijn. Om voorwaarden te checken heb ik ook nog een hele mooie mogelijkheid gevonden die ik in ieder geval voor C# niet zou weten zonder extra methodes. Je kan op een korte wijze heel makkelijk checken of een van beide waardes overeen komt met in dit geval 0.

Dit is een vergelijking aan de hand van een klein probleem. Ik zou in de toekomst graag nog eens meer iets willen doen met Python maar heb op dit moment niet zoveel ideeën om nou eens te maken in python. Als iemand iets leuks weet of een opmerking over iets anders in dit bericht heeft laat dan gerust een reactie achter.