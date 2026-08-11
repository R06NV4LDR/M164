#### TOC
- [[#Theorie]] |
	- [[#1. Was ist hier falsch?]] |
    - [[#2. Ordnen Sie die SQL-Befehle den Gruppen zu]] |
	- [[#3. Welche Aussagen zu Beziehungen sind richtig?]] |
	- [[#4. Ordnen Sie die korrekten Fachbegriffe zu!]] | [[]] | 
- [[#Praktischer Teil]] | [[]] | 
	- [[#1. Erstellen Sie eine Datenbank "db_ubs"]] | [[]] | 
	- [[#2. Erstellen Sie eine Tabelle KundenInfo mit folgenden Attributen]] | [[]] | 
    - [[#3. Daten in Kurzform einsetzen]] | [[]] | 
	- [[#4. Daten in Langform einsetzen]] | [[]] | 
	- [[#5. Spalte "geändert_am" hinzufügen]] | [[]] | 
    - [[]] | [[]] | 
	- [[]] | [[]] | 
- [[]] |
## Theorie Teil

#### 1. Was ist hier falsch? 
###### (Annahme dass Tabelle und Attribute existieren!)

```SQL
INSERT INTO customers (name, email, address)
SELECT name, email, address
FROM new_customers;
```
- [ ] Alles korrekt: Kopiert Datensatz von anderer Tabelle✅
- [ ] Man kann INSERT und SELECT nicht mischen❌
- [ ] Es fehlt VALUES (...) ❌
- [ ] Es fehlt ein " ; " am Ende der Zeile INSERT ❌

---
#### 2. Ordnen Sie die SQL-Befehle den Gruppen zu:

(a) DDL
(b) DML
(c) DQL

[c] SELECT
[a] ALTER
[b] UPDATE
[b] DELETE
[a] DROP

---
### 3. Welche Aussagen zu Beziehungen sind richtig?

(a) **Zu jeder** Beziehung gehört ein Fremdschlüssel✅
(b) **Jeder** Primärschlüssel **hat einen** Bezug zu einem Fremdschlüssel❌
(c) Eine Zwischentabelle hat **mindestens** zwei c:m(c) Beziehungen❌
(d) Ein Fremdschlüssel ist ein **"constraint"**✅
(e) Eine **1:1** Beziehung ist immer eine "identifying"-Beziehung❌
(f) **NOT NULL** und **UNIQUE** sind constraints bei Fremd- und Primärschlüssel✅
(g) Eine Zwischentabelle kann auch **drei** Entitäten miteinander verbinden✅

---
### 4. Ordnen Sie die korrekten Fachbegriffe zu!

![[m164_LB1_DB_Fachbegriffe 1.png]]
(a) Management System
(b) SQL / SQL-Script
(c) DB-Server / Datenbanksystem
(d) SQL-Client
(e) DBMS
(f) Datenstruktur
(g) Daten
(h) Datenbasis / Datenbank!

---
## Praktischer Teil

![[m164_LB1_KundenInfo_table.png]]
### 1. Erstellen Sie die Datenbasis auf ihrem DB-Server
### und "aktivieren" Sie diese:
```SQL
create database db_ubs;
use db_ubs;
```

---
### 2. Erstellen Sie die Tabelle
### mit ihren Attributen und Einstellungen (constraints) gemäss dem obigen Schema.

```SQL
create table KundenInfo (
ID_Kunde int primary key auto_increment not null,
Nachname varchar(50) not null,
Kontonummer varchar(5) not null,
SWIFT int,
Kontostand decimal(10,2),
Erstellt_am date
);
```

---
### 3.  Füllen Sie den ganzen ersten Datensatz mit ihren persönlichen Daten
### Verwenden Sie dazu die *Kurzform* des SQL-Befehls.

```SQL
insert into KundenInfo
values (null, "Bruhin", "12345" , "9876", "000000.00", "2024-03-15");
```

---
### 4. Füllen Sie den zweiten Datensatz
### mit *vier weiteren, lückenhaften* Werten in der *Langform* des SQL-Befehls.

```SQL
insert into KundenInfo (Nachname, Kontonummer, Erstellt_am)
values ("Seker", "23456", "1999-12-31"), ("Evans", "34567", "2010-06-06");

insert into KundenInfo (Nachname, Kontonummer, Kontostand)
values ("Aksoy", "45678", "9999999.99"), ("Burger", "56789", "55555555.55");
```

---
### 5. Fügen Sie ein neues Attribut 'geändert_am' hinzu.
### Verwenden Sie den Datentyp *DateTime*.

```SQL
alter table kundeninfo
add geändert_am datetime;
```

---
### 6. Erhöhen Sie ihren *eigenen* Kontostand:
### Gehen Sie dabei vom *aktuellen* Kontostand aus und *addieren* Sie 1000.- CHF dazu.

```SQL
UPDATE KundenInfo
SET Kontostand = Kontostand + 1000
WHERE Nachname = "Bruhin"
```

---
### 7.  Bereiten Sie eine *zukünftige Abfrage* vor
### die *folgende Bedingungen erfüllt*:
- Die Abfragetabelle soll ID, Nachname, Kontonummer und Kontostand beinhalten,
- dabei Nachname aufsteigend und Kontostand absteigend sortieren;
- Die Abfragetabelle zeigt alle Personen deren Nachname mit 'Par' beginnen
- oder eine Kontonummer grösser als 3322 haben
- und all diese Personen mit Kontostand kleiner oder gleich 100.- CHF

```SQL
select ID_Kunde, Nachname, Kontonummer, Kontostand from KundenInfo
where Nachname like "Par%" or  Kontonummer > 3322
and Kontostand <= 100
order by Nachname asc, Kontostand desc;
```

---