# Sql basis

### Database gegevens aanpassen
Maak gebruik van het sql-bestand reisbureau.sql en voer hierop onderstaande opdrachten uit.
Theorie kun je vinden op: https://www.edutorial.nl/dbq/introductie/

### Opdracht 1
* Geef de query om alle tabellen in de database 'reisbureau' weer te gegeven
SHOW TABLES;

### Opdracht 2
* Voeg 2 nieuwe klanten toe aan de tabel 'customers' (je mag de waarden zelf bedenken)

INSERT INTO `customers`(`id`, `first_name`, `last_name`, `email`, `address`, `postal_code`, `city`, `country_code`, `phone`, `created_at`, `updated_at`) VALUES (10456, 'john', 'de mol', 'kinky@gmail.com', 'sendhelp69 street', '6565bh', 'modtown', 'da_DK', '123456789', NOW(), NOW()); 

Dan het bovenstaande twee keer uitvoeren

### Opdracht 3
* Geef de query om de eerste 10 boekingen te verwijderen (reservations)

DELETE FROM reservations
WHERE id IN (1,2,3,4,5,6,7,8,9,10);

### Opdracht 4
* De klant met id 13 is verhuist naar 'De van der veldensteeg 81' in 'Apeldoorn'.
* Pas het record aan en geef de query
* Toon het record en controleer of de gegevens correct zijn.

UPDATE customers
SET address = 'De van der veldensteeg 81', city = 'Apeldoorn'
WHERE id = 13;

SELECT * FROM customers WHERE id = 13;

