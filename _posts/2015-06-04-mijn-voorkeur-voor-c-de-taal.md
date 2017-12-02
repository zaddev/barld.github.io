---
id: 61
title: 'Mijn voorkeur voor C# de taal'
date: 2015-06-04T22:39:59+00:00
author: Barld Boot
layout: post
guid: http://barld.nl/?p=61
permalink: /61/mijn-voorkeur-voor-c-de-taal/
videourl:
  - ""
categories:
  - Geen categorie
tags:
  - 'C#'
---
In mijn vorige blog post ging het al over mijn voorkeuren voor de taal C#. In dat bericht ben ik echter helemaal niet ingegaan over de eigenschappen van de taal zelf, dit wil in dit bericht wel doen. Ook wil ik hier geen vergelijking aangaan met één andere taal maar uit gaan van de sterke punten van C#.

## Statically typed

Een belangrijke eigenschap van C# is dat het statically typed is. Voor mensen die net beginnen met programmeren is een taal die deze eigenschap bezit kan het soms erg vervelend en lastig zijn als je overal moet aangeven wat  voor type het is maar als je het eenmaal gewend bent valt dit allemaal erg mee. Omdat bijna alles van te voren is gedefinieerd is het voor editors veel makkelijker om op een goede manier tijdens het typen je de mogelijkheden te laten zien wat je mogelijkheden zijn (auto intellisense). Dit kan vooral handig zijn als je werkt met objecten die je niet zelf heb gedefinieerd of regelmatig hebt gebruikt. Het voorkomt dat je telkens uit de flow raakt omdat je weer de documentatie in moet duiken om te kijken hoe iets werkt. Liever schrijven we natuurlijk allemaal nieuwe code maar af en toe moeten we ook wel eens code lezen van een ander of van ons zelf wat we al een tijd geleden hebben geproduceerd, bij het lezen van deze code is het ook een vorm van documentatie. Het is uiteraard nog steeds belangrijk dat er goed wordt nagedacht voor goede benamingen van je methodes en variabele maar het kan toch wat bijdragen als je weet van wat voor type je variabele is. Het laatste wat ik hierover wil zeggen is dat op het moment van compileren al je code nagekeken of je code wel type safe is en kunnen er eventueel optimalisaties worden toegepast.

## Propperties

Het missen van propporties in veel talen vind ik echt een gemis en ik ben blij dat ik dit niet hoef te missen binnen C#. Propperties bieden je de mogelijkheid om je code erg elegant te houden. Een van de concepten binnen OOP programmeren is encapsulation. Dit houd in dat je je fields in je object zoveel mogelijk private moet houden en ze toegankelijk moet gaan maken met get en set methodes ook al pas je op dat moment nog geen check toe en ga je dit misschien ook nooit doen. Hieronder een heel basis voorbeeldje waarin de voordelen van propperties duidelijk naar voren komt.

<pre class="brush: csharp; title: ; notranslate" title="">class Program
{
    class PersonWithPropperties
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }

    class PersonWithoutPropperties
    {
        private string name;
        public int age;

        public PersonWithoutPropperties()
        {
        }
        public PersonWithoutPropperties(string name, int age) : this()
        {
            this.name = name;
            this.age = age;
        }

        public string GetName()
        {
            return name;
        }
        public void SetName(string name)
        {
            this.name = name;
        }
        public int GetAge()
        {
            return age;
        }
        public void SetAge(int age)
        {
            this.age = age;
        }

    }
    static void Main(string[] args)
    {
        //construct objects
        PersonWithPropperties person1 = new PersonWithPropperties { Name = "Barld", Age = 20 };//longer to write but more flexible
        PersonWithoutPropperties person2 = new PersonWithoutPropperties("Barld", 20);//shorter to write

        //it's my birhtday!
        person1.Age++;
        person2.SetAge(person2.GetAge() + 1);

    }
}

</pre>

Zoals ik hier in het bovenstaande voorbeeld liet zien zorgt het bij simpele code zoals voor een stuk minder code en het blijf vooral overzichtelijker zodat je je kan richten op de belangrijke zaken binnen je code. Een ander punt is dat bij het gebruik van propperties het is toegestaan om propperties direct te kunnen manipuleren.

## overloading

Het overloaden van methodes en constructors is niet een unieke functionaliteit wat alleen maar in C# voorkomt maar toch wel zeker fijn dat het er in zit. Je kan het gebruiken voor extra opties of voor ecapsulation zodat je calls van buiten je class of libary nog eens een keer extra kan controleren voor dat je het doorstuurt naar de interne of private method.  Mijn advies echter wel zorg er altijd voor dat de methodes het zelfde doel hebben anders zal je programma al snel onduidelijk worden.

## events

C# heeft vind ik een erg goede implementatie van events. Het heeft mij bijvoorbeeld in staat gesteld om met behulp van event driven ontwerp de logica van boter, kaas en eieren(<a href="https://github.com/barld/BoterKaasEnEieren" target="_blank">source</a>) op een een goede en mooie manier kunnen scheiden vind ik zelf. In de code van frontend winform applicatie kon ik op die manier makkelijk naar bepaalde events luisteren en relevante informatie gebruiken om de gebruikers wat te laten doen of tonen. Later wou ik hier nog een simpele bot voor maken als tegenstander. Op een paar regels na dat ik de bot moest activeren heb ik hier eigenlijk geen regels code voor hoeven aanpassen in mijn frontend of backend logica door de architectuur die ik hiervoor heb gebruikt kon de bot gewoon meeluisteren naar de events.

uiteraard zijn er nog een hoop andere functionaliteiten waardoor ik de taal C# zo&#8217;n prettige taal vind. Ik ga deze niet meer in deze post behandelen maar wil nog wel een vervolg geven aan deze serie.