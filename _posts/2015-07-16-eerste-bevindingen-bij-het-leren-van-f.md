---
id: 91
title: 'Eerste bevindingen bij het leren van F#'
date: 2015-07-16T22:18:32+00:00
author: Barld Boot
layout: post
guid: http://barld.nl/?p=91
permalink: /91/eerste-bevindingen-bij-het-leren-van-f/
videourl:
  - ""
categories:
  - 'F#'
tags:
  - 'f#'
  - leren
---
Ik ben nu een korte tijd bezig met het leren van de voor mij nieuwe programeer taal F#.  Er valt voor mij nog veel te leren binnen het functioneel programmeren met behulp van F# maar ik wil hier alvast mijn eerste bevindingen delen die mij zijn opgevallen tijdens het leren van F#.

### Immutable

Met F# en schijnt eigenlijk met veel functionele talen te zijn dat variabelen en objecten zo veel mogelijk immutable zijn. Dit wil zeggen als je iets eenmaal aangemaakt hebt dat het niet meer te wijzigen valt. Je kan het expliciet aangeven dat iets wel mutable is maar dit is eigenlijk niet zoals je zou horen te doen in een functionele taal. In &#8220;normale talen&#8221; is dit wel gebruikelijk en daarom zorgt dit er direct voor dat je op een andere manier moet gaan nadenken om een probleem op te lossen. Ik vind de omslag lastig maar ik zie ook wel voordelen hiervan. Met normaal programmeren heb je kans dat variabelen worden aangepast van ergens anders in je programma. Dit kan onverwacht fouten opleveren wat niet zal gebeuren als je variabelen immutable zijn.

In normaal OOP hebben ze voor dit probleem ook deels een oplossing bedacht en dat is &#8220;encapsulation&#8221; hiermee kan je je variabelen en fields binnen een object beschermen door ze bijvoorbeeld private te maken. Wat overigens binnen F# ook nog kan.

Als je gevolg hiervan wordt er bijvoorbeeld ook veel sneller recursieve methodes gebruikt om bepaalde problemen op te lossen.

### Syntax

De syntax is heel anders dan dat ik gewend ben van andere talen als C# en PHP. Python komt nog het meeste in de buurt wat betreft syntax door het ontbreken van brackets in de syntax. Ik heb tot nu toe alleen nog maar brackets gezien bij het definiëren van een sequens. Dit is een soort lijst maar de items hoeven er nog niet perse in te zitten en kan ook eventueel oneindig lang zijn. De compiler of interpreter bepaalt die dingen die normaal met brackets worden gedaan aan de hand van tabs en spaties. Ook het gebruik van komma&#8217;s en haakjes is teruggebracht bij het definiëren en aanroepen van methodes. in plaats daarvan zeg je eerst hoe de methode heet en is daarna na iedere spatie een ander argument. Gebruik je wel haakjes en komma&#8217;s dan ben je een tuple aan het definiëren als argument. Deze worden overigens wel een stuk meer gebruikt dan in C# gebruikelijk is maar ze bestaan wel. Daarnaast zal je opvallen dat in een stuk F# code geen return statements staan ondanks de waarschijnlijk vele gedefinieerde functies in de code. Standaard wordt de laatste regel in de functie gereturnt. Naast deze dingen zijn er meestal geen type aanduidingen nodig binnen je code. F# is wel een static typed taal maar het is alleen maar nodig om dit aan te geven als de compiler er zelf niet uit kan komen. Met veel operaties is F# daar prima toe in staat.

### Acties op lijsten/verzamelingen

Op lijsten en verzamelingen worden met functionele talen ook veel gedaan met behulp van lambda methodes. Je geeft dan een functie als argument die dan vaak over de hele lijst wordt uitgevoerd. Je ziet dat deze manier ook steeds meer wordt overgenomen door een taal als C# waar je met behulp van Linq extension methods dit ook kan doen tegenwoordig. C# staat je als je wilt inmiddels al voor een belangrijk deel toe wat je in F# ook kan. Wat wel een verschil is dat je vaak ook nog add en remove acties kan uitvoeren wat niet is toegestaan is in F#. Daarnaast is het grootste verschil dat als je F# efficient wilt gebruiken dat je wel wordt geforceerd om in zo&#8217;n stijl te programmeren waar dat in C# niet het geval is en je vaak ook nog andere keuzes hebt.

### Voorlopige conclusie

Ik vind het nog steeds leuk om F# te leren, het helpt je weer op een andere manier naar problemen te kijken. Deze kennis is eventueel ook toe te passen in niet functionele talen als C# die ook steeds meer functionele concepten gaat ondersteunen. Ik denk wel dat ik het op deze manier beter leer om dat ik nu min of meer wordt gedwongen om echt puur functionele code te schrijven. Wel merk dat de ondersteuning F# binnen Visual Studio minder goed is dan wat het is bij het schrijven van C#. Ik hoop jullie over een tijdje nog eens een update te kunnen geven. Als je alvast wat code van mij wilt bekijken die ik in F# heb geschreven dan kan je <a href="https://github.com/barld/EulerFSharp" target="_blank">hier </a>op mijn github kijken waar ik een aantal problemen van project Euler heb opgelost