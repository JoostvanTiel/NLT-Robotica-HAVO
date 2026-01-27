---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Hoofdstuk 6: Doolhof oplossen
Hier moet nog nieuwe uitleg komen.

To Do:
  > Robot een bocht laten maken
  > Robot een T-splitsing laten nemen
  > Robot een kruispunt laten nemen
  > Robot om laten draaien bij een doodlopend pad

## Opdrachten hoofdstuk 6

### Zonder robot

1. Gebruik een `for`-lus met `range()` om van 9 naar 0 terug te tellen. Laat elk getal zien op het scherm met `sleep(500)` tussen de stappen.

2. Gebruik een `while`-lus om steeds een hartje en daarna een smiley af te wisselen op het scherm.

3. Gebruik een `for`-lus en het `continue`-statement om het getal 4 over te slaan.

4. Begin bij 0 en verhoog het getal telkens met 1. Laat het zien op de micro:bit. Stop met tellen zodra `button_a.is_pressed()` `True` is.

5. Maak een lijst `[1, 4, 2, 3, 7]` en gebruik een `for`-lus om te kijken of het getal 3 erin zit. Als je het vindt, laat een vinkje zien.

6. Bekijk de onderstaande code, **maar voer deze nog niet uit!** Bedenk welk getal er op het scherm getoond wordt.

		x = 0
		
		for i in range(3):
			for j in range(5):
				x = x + i + j
		
		display.scroll(x)

### Met robot

7. Gebruik een `for`-lus met `range(5)` en laat de robot elke seconde een beetje draaien met `motor_aan(...)` en `sleep(1000)`.

8. Gebruik een `while`-lus. Laat de robot rijden met beide motoren aan. Stop als de robot een donkere lijn ziet.

9. Rijd vooruit tot de robot binnen 10 cm van een voorwerp is. Laat de robot dan een willekeurige hoeveelheid draaien. Blijf dit oneindig herhalen.

10. Gebruik een `for`-lus en toon met `display.scroll()` de waarde van elke sensor op volgorde.

11. Gebruik een `for`-lus waarin je steeds `led_links`, `led_rechts` of `led_beide` aan- en uitzet. Wacht een halve seconde tussen de stappen.

12. Laat de robot een vierkantje rijden. Gebruik daarvoor een `for`-lus. Sla de instructies hiervoor op een functie genaamd `rijdVierkant()`.

13. Laat de robot vijfmaal achter elkaar een vierkantje rijden. Gebruik daarvoor de functie uit de vorige vraag.

14. Pak het A2-papier van de vorige hoofdstukken er weer bij en ontwerp zelf een klein doolhof. Houdt er rekening mee dat de paden niet te dicht op elkaar zitten (minimaal 1,5 robotlengtes afstand). Het doolhof moet minimaal bevatten: 
	+ start
	+ drie rechte bochten
	+ een t-splitsing
	+ een doodlopend pad
	+ een eind (grijs vel)