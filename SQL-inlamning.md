# SQL-inlämning — Diskografi

**Namn:** [Ali Kansour]  
**Artist:** [Meek Mill]  
**Datum:** [2026-10-22]

---

> Lägg länk till eller bild på ditt ER-diagram här:
> `[ER-diagram](er_diagram.png)`

---

## 1. Skapa databasen — CREATE TABLE

```sql

CREATE TABLE "Album" (
	"id"	INTEGER,
	"Titel"	TEXT NOT NULL,
	"Utgivningsar"	INTEGER NOT NULL,
	"ArtistID"	INTEGER NOT NULL,
	PRIMARY KEY("id" AUTOINCREMENT),
	FOREIGN KEY("ArtistID") REFERENCES "Artist"("id")
)
```
CREATE TABLE "Artist" (
	"id"	INTEGER,
	"Namn"	TEXT NOT NULL,
	PRIMARY KEY("id" AUTOINCREMENT)
)

---
CREATE TABLE "Latar" (
	"id"	INTEGER,
	"Titel"	TEXT NOT NULL,
	"Langdsekunder"	INTEGER NOT NULL,
	"AlbumID"	INTEGER NOT NULL,
	PRIMARY KEY("id" AUTOINCREMENT),
	FOREIGN KEY("AlbumID") REFERENCES "Album"("id")
)
## 2. Seeda med data — INSERT

```sql

INSERT INTO "Artist" ("id","Namn") VALUES (1,'Meek Mill');
```
INSERT INTO "Album" ("id","Titel","Utgivningsar","ArtistID") VALUES (1,'Dreams and Nightmares',2012,1);
INSERT INTO "Album" ("id","Titel","Utgivningsar","ArtistID") VALUES (2,'Wins & Losses',2017,1);
INSERT INTO "Album" ("id","Titel","Utgivningsar","ArtistID") VALUES (3,'Championships',2018,1);
```
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (1,'Dreams and Nightmares',235,1);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (2,'Traumatized',250,1);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (3,'Believe It',239,1);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (4,'Wins & Losses',189,2);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (5,'Heavy Heart',250,2);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (6,'1942 Flows',282,2);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (7,'Intro',213,3);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (8,'Trauma',238,3);
INSERT INTO "Latar" ("id","Titel","Langdsekunder","AlbumID") VALUES (9,'Going Bad',180,3);





## 3. Söka — SELECT

```sql
--- query 1: Lista alla album, sorterade efter år ---
SELECT *
FROM Album
ORDER BY Utgivningsar ASC;

--- query 2: Lista alla låtar på ett specifikt album ---
SELECT *
FROM Latar
WHERE AlbumID = 1;

--- query 3: Antal låtar per album ---

SELECT Album.Titel, COUNT(Latar.id) AS AntalLatar
FROM Album
LEFT JOIN Latar ON Album.id = Latar.AlbumID
GROUP BY Album.id, Album.Titel;

--- query 4: Längsta låten ---
SELECT Titel, Langdsekunder
FROM Latar
ORDER BY Langdsekunder DESC
LIMIT 1;

--- query 5: Alla låtar sorterade alfabetiskt ---
SELECT Titel
FROM Latar
ORDER BY Titel ASC;
```

---

## 4. Lägg till en ny rad — INSERT

```sql
INSERT INTO Latar (Titel, Langdsekunder, AlbumID) VALUES ('What''s Free', 362, 3);

```

---

## 5. Ta bort en rad — DELETE

```sql
DELETE FROM Latar WHERE Titel = 'What''s Free' AND AlbumID = 3; 

```

---

## 6. Uppdatera en rad — UPDATE

```sql
 UPDATE Latar SET Langdsekunder = 251 WHERE Titel = 'Traumatized' AND AlbumID = 1; 

```

---

## 7. VG-queries (om du siktar på VG)

```sql
--- query 6: Snittlängd på låtar per album ---


--- query 7: Albumet med flest låtar ---


--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---

```
