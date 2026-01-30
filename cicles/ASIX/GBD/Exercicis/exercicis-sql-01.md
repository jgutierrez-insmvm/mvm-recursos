# Exercicis SQL: Consultes a la base de dades Pagila
**Objectiu:** Practicar sentències SELECT bàsiques, filtratge, ordenació i funcions d'agregació;

---

### 1. Consultes Bàsiques (SELECT)
1.  Selecciona totes les dades de la taula d'actors (`actor`). 

`SELECT * FROM actor`

2.  Selecciona només el nom (`first_name`), cognom (`last_name`) i el correu electrònic (`email`) de tots els clients (`customer`).

`SELECT first_name, last_name, email FROM customer`

3.  Selecciona el títol (`title`) i la descripció (`description`) de totes les pel·lícules (`film`).

`SELECT title, description FROM film;`

---

### 2. Filtratge de Dades (WHERE)
4.  Selecciona totes les pel·lícules que tinguin una classificació (`rating`) de 'G'.

`SELECT * FROM film WHERE rating='G';`

5.  Selecciona totes les pel·lícules que durin (`length`) més de 120 minuts.

`SELECT * FROM film WHERE length>120;`

6.  Troba els pagaments (`payment`) on l'import (`amount`) sigui exactament 0.99.

`SELECT * FROM payment WHERE amount='0.99';`

7.  Selecciona les pel·lícules que tinguin una durada de lloguer (`rental_duration`) de 3 dies o de 5 dies.

`SELECT * FROM film WHERE rental_duration in (3,5);`

---

### 3. Funcions d'Agregació (COUNT, SUM, AVG, MIN/MAX)
8.  Quantes pel·lícules hi ha registrades en total a la taula `film`?

`SELECT COUNT(*) FROM film;`

9.  Calcula el total de diners recaptats registrats a la taula de pagaments (`payment`).

`SELECT SUM(amount) FROM payment;`

10. Quina és la durada mitjana (`length`) de totes les pel·lícules de la base de dades?

`SELECT AVG(length) FROM film;`

11. Quin és el cost de reemplaçament (`replacement_cost`) més alt i el més baix de les pel·lícules?

`SELECT MIN(replacement_cost) AS minimo FROM film;
SELECT MAX(replacement_cost) AS  maximo FROM film;`

---

### 4. Ordenació de Resultats (ORDER BY)
12. Llista els títols de les pel·lícules ordenats alfabèticament (A-Z).

`SELECT * FROM film ORDER BY title;`

13. Llista els clients ordenats pel seu cognom (`last_name`) de forma descendent (Z-A).

`SELECT * FROM customer ORDER BY last_name DESC;`

14. Mostra les pel·lícules ordenades per durada (`length`), de la més llarga a la més curta.

`SELECT * FROM film ORDER BY length DESC;`

---

### 5. Limitació de Resultats (LIMIT)
15. Mostra només les 5 primeres files de la taula d'actors (`actor`).

`SELECT * FROM film ORDER BY length DESC;`

16. Mostra els 10 pagaments (`payment`) amb l'import (`amount`) més alt (requereix ordenar primer).

`SELECT * FROM payment ORDER BY amount DESC LIMIT 10;`

---

### 6. Exercicis Combinats
17. Troba les 5 pel·lícules més llargues que tinguin una classificació (`rating`) de 'PG-13'.

`SELECT * FROM film WHERE rating='PG-13' ORDER BY length DESC LIMIT 5;`

18. Calcula la mitjana de l'import dels pagaments, però tenint en compte només aquells pagaments superiors a 5.99.

`SELECT AVG(amount) FROM payment WHERE amount>5.99;`

19. Troba el títol i el cost de reemplaçament de les 3 pel·lícules més barates de reemplaçar (`replacement_cost`), però que la seva durada sigui superior a 100 minuts.

`SELECT title, replacement_cost FROM film WHERE length>100 ORDER BY length LIMIT 3;`

20. Compta quants clients estan "actius" (camp `active` = 1) i tenen una adreça de correu electrònic que comença per la lletra 'M' (Pista: utilitza `LIKE 'M%'`).

`SELECT COUNT(*) FROM customer WHERE active='1' AND email LIKE 'M%';`
