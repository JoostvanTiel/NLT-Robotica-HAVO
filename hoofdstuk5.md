# Hoofdstuk 5: Je eigen commando's (Functies)

Stel je voor dat je de robot een vierkantje wilt laten rijden. De code daarvoor is best lang:
1. Rijd vooruit
2. Stop
3. Draai 90 graden
4. Stop
...en dat dan 4 keer achter elkaar. Je krijgt een enorme waslijst aan code.

Zou het niet handig zijn als we de robot een *nieuw* woord kunnen leren? Bijvoorbeeld: `rijd_vierkant()`.
Zodra de robot dit woord ziet, voert hij zelf alle stappen uit. Dit noemen we een **functie**.

## Wat is een functie?

Je kunt een functie zien als een recept.
*   **Het recept:** Een lijstje stappen die je één keer opschrijft.
*   **De maaltijd:** Het resultaat dat je krijgt als je het recept uitvoert ("aanroept").

We hebben al veel functies gebruikt: `motor_aan()`, `sleep()`, `display.show()`. Nu gaan we ze zelf maken.

### Je eerste eigen functie

Laten we de robot leren hoe hij "Hallo" moet zeggen met zijn lampjes.

	def knipper_lampjes():
		# Hier begint het recept
		headlights(led_beide, 1) # Aan
		sleep(500)
		headlights(led_beide, 0) # Uit
		sleep(500)

	# Hier stopt het recept (omdat we niet meer inspringen)

	# Nu gaan we het recept gebruiken (aanroepen)
	while True:
		if button_a.is_pressed():
			knipper_lampjes()   # Doe het trucje!
			knipper_lampjes()   # Doe het nog eens!

Met `def` (van **def**inities) vertel je Python: "Ik ga nu een nieuw woord uitleggen."

## Parameters: Een recept op maat

Stel je wilt dat de robot soms 1 seconde knippert, en soms heel snel (0.1 seconde). Moet je dan twee aparte recepten schrijven? Nee! We kunnen een **parameter** (instelling) toevoegen.

Vergelijk het met een recept voor pannenkoeken: "Voeg *X* eieren toe."
Als je het recept gebruikt, zegt iemand: "Maak pannenkoeken met 2 eieren" of "met 4 eieren".

In Python:

	def rijd_vooruit(tijd):
		motor_aan(motor_links)
		motor_aan(motor_rechts)
		sleep(tijd)              # Gebruik de instelling
		motor_uit(motor_links)
		motor_uit(motor_rechts)

Nu kunnen we de robot flexibel commanderen:

	rijd_vooruit(1000)  # Rijd 1 seconde
	rijd_vooruit(3000)  # Rijd 3 seconden

De waarde `1000` wordt in de 'doos' (variabele) `tijd` gestopt. Overal waar `tijd` staat in de functie, wordt nu `1000` gebruikt.

## Variabelen: Het geheugen

Een variabele is een doosje waarin je iets kunt bewaren.
In wiskunde is dat vaak `x` of `y`. Saai! Bij robotica geven we ze logische namen.

	snelheid = 255
	afstand_tot_muur = 0
	naam_robot = "Henk"

Er zijn verschillende soorten dozen:
1.  **Integer (Geheel getal):** `snelheid = 100`
2.  **Float (Kommagetal):** `wachttijd = 0.5`
3.  **String (Tekst):** `bericht = "Pas op!"`
4.  **Boolean (Waar/Niet waar):** `lamp_aan = True`

Je hoeft Python niet te vertellen wat voor soort doos het is; dat snapt hij zelf.

### Variabelen aanpassen
Je kunt de inhoud van de doos veranderen.
	
	snelheid = 50          # Start langzaam
	motor_aan(motor_links, snelheid, 0)
	
	snelheid = snelheid * 2 # Dubbele snelheid! (Nu 100)
	motor_aan(motor_links, snelheid, 0)

## Waardes teruggeven ("Return")

Sommige functies *doen* iets (zoals `motor_aan`), andere functies *berekenen* iets en geven het antwoord terug.
Bijvoorbeeld de ultrasoonsensor: jij vraagt "Hoe ver?", hij antwoordt "15 cm".

Als je zelf zo'n functie schrijft, gebruik je `return`.

	def is_gevaarlijk_dichtbij():
		afstand = afstand_tot_voorwerp()
		
		if afstand < 10:
			return True   # Ja, gevaarlijk!
		else:
			return False  # Nee, veilig.

	# Gebruik:
	if is_gevaarlijk_dichtbij():
		motor_uit(motor_links)
		motor_uit(motor_rechts)

## Willekeur (Random)

Soms wil je dat de robot onvoorspelbaar is, zoals een levend wezen.

	from random import randint
	
	# Kies een willekeurig getal tussen 0 en 100
	geluksgetal = randint(0, 100)
	
	if geluksgetal > 50:
		display.show(Image.HAPPY)
	else:
		display.show(Image.SAD)

## Opdrachten hoofdstuk 5

1.  **De Dans-functie**:
    Maak een functie `doe_de_moonwalk()`. Zorg dat de robot in die functie een stukje achteruit rijdt en draait. Roep deze functie aan als je op knop A drukt.

2.  **Slimme bocht**:
    Maak een functie `draai_graden(aantal_graden)`.
    *   Deze is lastig! Je moet experimenteren. Hoe lang moet de motor aan staan (`sleep`) om precies 90 graden te draaien? En voor 180 graden?
    *   Probeer een formule te vinden. Bijvoorbeeld: `tijd = aantal_graden * 10`.

3.  **Lichtsensor Variabele**:
    Maak een variabele `basis_licht`.
    *   Bij het opstarten meet de robot het licht in de kamer en stopt dit in de variabele.
    *   Daarna gaat hij rijden. Als het *plotseling* veel donkerder is dan `basis_licht` (bijvoorbeeld omdat hij onder een tafel rijdt), gaan de koplampen aan.

4.  **De Dronken Robot**:
    Laat de robot rondrijden. Gebruik `randint` om elke seconde een nieuwe snelheid voor het linker- én rechterwiel te kiezen.
    *   Links: willekeurig tussen 0 en 255.
    *   Rechts: willekeurig tussen 0 en 255.
    Wat voor gedrag zie je?