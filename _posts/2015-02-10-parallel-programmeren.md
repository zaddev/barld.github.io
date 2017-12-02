---
id: 18
title: Parallel programmeren introductie
date: 2015-02-10T10:24:51+00:00
author: Barld Boot
layout: post
guid: http://barld.nl/?p=18
permalink: /18/parallel-programmeren/
videourl:
  - ""
categories:
  - parallel
tags:
  - introductie
  - parallel
  - programing
---
**Parallel programmeren is een techniek die nog vrij nieuw is voor mij maar ik zeer zeker erg interessant vind. Ik wil hier verder behandelen wat het in de basis is, welke voor en nadelen ik er van zie en hoe je het zou kunnen toepassen. Nog opmerkingen of aanvullingen? Laat vooral een reactie achter.**

## Hoe gaat “normaal” programmeren?

Normaal gesproken wordt je programma serieel uitgevoerd. Dit betekent in de basis gewoon dat je code bovenaan begint en zich dan naar beneden werkt. Het gaat hierbij niet om de volgorde waar het staat in je source code maar vooral om de volgorde van de flow van je programma die je hebt gedefinieerd. Er wordt dan dus altijd maar een ding tegelijk uitgevoerd Als het statement is uitgevoerd wordt er pas naar het volgende statement gegaan om uit te voeren.

## Wat is parallel?

In de meetkunde betekent dat dat twee dingen evenwijdig aan elkaar lopen. In programmeren is er iets meer vrijheid en ligt de nadruk vooral op meerdere dingen tegelijkertijd. Hierdoor zou je dingen die je uitvoert kunnen versnellen. Als we het even gaan vergelijken met iets in de praktijk dan neem ik auto’s. Als ik van locatie A naar locatie B moet dan kan ik daar die auto voor nemen en ben ik na een bepaalde tijd hopelijk op locatie B. Stel dat ik sneller op locatie B wil wezen dan heb ik geen voordeel om twee auto’s te nemen. Het betekent gewoon dat er een chauffeur met een voor de rest lege auto achter je aan rijdt. Het kost je alleen meer geld en tijd omdat je ook nog een extra auto moet regelen en betalen. Dit nadeel veranderd uiteraard natuurlijk weer als je met een aantal vrienden gaat waardoor je net niet in één auto past. In dat geval zou de extra auto wel tot drie keer zo snel kunnen wezen omdat de auto ook nog terug zou moeten rijden.

En nu meer in de praktijk: veel moderne computers hebben tegenwoordig een Dual of Quad core processor. Om hier optimaal gebruik van te maken zal je soms dus moeten gaan kijken naar parallel programmeren. Let hier op dat het ook gebruikt kan worden om veel verschillende taken uit te voeren. Denk hierbij bevoordeeld dat je muziek aan het luisteren bent op de computer en ondertussen ben je ook nog een blog aan het schrijven en is Windows bezig met updates. Windows zorgt in dit geval dat de beschikbare resources netjes worden verdeeld over de programma’s die het nodig hebben hier hoef je als programmeur zelf niet perse rekening mee te houden. Een ander nog simpel voorbeeld waarbij je er wel rekening mee moet houden is als je een programma hebt die soms langere tijd bezig is denk hierbij bijvoorbeeld dat er bestanden gedownload moet worden. Om te voorkomen dat je programma niet meer op andere dingen reageert omdat het bezig is met het downloaden van bestanden kan je dit parallel uitvoeren ten opzichte van de grafische interface. Het is ook mogelijk om bepaalde taken die erg rekenintensief zijn te verdelen over meerdere kernen. Er komen hier wel verschillende dingen kijken om dit goed te kunnen doen, ik hoop hier later een keer op terug te komen.