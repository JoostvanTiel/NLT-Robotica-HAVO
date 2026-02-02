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

# Hoofdstuk 6: Algoritmes en Doolhoven

In de vorige hoofdstukken hebben we geleerd hoe we de robot een lijn kunnen laten volgen en hoe we keuzes kunnen maken met `if`-statements. In dit hoofdstuk gaan we deze kennis combineren om een grotere uitdaging aan te gaan: het oplossen van een doolhof.

Een doolhof is eigenlijk niets anders dan een lijn met veel vertakkingen en doodlopende wegen. Om het einde te vinden, hebben we een slim plan nodig. In de informatica noemen we zo'n plan een **algoritme**.

## Situaties herkennen

Voordat we een algoritme kunnen maken, moet de robot eerst begrijpen in welke situatie hij zich bevindt. De Maqueen heeft 5 lijnsensoren:
*   `lijnsensor_l2`: Uiterst links
*   `lijnsensor_l1`: Links van het midden
*   `lijnsensor_m`: Midden
*   `lijnsensor_r1`: Rechts van het midden
*   `lijnsensor_r2`: Uiterst rechts

Tot nu toe gebruikten we vooral de middelste drie. Voor een doolhof zijn de buitenste sensoren (`l2` en `r2`) erg belangrijk om kruispunten te herkennen.

### 1. De rechte lijn
Dit kennen we al. De `lijnsensor_m` ziet zwart. De andere sensoren zien wit.
*   **Actie:** Rechtdoor rijden.

### 2. T-Splitsing en Kruispunten
Bij een T-splitsing of een kruispunt zien meerdere sensoren tegelijk zwart. Bijvoorbeeld, als de robot op een kruispunt stuit, zien `lijnsensor_m`, `lijnsensor_l1`, en `lijnsensor_r1` (en vaak ook `l2` en `r2`) allemaal zwart.
*   **Signaal:** Meerdere sensoren geven een lage waarde (< 100).
*   **Actie:** Hier moet de robot een beslissing maken: links, rechts of rechtdoor?

### 3. Doodlopend pad
Als de lijn plotseling stopt, zien alle sensoren wit (hoge waarde > 100).
*   **Signaal:** Alle sensoren geven een hoge waarde.
*   **Actie:** De robot moet omdraaien (180 graden) en terugrijden tot hij weer een lijn vindt.

## Een Doolhof-Algoritme: De Rechterhandregel

Een bekend algoritme om simpele doolhoven op te lossen is de "rechterhandregel". Stel je voor dat je met je ogen dicht in een doolhof staat. Als je met je rechterhand constant de muur aanraakt en zo blijft lopen, kom je uiteindelijk bij de uitgang (of terug bij het begin).

Voor onze lijnvolg-robot werkt dit als volgt bij elk kruispunt:
1.  **Kan je naar rechts?** -> Ga rechtsaf.
2.  **Kan je niet naar rechts, maar wel rechtdoor?** -> Ga rechtdoor.
3.  **Kan je niet naar rechts en niet rechtdoor?** -> Ga linksaf.
4.  **Kan je nergens heen?** -> Keer om (doodlopend pad).

Om dit te programmeren, moet de robot bij een splitsing dus *eerst* kijken of rechtsaf een optie is.

## Opdrachten hoofdstuk 6

1. **De Lijn Herkennen (Basis)**
   Schrijf een programma waarbij de robot stopt zodra hij een dwarse streep (kruispunt) ziet. Gebruik hiervoor `lijnsensor_l2` en `lijnsensor_r2`. Als deze beide zwart zien, moet de robot stilvallen.

2. **Het Doolhof Ontwerpen**
   Pak het A2-papier. Ontwerp met zwarte tape een doolhof. Zorg voor:
   *   Minstens één T-splitsing.
   *   Minstens één doodlopend pad.
   *   Zorg dat de lijnen niet te dicht op elkaar liggen (minimaal 15 cm tussenruimte).

3. **T-Splitsing Nemen**
   Zet de robot voor een T-splitsing. Schrijf code zodat de robot naar de splitsing rijdt. Zodra hij de splitsing detecteert (via de sensoren), moet hij stoppen, 1 seconde wachten, en dan 90 graden naar rechts draaien en verder rijden.

4. **Doodlopend Pad (Dead End)**
   Zet de robot op een lijn die doodloopt.
   *   Detecteer het einde van de lijn (alles is wit).
   *   Laat de robot op zijn plek draaien tot hij weer een lijn ziet (gebruik `lijnsensor_m`).

5. **De Ultieme Test: Doolhof Oplossen**
   Combineer alles in één programma. Gebruik de **Rechterhandregel**:
   *   Volg de lijn.
   *   Kruispunt of splitsing? -> Check rechts. Rechts vrij? Draai rechts.
   *   Anders rechtdoor.
   *   Anders links.
   *   Doodlopend? -> Draai om.
   
   Start de robot aan het begin en kijk of hij zelfstandig het einde (het grijze vlak) kan vinden!