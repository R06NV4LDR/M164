TOC

- [[#Aufgabe 1|Aufgabe 1]]
	- [[#Aufgabe 1#1 Welches ist das teuerste Buch in der Datenbank?|1 Welches ist das teuerste Buch in der Datenbank?]]
	- [[#Aufgabe 1#2 Welches ist das billigste Buch in der Datenbank?|2 Welches ist das billigste Buch in der Datenbank?]]
	- [[#Aufgabe 1#3 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis aller Bücher in der Datenbank liegt.|3 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis aller Bücher in der Datenbank liegt.]]
	- [[#Aufgabe 1#4 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.|4 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.]]
	- [[#Aufgabe 1#5 Lassen Sie sich alle Thriller ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.|5 Lassen Sie sich alle Thriller ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.]]
	- [[#Aufgabe 1#6 Lassen Sie sich alle Bücher ausgeben, bei denen der Gewinn überdurchschnittlich ist; bei der Berechnung des Gewinndurchschnitts berücksichtigen Sie NICHT das Buch mit der id 22.|6 Lassen Sie sich alle Bücher ausgeben, bei denen der Gewinn überdurchschnittlich ist; bei der Berechnung des Gewinndurchschnitts berücksichtigen Sie NICHT das Buch mit der id 22.]]
- [[#Aufgabe 2|Aufgabe 2]]
	- [[#Aufgabe 2#7. Wir brauchen die Summe der durchschnittlichen Einkaufspreise der einzelnen Sparten. Allerdings wollen wir dabei nicht die Sparte Humor berücksichtigen, ebenso wenig die Sparten, in denen der durchschnittliche Einkaufspreis 10 Euro oder weniger beträgt.|7. Wir brauchen die Summe der durchschnittlichen Einkaufspreise der einzelnen Sparten. Allerdings wollen wir dabei nicht die Sparte Humor berücksichtigen, ebenso wenig die Sparten, in denen der durchschnittliche Einkaufspreis 10 Euro oder weniger beträgt.]]
	- [[#Aufgabe 2#2. "Bekannte Autoren" definieren wir als Autoren, die mehr als 4 Bücher veröffentlicht haben. Wie viele solcher Autor/innen haben wir in der Datenbank?|2. "Bekannte Autoren" definieren wir als Autoren, die mehr als 4 Bücher veröffentlicht haben. Wie viele solcher Autor/innen haben wir in der Datenbank?]]
	- [[#Aufgabe 2#9. Ihr Chef sagt zu Ihnen: "Schauen Sie sich mal alle Verlage an, die im Durchschnitt weniger als 10 Euro Gewinn pro Buch machen. Ich glaube, die verdienen im Schnitt höchstens 7 Euro pro Buch."|9. Ihr Chef sagt zu Ihnen: "Schauen Sie sich mal alle Verlage an, die im Durchschnitt weniger als 10 Euro Gewinn pro Buch machen. Ich glaube, die verdienen im Schnitt höchstens 7 Euro pro Buch."]]


## Aufgabe 1
### 1 Welches ist das teuerste Buch in der Datenbank?
```sql
SELECT b.titel, b.verkaufspreis
FROM buecher b
JOIN (
    SELECT MAX(verkaufspreis) AS max_verkaufspreis
    FROM buecher
) max_price ON b.verkaufspreis = max_price.max_verkaufspreis;
```
### 2 Welches ist das billigste Buch in der Datenbank?
```sql
SELECT b.titel, b.verkaufspreis
FROM buecher b
JOIN (
    SELECT MIN(verkaufspreis) AS min_verkaufspreis
    FROM buecher
) min_price ON b.verkaufspreis = min_price.min_verkaufspreis;
```
### 3 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis aller Bücher in der Datenbank liegt.
```sql
SELECT *
FROM buecher
WHERE einkaufspreis > (
    SELECT AVG(einkaufspreis)
    FROM buecher
);
```
### 4 Lassen Sie sich alle Bücher ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.
```sql
SELECT *
FROM buecher
WHERE genre = 'Thriller' 
AND einkaufspreis > (
    SELECT AVG(einkaufspreis)
    FROM buecher
    WHERE genre = 'Thriller'
);
```
### 5 Lassen Sie sich alle Thriller ausgeben, deren Einkaufspreis über dem durchschnittlichen Einkaufspreis der Thriller liegt.
```sql
SELECT b.*, s.bezeichnung AS genre
FROM buecher b
JOIN buecher_has_sparten bhs ON b.buecher_id = bhs.buecher_buecher_id
JOIN sparten s ON bhs.sparten_sparten_id = s.sparten_id
WHERE s.bezeichnung = 'Thriller'
AND b.einkaufspreis > (
    SELECT AVG(b2.einkaufspreis)
    FROM buecher b2
    JOIN buecher_has_sparten bhs2 ON b2.buecher_id = bhs2.buecher_buecher_id
    JOIN sparten s2 ON bhs2.sparten_sparten_id = s2.sparten_id
    WHERE s2.bezeichnung = 'Thriller'
);
```
### 6 Lassen Sie sich alle Bücher ausgeben, bei denen der Gewinn überdurchschnittlich ist; bei der Berechnung des Gewinndurchschnitts berücksichtigen Sie NICHT das Buch mit der id 22.
```sql
SELECT *,
       (verkaufspreis - einkaufspreis) AS gewinn
FROM buecher
WHERE buecher_id <> 22 
AND (verkaufspreis - einkaufspreis) > (
    SELECT AVG(gewinn)
    FROM (
        SELECT (verkaufspreis - einkaufspreis) AS gewinn
        FROM buecher
        WHERE buecher_id <> 22
    ) AS average_profit
);
```

---
## Aufgabe 2

### 7. Wir brauchen die Summe der durchschnittlichen Einkaufspreise der einzelnen Sparten. Allerdings wollen wir dabei nicht die Sparte Humor berücksichtigen, ebenso wenig die Sparten, in denen der durchschnittliche Einkaufspreis 10 Euro oder weniger beträgt.

> [!TIP] Tipp: 
> Erstellen Sie ein Subselect, dessen Ergebnis eine Tabelle ist, in der die gewünschten Sparten und ihre durchschnittlichen Einkaufspreise ausgegeben werden.
> Von dieser Tabelle fragen Sie anschließend die Summe ab.
   
```sql

```
### 2. "Bekannte Autoren" definieren wir als Autoren, die mehr als 4 Bücher veröffentlicht haben. Wie viele solcher Autor/innen haben wir in der Datenbank?

> [!TIP] Tipp: 
> Erstellen Sie ein Subselect, das Ihnen die bekannten Autoren ausgibt. Um zu sehen, ob Ihr Ergebnis plausibel wirkt, lassen Sie sich ausgeben: Vorname, Nachname, Anzahl veröffentlichter Büche.
> Über dieses Subselect machen Sie eine einfach COUNT-Abfrage.

```sql

```
### 9. Ihr Chef sagt zu Ihnen: "Schauen Sie sich mal alle Verlage an, die im Durchschnitt weniger als 10 Euro Gewinn pro Buch machen. Ich glaube, die verdienen im Schnitt höchstens 7 Euro pro Buch."

> [!TIP] Tipp: 
>  Erstellen Sie für den ersten Satz des Chefs ein Subselect, das Sie für die Überprüfung des zweiten Satzes verwenden (Ausgabe: 'durchschnittlicher Gewinn pro Buch der Verlage, die weniger als 10 Euro pro Buch verdienen')

```sql

```