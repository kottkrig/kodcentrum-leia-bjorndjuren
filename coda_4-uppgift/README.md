# CODA 4 – Simulera landning på Mars

Test-edit från Johans repo.

Det är farligt att åka till Mars. Rätt var det är så kan det dyka upp ett asteroidfält. 

För att ta reda på när det är säkrast att åka så kan vi bygga en *simulation*. En simulation är ett datorprogram som kan testa saker. Vi kan till exempel testa att landa vid olika tidpunkter på dagen. För att vi skall kunna se vilken tid som är bäst.

## 1 – Remixa simulationen

Vi har hittat ett projekt för simulationen men det ser ut att vara ofärdigt. Vi skulle behöva göra klart det.

Låt oss remixa det.

// TODO: Lägg till länk till grundprojekt.

## 2 – Beskrivning

Vi kommer behöva:

- Två variabler
	- En som räknar lyckade landningsförsök
	- En som räknar misslyckade landningsförsök
- Ett skript som avfyrar raketen mot mars
	- Om raketen nuddar asteroidfältet så skall variabeln "misslyckade landningsförsök" ändras med 1
	- Om raketen nuddar Mars så skall "lyckade landningsförsök" ändras med 1
- Ett skript som sätter variablerna till 0 och sedan avfyrar raketen 100 gånger

Låt oss bygga det tillsammans.

## 3 – Avfyra raketen

Vi vill att raketen skall avfyras när vi startar vår simulation. Alltså när vi trycker på den gröna flaggan.

När vi trycker på den gröna flaggan så skall raketen **för alltid** röra sig framåt med **gå 5 steg**.

![](./1_1.gif)

## 4

![Nu åker raketen framåt](./2_1.png)

Men om vi bara åker framåt utan att någonsin stanna så kommer vi bara att fortsätta att åka och åka. Och då kommer vi åka förbi Mars.

Efter varje steg framåt så måste vi kolla **om** vi **rör vid Mars**. Och om vi gör det så vill vi **stoppa detta skript** eftersom vi då har kommit fram till Mars. 

![](./2_2.gif)

## 5 – Skapa en variabel

![Nu stannar raketen vid Mars](./5_1.png)

Nu stannar raketen vid Mars men vi skulle behöva hålla räkningen på hur många gånger vi lyckas landa.

För det behöver vi en *variabel*. Variabler är bra för de kan hålla reda på saker åt oss. Till exempel hur många gånger vi lyckas landa.

![](./5_2.png)

Skapa en variabel som heter ”lyckade landningsförsök”.

## 6 – Ändra variabeln

I vårt skript så vill vi nu **ändra "lyckade landningsförsök" med 1** när vi rör vid mars men innan vi stoppar vårt skript.

![](./6_1.png)

Då kommer vår variabel att plussas med 1 varje gång vi rör vid Mars. Så om vi trycker på den gröna flaggan flera gånger så kommer vår variabel att hålla räkningen för hur många gånger vi har rört vid Mars.

![](./6_2.gif)

## 7 – Åk till Mars med ett meddelande

När vi kör vår simulation så körs den bara en gång. Så om vi vill köra 100 simulationer så måste vi trycka på den gröna flaggan 100 gånger. Det är det väl ingen som orkar!? Tur att det finns ett bättre sätt!

Vi kan använda *meddelanden* för att avfyra vår raket flera gånger. Så i stället för att avfyra vår raket 1 gång genom att trycka på den gröna flaggan så kan vi avfyra vår raket 100 gånger genom att skicka ett meddelande 100 gånger.

Lägg ut blocket **När jag tar emot ”uppskjutning”**.

Flytta sedan alla block från **När grön flagga klickas på** till **När jag tar emot ”uppskjutning"** genom att dra dem.

Om vi skulle testa att starta simulationen så skulle ingenting hända för vi skickar aldrig meddelandet ”uppskjutning".

Lägg till ett block **skicka "uppskjutning" och vänta** och lägg det under **När grön flagga klickas på**.

Om vi testar programmet nu så fungerar det precis som tidigare. Raketen flyger mot Mars.

## 8 – Skjut upp 100 gånger

![Skicka meddelande ”uppskjutning”](./8_1.png)

Vi skjuter fortfarande bara upp raketen 1 gång. Men vi vill testa att skjuta upp raketen 100 gånger.

Lägg till blocket **repetera 100 gånger** runt vårt block **skicka "uppskjutning" och vänta**. 

Nu kommer raketen att skjutas upp 100 gånger. Utan att vi behöver avfyra den själva. Den bara åker och åker.

![](./8_2.gif)

## 9 – Räkna misslyckade landningar

![Vi åker till Mars 100 gånger](./9_1.png)

Nu åker vi till Mars varje gång vi trycker på den gröna flaggan men vi åker rätt igenom asteroidfältet. Det måste vi fixa!

Vi behöver **skapa en ny variabel** som heter ”misslyckade landningar”.

Efter varje steg framåt så skall vi på samma sätt som vi räknade antalet "lyckade landningar" räkna "misslyckade landningar". **Om vi rör vid Asteroider** så skall vi **ändra "misslyckade landningar" med 1**.

Och precis som när vi rör vid Mars så vill vi också **stoppa detta script** efter att vi har ändrat vår variabel.

![](./9_2.gif)


## 10 – Sätt variabler till 0 vid start

![](./10_1.png)

Våra variabler bara fortsätter att räkna och räkna. De börjar aldrig om från början. Vi skulle behöva sätta dem till 0 varje gång vi trycker på den gröna flaggan.

![](./10_2.png)

Lägg de här blocken **mellan** blocket ”när grön flagga klickas på” och ”repetera 100”.

## 11 – Ändra klockslag

Åh! Det finns en variabel som har legat gömd hela tiden. Har du sett den? Den heter ”klockslag”. Den måste ha funnits med sedan vi remixade den.

Det verkar som att vi kan köra simulationen vid olika klockslag. För att se om det är någon skillnad att till exempel åka på morgonen eller på eftermiddagen. 

För att byta klockslag så lägger vi till blocket **ändra "klockslag" till "17"** precis i början av vårt skript. Efter att den gröna flaggan har klickats på. Då kommer vi testa att landa 100 gånger när klockan är 17:00. Alltså fem på eftermiddagen.

> Om du vill se vilket klockslag simulationen är inställd på så kan du bocka för den lilla rutan som ligger framför variabeln.
> ![](./11_2.png)



## 12 – Fler justeringar

Tycker du att simulationen går långsamt? Det går att snabba upp den genom att gå fler steg framåt. Testa att skriva in en högre siffra i blocket **gå 3 steg framåt**.
