# Hoofdstuk 1: Beginnen met programmeren

In dit hoofdstuk duiken we in de wereld van programmeren. Voordat we de robot echt laten rijden, beginnen we in een veilige omgeving: de simulator. We leren hoe je een computer (of robot) instructies geeft, wat de "taal" van Python is, en hoe je code schrijft die ook voor anderen begrijpelijk is.

## De Computer als Eigenwijze Leerling

Een robot is eigenlijk een hele snelle, maar ontzettend domme leerling. Hij doet *precies* wat jij zegt, niet wat jij *bedoelt*. 

Stel je voor dat ik jou vraag: "Pak een glas water." Dat snap jij direct.
Maar als ik dat tegen een robot zeg, blijft hij stil staan. Hij weet niet wat 'pakken' is, waar de kraan is of hoe een glas eruit ziet.

Om een robot iets te laten doen, moeten we gebruik maken van **pseudocode**. Dit is een stappenplan in normale mensentaal, maar dan zo precies dat zelfs een robot het niet fout kan doen.

### Opdracht: De Robot-Docent
Kies één iemand uit de klas (of je docent) die voor robot gaat spelen. De robot mag alleen bewegen als hij exact commando's krijgt.
Probeer de robot-docent de deur uit te laten lopen.

**Fout:** "Loop naar de deur." (Robot weet niet waar de deur is)
**Goed:**
1. Sta op.
2. Draai 90 graden naar rechts.
3. Zet 5 stappen vooruit.
4. Til je arm op tot deurkruk-hoogte.
5. ...

Zie je hoe gedetailleerd je moet zijn? Dit is precies wat programmeren is: complexe problemen opbreken in kleine, logische stapjes.

## Je Eerste Code: De Simulator

We gebruiken de [micro:bit Python Editor](https://python.microbit.org/v/3) om onze code te schrijven.
1. Ga naar de website.
2. Je ziet links een stuk tekst (de code) en rechts een plaatje van de micro:bit (de simulator).

![screenshot van hoofdscherm](/img/h1.1.png)

### PRIMM: Eerst kijken, dan doen
In de informatica gebruiken we vaak de **PRIMM**-methode: **P**redict (Voorspel), **R**un (Voer uit), **I**nvestigate (Onderzoek), **M**odify (Pas aan), **M**ake (Maak).

In de editor staat al een stukje code. 

**Stap 1: Predict (Voorspel)**
Kijk naar de onderstaande code. Wat denk je dat er gebeurt als je op 'Play' drukt? Bespreek dit met je buurman/vrouw.

	# Imports go at the top
	from microbit import *
	
	# Code in a 'while True:' loop repeats forever
	while True:
		display.show(Image.HEART)
		sleep(1000)
		display.scroll('Hello')

**Stap 2: Run (Voer uit)**
Druk op de Play-knop (driehoekje) onder de simulator. Had je gelijk?
Je ziet waarschijnlijk een hartje voor 1 seconde (1000 milliseconden), en daarna de tekst "Hello" die voorbij rolt.

## Syntax: De Grammatica van Python

Net zoals Nederlands spellingsregels heeft, heeft Python dat ook. Dit noemen we **syntax**.

*   `from microbit import *`: Dit is je gereedschapskist. Je 'pakt' alle hulpmiddelen die je nodig hebt om de micro:bit te besturen.
*   `while True:`: Dit betekent "Doe dit voor altijd". Alles wat hieronder staat (en ingesprongen is), wordt herhaald tot de batterij leeg is.
*   `sleep(1000)`: Wacht 1000 milliseconden (1 seconde).

### Let op de details!
Python is hoofdlettergevoelig. `True` is goed, `true` werkt niet. `Image.HEART` moet met hoofdletters.

## Inspringen (Indentation)

Python gebruikt **inspringen** (ruimte aan het begin van de regel) om te bepalen wat bij elkaar hoort. Kijk maar eens naar dit voorbeeld:

	while True:
		display.show(Image.HEART)
		sleep(1000)
	display.scroll('Hello')

In dit foute voorbeeld staat `display.scroll('Hello')` *niet* ingesprongen. Python denkt nu: "Oh, die regel hoort niet bij de herhaling." Maar omdat de herhaling (`while True`) nooit stopt, zal hij nooit aan het woordje "Hello" toe komen!

**Regel:** Alles dat bij de `while`-loop hoort, moet met een `Tab` ingesprongen worden.

## Commentaar: Briefjes aan jezelf

Code kan best ingewikkeld worden. Help jezelf (en je docent) door **commentaar** toe te voegen. Alles wat achter een hekje (`#`) staat, wordt door de computer genegeerd.

	# Dit programma laat een boos gezicht zien
	display.show(Image.ANGRY) # Ik ben boos!

Gebruik commentaar om je code te structureren:
1.  Bovenin: Wie heeft dit gemaakt en wat doet het?
2.  Bij lastige stukjes: Waarom doe je dit?

## Opdrachten H1

1.  **Investigate**: Verander in de standaard code `sleep(1000)` naar `sleep(200)`. Wat gebeurt er met het tempo?
2.  **Modify**: Maak de code zo dat hij eerst een **blij** gezichtje toont, dan 2 seconden wacht, en dan een **boos** gezichtje toont.
3.  **Make**: Schrijf (eerst in pseudocode op papier, dan in Python) een programma dat jouw naam laat scrollen, gevolgd door jouw favoriete dier (bijv. `Image.DUCK` of `Image.GIRAFFE`).
4.  **Debuggen**: De onderstaande code werkt niet. Er zitten 3 fouten in. Kun jij ze vinden en oplossen? (Tip: Let op hoofdletters en inspringen!)

		while true:
		display.show(Image.HAPPY)
		Sleep(1000)