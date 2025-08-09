Evo kompletno urađenog domaćeg zadatka za **osnovni nivo SQL**. Ispod svakog zadatka nalazi se odgovarajući SQL upit.

---

# **SQL Domaći zadatak – Osnovni nivo**

## **1\. Ispišite ime, prezime, patronus svih likova koji imaju patronusa i on je poznat.**

SELECT fname, lname, patronus  
FROM characters  
WHERE patronus IS NOT NULL AND patronus \<\> '';

---

## **2\. Ispišite prezime likova čije prezime završava slovom 'e'.**

SELECT lname  
FROM characters  
WHERE lname LIKE '%e';

---

## **3\. Izračunajte ukupne godine svih likova i ispišite to na ekran.**

SELECT SUM(age) AS total\_age  
FROM characters;

---

## **4\. Ispišite ime, prezime i godine likova po opadajućem redosledu njihovih godina.**

SELECT fname, lname, age  
FROM characters  
ORDER BY age DESC;

---

## **5\. Ispišite ime likova i godine onih čije godine su u rasponu od 50 do 100 godina.**

SELECT fname, age  
FROM characters  
WHERE age BETWEEN 50 AND 100;

---

## **6\. Ispišite godine svih likova tako da među njima nema onih sa istim godinama.**

SELECT DISTINCT age  
FROM characters;

---

## **7\. Ispišite sve informacije o likovima čiji je faculty \= Gryffindor i čije su godine preko 30\.**

SELECT \*  
FROM characters  
WHERE faculty \= 'Gryffindor' AND age \> 30;

---

## **8\. Ispišite imena prva tri fakulteta iz tabele tako da se fakulteti ne ponavljaju.**

SELECT DISTINCT faculty  
FROM characters  
WHERE faculty IS NOT NULL AND faculty \<\> ''  
LIMIT 3;

---

## **9\. Ispišite imena likova čije ime počinje sa 'N' i ima 5 slova, ili čije ime počinje sa 'L'.**

SELECT fname  
FROM characters  
WHERE (fname LIKE 'N\_\_\_\_') OR (fname LIKE 'L%');

---

## **10\. Izračunajte prosečne godine svih likova.**

SELECT AVG(age) AS average\_age  
FROM characters;

---

## **11\. Obrišite lika sa ID \= 11\.**

DELETE FROM characters  
WHERE id \= 11;

---

## **12\. Ispišite prezime svih likova koja sadrže slovo 'a'.**

SELECT lname  
FROM characters  
WHERE lname LIKE '%a%';

---

## **13\. Koristite pseudonim da privremeno zamenite naziv kolone fname u Half-Blood Prince za stvarnog princa-polukrvnog.**

SELECT fname AS 'Half-Blood Prince'  
FROM characters;

---

## **14\. Ispišite id i imena svih patronusa po abecednom redu, pod uslovom da su poznati.**

SELECT id, patronus  
FROM characters  
WHERE patronus IS NOT NULL AND patronus \<\> ''  
ORDER BY patronus ASC;

---

## **15\. Koristite operator IN, ispišite ime i prezime likova čije je prezime Crabbe, Granger ili Diggory.**

SELECT fname, lname  
FROM characters  
WHERE lname IN ('Crabbe', 'Granger', 'Diggory');

---

## **16\. Ispišite minimalne godine likova.**

SELECT MIN(age) AS minimal\_age  
FROM characters;

---

## **17\. Koristite operator UNION, ispišite imena iz tabele characters i naslove knjiga iz tabele library.**

SELECT fname AS name  
FROM characters  
UNION  
SELECT title AS name  
FROM library;

---

## **18\. Koristite operator HAVING, izračunajte broj likova po svakom fakultetu, ostavljajući samo one fakultete gde je broj studenata veći od 1\.**

SELECT faculty, COUNT(\*) AS number\_of\_students  
FROM characters  
GROUP BY faculty  
HAVING COUNT(\*) \> 1;

---

## **NAPREDNI NIVO**

### **1\. Ispišite ime, prezime likova i naziv knjige koja im pripada.**

sql  
CopyEdit  
`SELECT c.fname, c.lname, l.title`  
`FROM characters c`  
`JOIN library l ON c.id = l.character_id;`

---

### **2\. Ispišite ime, prezime likova i naziv knjige, bez obzira na to da li imaju knjige ili ne.**

sql  
CopyEdit  
`SELECT c.fname, c.lname, l.title`  
`FROM characters c`  
`LEFT JOIN library l ON c.id = l.character_id;`

---

### **3\. Ispišite naziv knjige i ime patronusa, bez obzira na to da li je informacija o vlasniku knjige u tabeli ili ne.**

sql  
CopyEdit  
`SELECT l.title, c.patronus`  
`FROM library l`  
`LEFT JOIN characters c ON l.character_id = c.id;`

---

### **4\. Ispišite ime, prezime, godine likova i naziv knjige koja im pripada, pod uslovom da su svi vlasnici knjiga stariji od 15 godina.**

sql  
CopyEdit  
`SELECT c.fname, c.lname, c.age, l.title`  
`FROM characters c`  
`JOIN library l ON c.id = l.character_id`  
`WHERE c.age > 15;`

---

### **5\. Ispišite ime lika, naziv knjige, datum izdavanja i datum završetka, pod uslovom da je mlađi od 15 godina i njegov patronus nije poznat.**

sql  
CopyEdit  
SELECT characters.fname, library.book\_name, library.start\_date, library.end\_date  
FROM characters  
JOIN library ON characters.book\_id \= library.book\_id  
WHERE characters.age \< 15 AND patronus IS UNKNOWN;

---

### **6\. Koristite ugnježđeni upit za broj knjiga čiji je end\_date veći od end\_date kod Hermione.**

sql  
CopyEdit  
`SELECT COUNT(*) AS number_of_books`  
`FROM library`  
`WHERE end_date > (`  
    `SELECT end_date`  
    `FROM library l`  
    `JOIN characters c ON l.character_id = c.id`  
    `WHERE c.fname = 'Hermione'`  
    `LIMIT 1`  
`);`

---

### **7\. Pomoću ugnježdenog upita ispišite imena svih patronusa čiji su vlasnici stariji od lika čiji je patronus Unknown.**

sql  
CopyEdit  
`SELECT patronus`  
`FROM characters`  
`WHERE age > (`  
    `SELECT age`  
    `FROM characters`  
    `WHERE patronus = 'Unknown'`  
    `LIMIT 1`  
`)`  
`AND patronus IS NOT NULL AND patronus <> '';`  
