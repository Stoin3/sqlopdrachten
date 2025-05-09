# Sql basis

### Database 
Maak gebruik van het sql-bestand reisbureau.sql en voer hierop onderstaande opdrachten uit.
Theorie kun je vinden op: https://www.edutorial.nl/dbq/introductie/

### Queries reisbureau
* Geef de namen van de klanten die in Rotterdam wonen
SELECT naam FROM klanten WHERE Plaats = 'Rotterdam'; 

* Geef de namen van de klanten die geen reis geboekt hebben.
SELECT klanten.naam
FROM klanten
LEFT JOIN boekingen ON klanten.klantnummer = boekingen.Klantnummer
WHERE boekingen.Klantnummer IS NULL;

* Hoeveel klanten komen er niet uit Rotterdam
SELECT klanten.Plaats
FROM klanten
WHERE klanten.Plaats != 'Rotterdam'

* Hoeveel reizen hebben als bestemming Afrika?
SELECT bestemmingen.Werelddeel
FROM bestemmingen
WHERE bestemmingen.Werelddeel = 'Afrika'

* Hoeveel moeten de klanten, die naar Azië gaan, in totaal betalen?
SELECT SUM(`Betaald bedrag`) AS Totaalbetaald
FROM boekingen

* Geef de namen van de klanten die met kinderen op reis gaan.
SELECT klanten.Naam
FROM klanten
JOIN boekingen ON boekingen.`Klantnummer` = klanten.Klantnummer
WHERE boekingen.`Aantal kinderen` > 0

* Hoeveel verschillende reizen kun je boeken bij dit reisbureau?
SELECT COUNT(`Bestemmingcode`) AS Hoeveelheid FROM reizen; 

* Geef de naam en postcode van de klanten die in een postcode gebied wonen dat begint met een 9.
SELECT `Naam`,`Postcode` FROM klanten WHERE `Postcode` LIKE '9%';

* Groepeer de klanten op woonplaats. Geef de woonplaats en het aantal klanten per woonplaats.
SELECT `Plaats`, COUNT(`Plaats`) AS hoeveelheid
FROM klanten
GROUP BY `Plaats`

* Geef naam en datum van de klanten die voor de maand April een reis hebbben geboekt.
SELECT `Naam`, boekingen.Boekdatum
FROM klanten
JOIN boekingen ON boekingen.`Klantnummer` = klanten.Klantnummer
WHERE MONTH(boekingen.Boekdatum) < 4;

* Geef de namen van klanten, het werelddeel van de bestemming en het aantal dagen van de reis voor boekingen van minimaal 15 dagen.
SELECT 
    k.Naam AS klantnaam,
    r.`Bestemmingcode`,
    r.`Aantal dagen`
FROM 
    boekingen b
JOIN 
    reizen r ON b.`Reisnummer` = r.`Reisnummer`
JOIN 
    klanten k ON b.klantnummer = k.klantnummer
WHERE 
    r.`Aantal dagen` >= 15;
