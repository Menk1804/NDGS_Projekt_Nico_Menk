# Präsentationsscript – NGDS Projekt Gruppe H
**Station:** SMM – Sta. Maria, Val Müstair (1386 m ü. M.)  
**Gruppe H:** Melchior von Weissenfluh & Nico Schellhaas  
**Gesamtdauer:** ca. 9–10 Minuten

---

## Folie 1 – Titelfolie (Nico, ~30 Sek.)

> „Guten Tag. Wir sind Gruppe H – Melchior von Weissenfluh und Nico Schellhaas.
> In unserem Projekt haben wir Wetterdaten der Messstation SMM in Sta. Maria, Val Müstair
> auf 1386 Meter über Meer analysiert. Die Daten von MeteoSchweiz umfassen ein ganzes Jahr
> mit stündlichen Messungen von Temperatur, Luftdruck, Niederschlag und Sonnenstunden.
> Ich werde euch zuerst den Datensatz und die Interpolation vorstellen,
> anschliessend übernimmt Nico die Aufgaben 4 bis 7."

**Empfohlene Grafik:** Karte der Schweiz mit Standort der Station SMM markiert (optional), oder einfach Titelfolie mit Stationsname und Bild der Landschaft.

---

## Folie 2 – Daten & Interpolation (Nico, ~2 Min.)

> „Unsere Rohdaten enthielten rund 7'400 Messwerte – allerdings fehlten etwa 15% davon.
> Um trotzdem eine vollständige Zeitreihe zu erhalten, haben wir die Daten interpoliert
> und auf ein viertelstündliches Raster mit über 35'000 Punkten verdichtet."

> „Für Temperatur und Luftdruck haben wir einen **kubischen Spline** mit natürlichen
> Randbedingungen gewählt. Dieser erzeugt einen glatten, physikalisch plausiblen Verlauf.
> Für Niederschlag und Sonnenstunden haben wir **lineare Interpolation** verwendet –
> damit verhindern wir negative Werte, die physikalisch keinen Sinn ergeben."

> „Auf dieser Grafik seht ihr den Vergleich zwischen den Originaldaten (Punkte)
> und der Interpolation (Linie) für ein Zeitfenster von Tag 5 bis Tag 9.
> In diesem Zeitraum fiel Regen und die Sonne schien – ein interessantes Fenster
> mit Aktivität in allen vier Messgrössen."

**Empfohlene Grafik:** 4-er Plot aus Aufgabe 3 (Temperatur, Luftdruck, Niederschlag, Sonnenschein).

---

## Folie 3 – Nullstellen der Temperatur (Nico, ~2 Min.)

> „Ich übernehme jetzt mit Aufgabe 4. Wir haben untersucht, wann die Temperatur
> den Gefrierpunkt von 0°C überschreitet oder unterschreitet –
> also wann es von Frost zu Tauwetter wechselt und umgekehrt."

> „Dazu haben wir zuerst grob nach Vorzeichenwechseln in der interpolierten Kurve gesucht
> und diese dann mit dem **Newton-Verfahren** auf vier Nachkommastellen genau bestimmt."

> „Im Zeitraum von Tag 1 bis Tag 10 haben wir **13 Nullstellen** gefunden.
> Die vielen Nullstellen in kurzer Zeit zeigen, dass es in den ersten Januartagen
> sehr unbeständiges Wetter gab – die Temperatur schwankte ständig um den Gefrierpunkt."

**Empfohlene Grafik:** Temperaturverlauf mit roten Nullstellen-Punkten aus Aufgabe 4.

---

## Folie 4 – Grösste Schwankungen (Nico, ~2 Min.)

> „In Aufgabe 5 haben wir untersucht, wann die Temperatur am schnellsten steigt
> und fällt – also das Maximum und Minimum der Ableitung."

> „Die Ableitung dT/dt gibt an, wie stark sich die Temperatur pro Tag ändert.
> Wir haben sie **analytisch** aus dem Spline berechnet – das ist exakter als eine
> numerische Näherung."

