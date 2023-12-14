# DML exercise

Tables:

Albums:

Columns: AlbumID (Primary Key), Title, ReleaseYear, Genre, Price, StockQuantity
Artists:

Columns: ArtistID (Primary Key), ArtistName, Country

Exercise Tasks:
note: add some data entries before fetching it

mysql> CREATE DATABASE DML_exercise;
Query OK, 1 row affected (0,01 sec)

mysql> USE DML_exercise;
Database changed
mysql> CREATE TABLE albums(
    -> albumID INT PRIMARY KEY,
    -> title VARCHAR(100),
    -> releaseYear INT,
    -> genre VARCHAR(50),
    -> price DECIMAL(5, 2),
    -> stockQuantity INT
    -> );
Query OK, 0 rows affected (0,03 sec)

mysql> CREATE TABLE artists(
    -> artistID INT PRIMARY KEY,
    -> artistName VARCHAR(100),
    -> country VARCHAR(100)
    -> );
Query OK, 0 rows affected (0,03 sec)


mysql> INSERT INTO albums (albumID, title, releaseYear, genre, price, stockQuantity) 
    -> VALUES
    ->     (1, 'Thriller', 1982, 'Pop', 12.99, 100),
    ->     (2, 'The Dark Side of the Moon', 1973, 'Progressive Rock', 15.49, 75),
    ->     (3, 'Back in Black', 1980, 'Rock', 14.99, 90),
    ->     (4, 'Rumours', 1977, 'Rock', 11.89, 80),
    ->     (5, 'Abbey Road', 1969, 'Rock', 13.25, 85);
Query OK, 5 rows affected (0,01 sec)
Records: 5  Duplicates: 0  Warnings: 0


mysql> INSERT INTO artists (artistID, artistName, country) 
    -> VALUES
    ->     (1, 'Michael Jackson', 'United States'),
    ->     (2, 'Pink Floyd', 'United Kingdom'),
    ->     (3, 'AC/DC', 'Australia'),
    ->     (4, 'Fleetwood Mac', 'United Kingdom'),
    ->     (5, 'The Beatles', 'United Kingdom');
Query OK, 5 rows affected (0,01 sec)
Records: 5  Duplicates: 0  Warnings: 0



# Select Queries:

Retrieve all album titles along with their release years.
Display the genres available in the store without repetition.
List all artists' names along with their respective countries.
Fetch the album titles released in a specific year.

mysql> SELECT title, releaseYear
    -> FROM albums;
+---------------------------+-------------+
| title                     | releaseYear |
+---------------------------+-------------+
| Thriller                  |        1982 |
| The Dark Side of the Moon |        1973 |
| Back in Black             |        1980 |
| Rumours                   |        1977 |
| Abbey Road                |        1969 |
+---------------------------+-------------+
5 rows in set (0,00 sec)

mysql> SELECT DISTINCT genre
    -> FROM albums;
+------------------+
| genre            |
+------------------+
| Pop              |
| Progressive Rock |
| Rock             |
+------------------+
3 rows in set (0,02 sec)

mysql> SELECT artistName, country
    -> FROM artists;
+-----------------+----------------+
| artistName      | country        |
+-----------------+----------------+
| Michael Jackson | United States  |
| Pink Floyd      | United Kingdom |
| AC/DC           | Australia      |
| Fleetwood Mac   | United Kingdom |
| The Beatles     | United Kingdom |
+-----------------+----------------+
5 rows in set (0,00 sec)

mysql> SELECT title
    -> FROM albums
    -> WHERE releaseYear = 1977;
+---------+
| title   |
+---------+
| Rumours |
+---------+
1 row in set (0,00 sec)


# Insert Queries:

Add a new album titled "Greatest Hits" released in the year 2023 to the database with a price of $15 and a stock quantity of 50.
Insert a new artist named "New Artist" from "Canada" into the Artists table.
Update Queries:

mysql> INSERT INTO albums
    -> VAlUES(
    -> 6, 'Greatest Hits', 2023, NULL, 15.00, 50
    -> );
Query OK, 1 row affected (0,01 sec)

mysql> INSERT INTO artists
    -> VALUES(
    -> 6, 'New Artist', 'Canada'
    -> );
Query OK, 1 row affected (0,02 sec)


# Update
the price of all albums in the "Pop" genre to $20.
Increase the stock quantity of the album titled "Thriller" by 10 units.

mysql> UPDATE albums
    -> SET price = 20
    -> WHERE genre = 'Pop';
Query OK, 1 row affected (0,01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> UPDATE albums
    -> SET stockQuantity = stockQuantity + 10
    -> WHERE title = 'Thriller';
Query OK, 1 row affected (0,01 sec)
Rows matched: 1  Changed: 1  Warnings: 0



# Delete Queries:
Remove an album titled "Dangerous" from the database.
Delete an artist named "Old Artist" from the Artists table.

mysql> DELETE FROM albums
    -> WHERE title = 'Greatest Hits';
Query OK, 1 row affected (0,01 sec)

mysql> DELETE FROM artists
    -> WHERE artistName = 'New Artist';
Query OK, 1 row affected (0,01 sec)

