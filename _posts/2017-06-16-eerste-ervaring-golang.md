---
id: 189
title: Mijn eerste ervaring met GoLang
date: 2017-06-16T22:19:47+00:00
author: Barld Boot
layout: post
guid: http://barld.nl/?p=189
permalink: /189/eerste-ervaring-golang/
categories:
  - parallel
  - school
---
&nbsp;

Inmiddels al weer een tijdje geleden begonnen met het leren van een voor mij nieuwe programmeer taal GoLang. In dit artikel wil ik mijn eerste ervaring en mening over deze taal delen.

GoLang ook wel een gewoon Go genoemd bestaat sinds 2009 en is ontwikkeld door de internet reus Google. Het is een taal waarover je de afgelopen jaren al regelmatig iets van hebt kunnen horen. Een van de meest bekende projecten ontwikkeld in GoLang is Docker. Dat het mogelijk was om zo&#8217;n succesvol project te ontwikkelen in GoLang heeft bijgedragen aan de populariteit en de groei van een online community.

## Low level geheugen beheer

Ik vind persoonlijke deze keus die ze hebben gemaakt wel leuk. Je moet namelijk weer een beetje gaan nadenken over pointers. Alle in iedere geval zelf gedefineerde data types zijn een struct. Dit betekent dat ze standaard als value type worden behandeld in tegenstelling tot veel ander High level talen waar je zelf gedefinieerde types meestal maakt met een class. Deze nieuwe datatypes zijn standaard reference types dit is regelmatig zelfs niet eens te veranderen. Bij Go is dit ook mogelijk je kan namelijk een pointer naar de waarde geven. Hierdoor kan je wel de originele waardes aanpassen en hoeft er ook geen kopie van een object te worden gemaakt.

Ik vind het leuk dat je daar zelf invloed op hebt. In het eerste jaar hebben we behoorlijk wat theorie gehad over stack en heap maar nu mag je het ook werkelijk zelf bewust toepassen in de praktijk. Normaal was het alleen handig om door te hebben dat de programmeer taal dat op de achtergrond voor je doet. Je kon verklaren waarom er bepaald gedrag was.

## GoLang is clean en simpel

Er bestaan in Go maar relatief weinig concepten en syntax. Daarnaast is Golang erg streng op formatting. De code moet gewoon aan een bepaalde code convention voldoen anders compiled het vaak niet eens. Ook zit er standaard een formatting tool in de compiler. Dit alles zorgt ervoor dat vrijwel alle code door wie het ook ontwikkeld er behoorlijk consistent uit ziet wat betreft stijl. Dit vind ik een groot voordeel omdat het gewoon makkelijk leesbaar is. En een ander voordeel is dat je minder discussie zal moeten voeren over code stijl. De compiler dwingt je om het op een bepaalde manier te doen zo simpel is het. Als je net begint kan het wel eens wat verwarrend zijn en je irriteren als het niet wil compilen maar dat wordt vanzelf beter. Voorbeelden zijn dat curly bracket direct na de if of for loop moet staan en dat er geen unused variabele in je code mag zitten.

Daarnaast is het een vrij simpele taal die vrij weinig concepten bevat. Zo is er geen ondersteuning voor uitgebreide inheritance. Ook missen er nog allemaal andere dingen zoals bijvoorbeeld generics dingen markeren als read only of verschillende soorten loops. Het is prettig omdat je snel alle concepten snel kan leren en je zelf of je groepsgenoten code minder makkelijk complex kan maken. Vaak is er wel om heen te werken maar zelf mis ik soms toch nog wel dingen zoals als Generics.

## GoRoutines

Dit is waarschijnlijk een van de belangrijkste redenen waarom je zou kiezen om go te gaan leren en gebruiken. Met GoRoutines kan je makkelijk zonder veel kosten code asynchroon laten draaien. Dit komt mede doordat de stack van GoLang een dynamische grote heeft. Je zet &#8220;go&#8221; voor je statement en je code wordt parallel uitgevoerd het is nog steeds niet simpel maar maakt het wel een stuk simpeler. Daarnaast bestaan er channels om data weer te kunnen synchroniseren. Om dingen parallel te laten lopen vraagt weer om een andere manier van denken waar je beter in kan worden door gewoon veel te trainen of wel gewoon oefenen en het veel proberen net zoals het leren OOP en FP.

## Wat ik allemaal heb gedaan

Ik ben begonnen met doornemen van de Go tour op <https://tour.golang.org/> . Als je dit hebt doorgenomen dan ben je al een heel eind op weg. De volgende uitdaging was om een lokale developement omgeving op te zetten. Dit was nog wel een uitdaging, zeker door hebben hoe alle paden moeten staan was wel even lastig. Mogelijk snap ik dat nog steeds niet zo goed maar dat vind ik ook een minder punt aan GoLang. Daarna natuurlijk wat kleine proef dingetjes en scriptjes geschreven. Een voorbeeld hiervan is de socket chat die ik met een klasgenoot heb proberen te schrijven. [(https://github.com/Daan-Grashoff/Golang\_socket\_chat)](https://github.com/Daan-Grashoff/Golang_socket_chat)

## De toekomst

Wat ik tot nu toe heb ervaren is het een prettige taal op een paar nadelen na. Ik denk dat als ik er verder mee ga dat ik er nog veel van kan leren. Als alles volgens plan verloopt hopen we voor ons komende project de backend op de server ook in GoLang te gaan ontwikkelen. Ik hoop dat we daar als team veel van kunnen leren op gebiedt van specifiek de taal GoLang te leren maar ook de concepten van concurrent programmeren beter gaan begrijpen.

&nbsp;

&nbsp;

&nbsp;