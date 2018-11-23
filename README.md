# Performance testing

Performance testing handler om at i skal få en fornemmelse af, hvor mange brugere applikationen kan trække. Det gør i ved at simulere et antal requests, der sendes afsted til serveren.

Der er to tilgange - Enten kan i bruge et konsol-program som siege eller apache bench som vi har brugt tidligere, eller i kan bruge et GUI program som jmeter. jmeter tillader jer at bygge mere avanceret test-planer, men det kræver også lidt arbejde at forstå hvordan jmeter virker.

## jmeter

https://www.digitalocean.com/community/tutorials/how-to-use-apache-jmeter-to-perform-load-testing-on-a-web-server

https://www.blazemeter.com/blog/getting-started-jmeter-basic-tutorial

## siege
https://github.com/Distribuerede-Systemer-2018/scaled-dis

## Generelle råd
* Når i tester jeres applikation er det vigtig at simulere en belastning der er så realistisk som muligt. Det vil sige, at i ikke bare tilgår det samme URL 100 gange, men forskellige URLer. fx skal i ikke lave en test som åbner `/orders/1` 100 gange - i skal åbne alle ordre-URLer (`/orders/2` osv.). I siege kan i bruge en liste af URLer (https://www.joedog.org/siege-manual/#a05), og i jmeter kan i få inspiration fra punktet "Dynamic Data"  i blazemeter guiden. I jmeter kan i også med fordel lave flere 'thread groups' så i kan sende forskellige requests afsted samtidig.
* Husk ikke kun at teste `GET` requests, men også `PUT`, `POST`, og `DELETE`. Test også gerne hvordan jeres `GET` requests bliver påvirket når der kører `POST`s samtidig - bliver læsning langsommere når der er mange inserts / updates?
* Husk at inkludere jeres jmeter test-planer eller jeres siege kommandoer i afleveringen.
* Husk at beskrive jeres test-plan i rapporten - Hvad mener i er vigtigt at teste, og hvordan giver jeres resultater jer en ide om hvor mange brugere applikationen kan understøtte.
* Huks at teste solr! Der har ikke været nogle TODOs i solr (reviews) delen af koden, men derfor skal i stadig teste dens performance. URLen er `/search/title/{title}`, og her er det ekstra vigtigt at i sørger for at `{title}` delen er dynamisk, så alle brugere ikke søger på det samme.