> „Über das ganze Jahr hinweg haben wir die Woche von Tag 40 bis 47 als besonders
> schwankungsreich identifiziert. Der stärkste Anstieg war an Tag 46.81,
> der stärkste Abfall kurz davor an Tag 46.66 –
> beides innerhalb weniger Stunden, was auf ein markantes Wetterereignis hindeutet."

> „Die grossen Werte in der Ableitung – teils über 60°C pro Tag – sind
> Artefakte des Splines an Stellen mit fehlenden Messwerten, keine realen Temperaturen."

**Empfohlene Grafik:** 2-er Plot aus Aufgabe 5 (oben Temperaturverlauf, unten Ableitung mit grünem und blauem Punkt).

---

## Folie 5 – Mittelwerte (Melchior, ~1.5 Min.)

> „Für die Mittelwertberechnung habe ich die Temperatur verwendet.
> Den Jahresmittelwert und die Monatsmittelwerte haben wir nicht einfach
> durch Aufsummieren berechnet, sondern durch **numerische Integration**
> der Interpolationsfunktion – das ist mathematisch präziser."

> „Der Jahresmittelwert der Station SMM beträgt **7.68°C**.
> Zum Vergleich: Im Schweizer Mittelland liegt der Jahresmittelwert
> typischerweise bei 9–10°C – die Höhenlage von 1386m macht sich also deutlich bemerkbar."

> „Die Monatsmittelwerte zeigen den klaren Jahresgang:
> Im Winter sinkt die Temperatur unter 0°C, im Sommer erreicht sie ihr Maximum.
> Einige Monate liegen deutlich unter dem Jahresmittel."

**Empfohlene Grafik:** Temperaturverlauf mit Jahresmittel (gestrichelte Linie) und Monatsmittelwerten (Treppenkurve) aus Aufgabe 6.

---

## Folie 6 – Glättung (Melchior, ~1.5 Min.)

> „In der letzten Aufgabe haben wir die Temperaturdaten geglättet –
> also kurzfristige Schwankungen herausgefiltert, um den langfristigen Trend sichtbar zu machen."

> „Dazu haben wir eine **diskrete Faltung** mit einer symmetrischen Rechteckfunktion verwendet.
> Je grösser die Fensterbreite, desto stärker die Glättung:
> 7 Tage zeigen noch die Wochenschwankungen,
> 14 Tage dämpfen diese spürbar,
> 28 Tage zeigen fast nur noch den saisonalen Verlauf."

> „Technisch haben wir darauf geachtet, Randeffekte zu vermeiden:
> Statt die Ränder mit Nullen aufzufüllen – was die Kurve am Anfang und Ende
> künstlich gegen Null zieht – haben wir die Randwerte gespiegelt."

**Empfohlene Grafik:** Glättungsplot aus Aufgabe 7 mit allen drei Fensterbreiten.

---

## Folie 7 – Zusammenfassung & Schluss (Melchiro), ~30 Sek.)

> „Zusammenfassend haben wir gezeigt, wie man mit numerischen Methoden –
> Interpolation, Nullstellensuche, Differentiation, Integration und Faltung –
> reale Wetterdaten analysieren kann."

> „Die wichtigsten Erkenntnisse: Der Jahresmittelwert beträgt 7.68°C,
> die ersten Januartage zeigten sehr unbeständiges Wetter mit 13 Temperaturnulldurchgängen,
> und Anfang Februar gab es das markanteste Wetterereignis des analysierten Zeitraums."

> „Vielen Dank für eure Aufmerksamkeit – wir beantworten gerne Fragen."

---

## Empfohlene Folienstruktur (7 Folien)

| # | Titel | Sprecher | Zeit |
|---|-------|----------|------|
| 1 | Titelfolie & Einleitung | Melchior | 30s |
| 2 | Daten & Interpolation | Melchior | 2 min |
| 3 | Nullstellen der Temperatur | Nico | 2 min |
| 4 | Grösste Schwankungen | Nico | 2 min |
| 5 | Mittelwerte | Melchior | 1.5 min |
| 6 | Glättung | Melchior | 1.5 min |
| 7 | Zusammenfassung | Nico | 30s |
| **Total** | | | **~10 min** |
