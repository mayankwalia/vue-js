```sql
mysql> create atble reviewers (id int primary key auto_increment,first_name varchar(50) not null,last_name varchar(50) not null);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'atble reviewers (id int primary key auto_increment,first_name varchar(50) not nu' at line 1
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| book_shop          |
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| shop               |
| sys                |
| tea_shop           |
| test               |
| world              |
+--------------------+
10 rows in set (0.02 sec)

mysql> create database books
    -> ;
Query OK, 1 row affected (0.05 sec)

mysql> use books
Database changed
mysql> create atble reviewers (id int primary key auto_increment,first_name varchar(50) not null,last_name varchar(50) not null);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'atble reviewers (id int primary key auto_increment,first_name varchar(50) not nu' at line 1
mysql> create table reviewers (id int primary key auto_increment,first_name varchar(50) not null,last_name varchar(50) not null);
Query OK, 0 rows affected (0.17 sec)

mysql> create table reviewers (id int primary key auto_increment,first_name varchar(50) not null,last_name varchar(50) not null);^C
mysql> create table series (id int primary key auto_increment, title varchar(100), releaesed year year, genre varchar(100));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'year, genre varchar(100))' at line 1
mysql> create table series (id int primary key auto_increment, title varchar(100), releaesed year, genre varchar(100));
Query OK, 0 rows affected (0.10 sec)

mysql> create table reviews(id int primary key auto_increment,rating decimal(2,1),series_id int,reviewer_id int, foreign key (series_id) references foreign key series(id),foreign key (reviewer_id) references reviewers(id));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'foreign key series(id),foreign key (reviewer_id) references reviewers(id))' at line 1
mysql> create table reviews(id int primary key auto_increment,rating decimal(2,1),series_id int,reviewer_id int, foreign key (series_id) references series(id),foreign key (reviewer_id) references reviewers(id));
Query OK, 0 rows affected (0.16 sec)

mysql> show tables;
+-----------------+
| Tables_in_books |
+-----------------+
| reviewers       |
| reviews         |
| series          |
+-----------------+
3 rows in set (0.06 sec)

mysql> desc reviews;
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| id          | int          | NO   | PRI | NULL    | auto_increment |
| rating      | decimal(2,1) | YES  |     | NULL    |                |
| series_id   | int          | YES  | MUL | NULL    |                |
| reviewer_id | int          | YES  | MUL | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> INSERT INTO series (title, released_year, genre) VALUES
    ->     ('Archer', 2009, 'Animation'),
    ->     ('Arrested Development', 2003, 'Comedy'),
    ->     ("Bob's Burgers", 2011, 'Animation'),
    ->     ('Bojack Horseman', 2014, 'Animation'),
    ->     ("Breaking Bad", 2008, 'Drama'),
    ->     ('Curb Your Enthusiasm', 2000, 'Comedy'),
    ->     ("Fargo", 2014, 'Drama'),
    ->     ('Freaks and Geeks', 1999, 'Comedy'),
    ->     ('General Hospital', 1963, 'Drama'),
    ->     ('Halt and Catch Fire', 2014, 'Drama'),
    ->     ('Malcolm In The Middle', 2000, 'Comedy'),
    ->     ('Pushing Daisies', 2007, 'Comedy'),
    ->     ('Seinfeld', 1989, 'Comedy'),
    ->     ('Stranger Things', 2016, 'Drama');
ERROR 1054 (42S22): Unknown column 'released_year' in 'field list'
mysql>
mysql>
mysql> INSERT INTO reviewers (first_name, last_name) VALUES
    ->     ('Thomas', 'Stoneman'),
    ->     ('Wyatt', 'Skaggs'),
    ->     ('Kimbra', 'Masters'),
    ->     ('Domingo', 'Cortes'),
    ->     ('Colt', 'Steele'),
    ->     ('Pinkie', 'Petit'),
    ->     ('Marlon', 'Crafford');
Query OK, 7 rows affected (0.01 sec)
Records: 7  Duplicates: 0  Warnings: 0

mysql>
mysql>
mysql> INSERT INTO reviews(series_id, reviewer_id, rating) VALUES
    ->     (1,1,8.0),(1,2,7.5),(1,3,8.5),(1,4,7.7),(1,5,8.9),
    ->     (2,1,8.1),(2,4,6.0),(2,3,8.0),(2,6,8.4),(2,5,9.9),
    ->     (3,1,7.0),(3,6,7.5),(3,4,8.0),(3,3,7.1),(3,5,8.0),
    ->     (4,1,7.5),(4,3,7.8),(4,4,8.3),(4,2,7.6),(4,5,8.5),
    ->     (5,1,9.5),(5,3,9.0),(5,4,9.1),(5,2,9.3),(5,5,9.9),
    ->     (6,2,6.5),(6,3,7.8),(6,4,8.8),(6,2,8.4),(6,5,9.1),
    ->     (7,2,9.1),(7,5,9.7),
    ->     (8,4,8.5),(8,2,7.8),(8,6,8.8),(8,5,9.3),
    ->     (9,2,5.5),(9,3,6.8),(9,4,5.8),(9,6,4.3),(9,5,4.5),
    ->     (10,5,9.9),
    ->     (13,3,8.0),(13,4,7.2),
    ->     (14,2,8.5),(14,3,8.9),(14,4,8.9);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`books`.`reviews`, CONSTRAINT `reviews_ibfk_1` FOREIGN KEY (`series_id`) REFERENCES `series` (`id`))
mysql> INSERT INTO reviews(series_id, reviewer_id, rating) VALUES
    ->     (1,1,8.0),(1,2,7.5),(1,3,8.5),(1,4,7.7),(1,5,8.9),
    ->     (2,1,8.1),(2,4,6.0),(2,3,8.0),(2,6,8.4),(2,5,9.9),
    ->     (3,1,7.0),(3,6,7.5),(3,4,8.0),(3,3,7.1),(3,5,8.0),
    ->     (4,1,7.5),(4,3,7.8),(4,4,8.3),(4,2,7.6),(4,5,8.5),
    ->     (5,1,9.5),(5,3,9.0),(5,4,9.1),(5,2,9.3),(5,5,9.9),
    ->     (6,2,6.5),(6,3,7.8),(6,4,8.8),(6,2,8.4),(6,5,9.1),
    ->     (7,2,9.1),(7,5,9.7),
    ->     (8,4,8.5),(8,2,7.8),(8,6,8.8),(8,5,9.3),
    ->     (9,2,5.5),(9,3,6.8),(9,4,5.8),(9,6,4.3),(9,5,4.5),
    ->     (10,5,9.9),
    ->     (13,3,8.0),(13,4,7.2),
    ->     (14,2,8.5),(14,3,8.9),(14,4,8.9);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`books`.`reviews`, CONSTRAINT `reviews_ibfk_1` FOREIGN KEY (`series_id`) REFERENCES `series` (`id`))
mysql> desc reviewers;
+------------+-------------+------+-----+---------+----------------+
| Field      | Type        | Null | Key | Default | Extra          |
+------------+-------------+------+-----+---------+----------------+
| id         | int         | NO   | PRI | NULL    | auto_increment |
| first_name | varchar(50) | NO   |     | NULL    |                |
| last_name  | varchar(50) | NO   |     | NULL    |                |
+------------+-------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)

mysql> desc series;
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| id        | int          | NO   | PRI | NULL    | auto_increment |
| title     | varchar(100) | YES  |     | NULL    |                |
| releaesed | year         | YES  |     | NULL    |                |
| genre     | varchar(100) | YES  |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> alter table series modify releaesed to released_year;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to released_year' at line 1
mysql> alter table series rename releaesed to released_year;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to released_year' at line 1
mysql> alter table series rename column releaesed to released_year;
Query OK, 0 rows affected (0.10 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> INSERT INTO reviews(series_id, reviewer_id, rating) VALUES
    ->     (1,1,8.0),(1,2,7.5),(1,3,8.5),(1,4,7.7),(1,5,8.9),
    ->     (2,1,8.1),(2,4,6.0),(2,3,8.0),(2,6,8.4),(2,5,9.9),
    ->     (3,1,7.0),(3,6,7.5),(3,4,8.0),(3,3,7.1),(3,5,8.0),
    ->     (4,1,7.5),(4,3,7.8),(4,4,8.3),(4,2,7.6),(4,5,8.5),
    ->     (5,1,9.5),(5,3,9.0),(5,4,9.1),(5,2,9.3),(5,5,9.9),
    ->     (6,2,6.5),(6,3,7.8),(6,4,8.8),(6,2,8.4),(6,5,9.1),
    ->     (7,2,9.1),(7,5,9.7),
    ->     (8,4,8.5),(8,2,7.8),(8,6,8.8),(8,5,9.3),
    ->     (9,2,5.5),(9,3,6.8),(9,4,5.8),(9,6,4.3),(9,5,4.5),
    ->     (10,5,9.9),
    ->     (13,3,8.0),(13,4,7.2),
    ->     (14,2,8.5),(14,3,8.9),(14,4,8.9);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`books`.`reviews`, CONSTRAINT `reviews_ibfk_1` FOREIGN KEY (`series_id`) REFERENCES `series` (`id`))
mysql> INSERT INTO series (title, released_year, genre) VALUES
    ->     ('Archer', 2009, 'Animation'),
    ->     ('Arrested Development', 2003, 'Comedy'),
    ->     ("Bob's Burgers", 2011, 'Animation'),
    ->     ('Bojack Horseman', 2014, 'Animation'),
    ->     ("Breaking Bad", 2008, 'Drama'),
    ->     ('Curb Your Enthusiasm', 2000, 'Comedy'),
    ->     ("Fargo", 2014, 'Drama'),
    ->     ('Freaks and Geeks', 1999, 'Comedy'),
    ->     ('General Hospital', 1963, 'Drama'),
    ->     ('Halt and Catch Fire', 2014, 'Drama'),
    ->     ('Malcolm In The Middle', 2000, 'Comedy'),
    ->     ('Pushing Daisies', 2007, 'Comedy'),
    ->     ('Seinfeld', 1989, 'Comedy'),
    ->     ('Stranger Things', 2016, 'Drama');
Query OK, 14 rows affected (0.03 sec)
Records: 14  Duplicates: 0  Warnings: 0

mysql>  INSERT INTO reviews(series_id, reviewer_id, rating) VALUES
    ->     (1,1,8.0),(1,2,7.5),(1,3,8.5),(1,4,7.7),(1,5,8.9),
    ->     (2,1,8.1),(2,4,6.0),(2,3,8.0),(2,6,8.4),(2,5,9.9),
    ->     (3,1,7.0),(3,6,7.5),(3,4,8.0),(3,3,7.1),(3,5,8.0),
    ->     (4,1,7.5),(4,3,7.8),(4,4,8.3),(4,2,7.6),(4,5,8.5),
    ->     (5,1,9.5),(5,3,9.0),(5,4,9.1),(5,2,9.3),(5,5,9.9),
    ->     (6,2,6.5),(6,3,7.8),(6,4,8.8),(6,2,8.4),(6,5,9.1),
    ->     (7,2,9.1),(7,5,9.7),
    ->     (8,4,8.5),(8,2,7.8),(8,6,8.8),(8,5,9.3),
    ->     (9,2,5.5),(9,3,6.8),(9,4,5.8),(9,6,4.3),(9,5,4.5),
    ->     (10,5,9.9),
    ->     (13,3,8.0),(13,4,7.2),
    ->     (14,2,8.5),(14,3,8.9),(14,4,8.9);
Query OK, 47 rows affected (0.05 sec)
Records: 47  Duplicates: 0  Warnings: 0

mysql> select * from series;
+----+-----------------------+---------------+-----------+
| id | title                 | released_year | genre     |
+----+-----------------------+---------------+-----------+
|  1 | Archer                |          2009 | Animation |
|  2 | Arrested Development  |          2003 | Comedy    |
|  3 | Bob's Burgers         |          2011 | Animation |
|  4 | Bojack Horseman       |          2014 | Animation |
|  5 | Breaking Bad          |          2008 | Drama     |
|  6 | Curb Your Enthusiasm  |          2000 | Comedy    |
|  7 | Fargo                 |          2014 | Drama     |
|  8 | Freaks and Geeks      |          1999 | Comedy    |
|  9 | General Hospital      |          1963 | Drama     |
| 10 | Halt and Catch Fire   |          2014 | Drama     |
| 11 | Malcolm In The Middle |          2000 | Comedy    |
| 12 | Pushing Daisies       |          2007 | Comedy    |
| 13 | Seinfeld              |          1989 | Comedy    |
| 14 | Stranger Things       |          2016 | Drama     |
+----+-----------------------+---------------+-----------+
14 rows in set (0.00 sec)

mysql> select * from reviewers;
+----+------------+-----------+
| id | first_name | last_name |
+----+------------+-----------+
|  1 | Thomas     | Stoneman  |
|  2 | Wyatt      | Skaggs    |
|  3 | Kimbra     | Masters   |
|  4 | Domingo    | Cortes    |
|  5 | Colt       | Steele    |
|  6 | Pinkie     | Petit     |
|  7 | Marlon     | Crafford  |
+----+------------+-----------+
7 rows in set (0.00 sec)

mysql> select * from reviews;
+-----+--------+-----------+-------------+
| id  | rating | series_id | reviewer_id |
+-----+--------+-----------+-------------+
| 142 |    8.0 |         1 |           1 |
| 143 |    7.5 |         1 |           2 |
| 144 |    8.5 |         1 |           3 |
| 145 |    7.7 |         1 |           4 |
| 146 |    8.9 |         1 |           5 |
| 147 |    8.1 |         2 |           1 |
| 148 |    6.0 |         2 |           4 |
| 149 |    8.0 |         2 |           3 |
| 150 |    8.4 |         2 |           6 |
| 151 |    9.9 |         2 |           5 |
| 152 |    7.0 |         3 |           1 |
| 153 |    7.5 |         3 |           6 |
| 154 |    8.0 |         3 |           4 |
| 155 |    7.1 |         3 |           3 |
| 156 |    8.0 |         3 |           5 |
| 157 |    7.5 |         4 |           1 |
| 158 |    7.8 |         4 |           3 |
| 159 |    8.3 |         4 |           4 |
| 160 |    7.6 |         4 |           2 |
| 161 |    8.5 |         4 |           5 |
| 162 |    9.5 |         5 |           1 |
| 163 |    9.0 |         5 |           3 |
| 164 |    9.1 |         5 |           4 |
| 165 |    9.3 |         5 |           2 |
| 166 |    9.9 |         5 |           5 |
| 167 |    6.5 |         6 |           2 |
| 168 |    7.8 |         6 |           3 |
| 169 |    8.8 |         6 |           4 |
| 170 |    8.4 |         6 |           2 |
| 171 |    9.1 |         6 |           5 |
| 172 |    9.1 |         7 |           2 |
| 173 |    9.7 |         7 |           5 |
| 174 |    8.5 |         8 |           4 |
| 175 |    7.8 |         8 |           2 |
| 176 |    8.8 |         8 |           6 |
| 177 |    9.3 |         8 |           5 |
| 178 |    5.5 |         9 |           2 |
| 179 |    6.8 |         9 |           3 |
| 180 |    5.8 |         9 |           4 |
| 181 |    4.3 |         9 |           6 |
| 182 |    4.5 |         9 |           5 |
| 183 |    9.9 |        10 |           5 |
| 184 |    8.0 |        13 |           3 |
| 185 |    7.2 |        13 |           4 |
| 186 |    8.5 |        14 |           2 |
| 187 |    8.9 |        14 |           3 |
| 188 |    8.9 |        14 |           4 |
+-----+--------+-----------+-------------+
47 rows in set (0.00 sec)

mysql> select title, rating from reviews,reviewers where reviews.reviewer_id =reviewer.id;
ERROR 1054 (42S22): Unknown column 'title' in 'field list'
mysql> select title, rating from reviews,series where reviews.series_id =series.id;
+----------------------+--------+
| title                | rating |
+----------------------+--------+
| Archer               |    8.0 |
| Archer               |    7.5 |
| Archer               |    8.5 |
| Archer               |    7.7 |
| Archer               |    8.9 |
| Arrested Development |    8.1 |
| Arrested Development |    6.0 |
| Arrested Development |    8.0 |
| Arrested Development |    8.4 |
| Arrested Development |    9.9 |
| Bob's Burgers        |    7.0 |
| Bob's Burgers        |    7.5 |
| Bob's Burgers        |    8.0 |
| Bob's Burgers        |    7.1 |
| Bob's Burgers        |    8.0 |
| Bojack Horseman      |    7.5 |
| Bojack Horseman      |    7.8 |
| Bojack Horseman      |    8.3 |
| Bojack Horseman      |    7.6 |
| Bojack Horseman      |    8.5 |
| Breaking Bad         |    9.5 |
| Breaking Bad         |    9.0 |
| Breaking Bad         |    9.1 |
| Breaking Bad         |    9.3 |
| Breaking Bad         |    9.9 |
| Curb Your Enthusiasm |    6.5 |
| Curb Your Enthusiasm |    7.8 |
| Curb Your Enthusiasm |    8.8 |
| Curb Your Enthusiasm |    8.4 |
| Curb Your Enthusiasm |    9.1 |
| Fargo                |    9.1 |
| Fargo                |    9.7 |
| Freaks and Geeks     |    8.5 |
| Freaks and Geeks     |    7.8 |
| Freaks and Geeks     |    8.8 |
| Freaks and Geeks     |    9.3 |
| General Hospital     |    5.5 |
| General Hospital     |    6.8 |
| General Hospital     |    5.8 |
| General Hospital     |    4.3 |
| General Hospital     |    4.5 |
| Halt and Catch Fire  |    9.9 |
| Seinfeld             |    8.0 |
| Seinfeld             |    7.2 |
| Stranger Things      |    8.5 |
| Stranger Things      |    8.9 |
| Stranger Things      |    8.9 |
+----------------------+--------+
47 rows in set (0.00 sec)

mysql> select title,rating from series join reviews on series.id=reviews.series_id;
+----------------------+--------+
| title                | rating |
+----------------------+--------+
| Archer               |    8.0 |
| Archer               |    7.5 |
| Archer               |    8.5 |
| Archer               |    7.7 |
| Archer               |    8.9 |
| Arrested Development |    8.1 |
| Arrested Development |    6.0 |
| Arrested Development |    8.0 |
| Arrested Development |    8.4 |
| Arrested Development |    9.9 |
| Bob's Burgers        |    7.0 |
| Bob's Burgers        |    7.5 |
| Bob's Burgers        |    8.0 |
| Bob's Burgers        |    7.1 |
| Bob's Burgers        |    8.0 |
| Bojack Horseman      |    7.5 |
| Bojack Horseman      |    7.8 |
| Bojack Horseman      |    8.3 |
| Bojack Horseman      |    7.6 |
| Bojack Horseman      |    8.5 |
| Breaking Bad         |    9.5 |
| Breaking Bad         |    9.0 |
| Breaking Bad         |    9.1 |
| Breaking Bad         |    9.3 |
| Breaking Bad         |    9.9 |
| Curb Your Enthusiasm |    6.5 |
| Curb Your Enthusiasm |    7.8 |
| Curb Your Enthusiasm |    8.8 |
| Curb Your Enthusiasm |    8.4 |
| Curb Your Enthusiasm |    9.1 |
| Fargo                |    9.1 |
| Fargo                |    9.7 |
| Freaks and Geeks     |    8.5 |
| Freaks and Geeks     |    7.8 |
| Freaks and Geeks     |    8.8 |
| Freaks and Geeks     |    9.3 |
| General Hospital     |    5.5 |
| General Hospital     |    6.8 |
| General Hospital     |    5.8 |
| General Hospital     |    4.3 |
| General Hospital     |    4.5 |
| Halt and Catch Fire  |    9.9 |
| Seinfeld             |    8.0 |
| Seinfeld             |    7.2 |
| Stranger Things      |    8.5 |
| Stranger Things      |    8.9 |
| Stranger Things      |    8.9 |
+----------------------+--------+
47 rows in set (0.00 sec)

mysql> select title,avg(rating) as average_rating from series join reviews on series.id=reviews.series_id group by title;
+----------------------+----------------+
| title                | average_rating |
+----------------------+----------------+
| Archer               |        8.12000 |
| Arrested Development |        8.08000 |
| Bob's Burgers        |        7.52000 |
| Bojack Horseman      |        7.94000 |
| Breaking Bad         |        9.36000 |
| Curb Your Enthusiasm |        8.12000 |
| Fargo                |        9.40000 |
| Freaks and Geeks     |        8.60000 |
| General Hospital     |        5.38000 |
| Halt and Catch Fire  |        9.90000 |
| Seinfeld             |        7.60000 |
| Stranger Things      |        8.76667 |
+----------------------+----------------+
12 rows in set (0.05 sec)

mysql> select title,avg(rating) as average_rating from series join reviews on series.id=reviews.series_id group by title order by average_rating;
+----------------------+----------------+
| title                | average_rating |
+----------------------+----------------+
| General Hospital     |        5.38000 |
| Bob's Burgers        |        7.52000 |
| Seinfeld             |        7.60000 |
| Bojack Horseman      |        7.94000 |
| Arrested Development |        8.08000 |
| Archer               |        8.12000 |
| Curb Your Enthusiasm |        8.12000 |
| Freaks and Geeks     |        8.60000 |
| Stranger Things      |        8.76667 |
| Breaking Bad         |        9.36000 |
| Fargo                |        9.40000 |
| Halt and Catch Fire  |        9.90000 |
+----------------------+----------------+
12 rows in set (0.00 sec)

mysql> select title,round(avg(rating),2) as average_rating from series join reviews on series.id=reviews.series_id group by title order by average_rating;
+----------------------+----------------+
| title                | average_rating |
+----------------------+----------------+
| General Hospital     |           5.38 |
| Bob's Burgers        |           7.52 |
| Seinfeld             |           7.60 |
| Bojack Horseman      |           7.94 |
| Arrested Development |           8.08 |
| Archer               |           8.12 |
| Curb Your Enthusiasm |           8.12 |
| Freaks and Geeks     |           8.60 |
| Stranger Things      |           8.77 |
| Breaking Bad         |           9.36 |
| Fargo                |           9.40 |
| Halt and Catch Fire  |           9.90 |
+----------------------+----------------+
12 rows in set (0.01 sec)

mysql> select first_name,last_name,rating from reviews join series on series.id=reviews.series_id join reviewers on reviewer_id=reviewers.id;
+------------+-----------+--------+
| first_name | last_name | rating |
+------------+-----------+--------+
| Thomas     | Stoneman  |    8.0 |
| Thomas     | Stoneman  |    8.1 |
| Thomas     | Stoneman  |    7.0 |
| Thomas     | Stoneman  |    7.5 |
| Thomas     | Stoneman  |    9.5 |
| Wyatt      | Skaggs    |    7.5 |
| Wyatt      | Skaggs    |    7.6 |
| Wyatt      | Skaggs    |    9.3 |
| Wyatt      | Skaggs    |    6.5 |
| Wyatt      | Skaggs    |    8.4 |
| Wyatt      | Skaggs    |    9.1 |
| Wyatt      | Skaggs    |    7.8 |
| Wyatt      | Skaggs    |    5.5 |
| Wyatt      | Skaggs    |    8.5 |
| Kimbra     | Masters   |    8.5 |
| Kimbra     | Masters   |    8.0 |
| Kimbra     | Masters   |    7.1 |
| Kimbra     | Masters   |    7.8 |
| Kimbra     | Masters   |    9.0 |
| Kimbra     | Masters   |    7.8 |
| Kimbra     | Masters   |    6.8 |
| Kimbra     | Masters   |    8.0 |
| Kimbra     | Masters   |    8.9 |
| Domingo    | Cortes    |    7.7 |
| Domingo    | Cortes    |    6.0 |
| Domingo    | Cortes    |    8.0 |
| Domingo    | Cortes    |    8.3 |
| Domingo    | Cortes    |    9.1 |
| Domingo    | Cortes    |    8.8 |
| Domingo    | Cortes    |    8.5 |
| Domingo    | Cortes    |    5.8 |
| Domingo    | Cortes    |    7.2 |
| Domingo    | Cortes    |    8.9 |
| Colt       | Steele    |    8.9 |
| Colt       | Steele    |    9.9 |
| Colt       | Steele    |    8.0 |
| Colt       | Steele    |    8.5 |
| Colt       | Steele    |    9.9 |
| Colt       | Steele    |    9.1 |
| Colt       | Steele    |    9.7 |
| Colt       | Steele    |    9.3 |
| Colt       | Steele    |    4.5 |
| Colt       | Steele    |    9.9 |
| Pinkie     | Petit     |    8.4 |
| Pinkie     | Petit     |    7.5 |
| Pinkie     | Petit     |    8.8 |
| Pinkie     | Petit     |    4.3 |
+------------+-----------+--------+
47 rows in set (0.00 sec)

mysql> select first_name,last_name,rating from reviews reviewers on reviews.reviewer_id=reviewers.id;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'on reviews.reviewer_id=reviewers.id' at line 1
mysql> select first_name,last_name,rating from reviews join reviewers on reviews.reviewer_id=reviewers.id;
+------------+-----------+--------+
| first_name | last_name | rating |
+------------+-----------+--------+
| Thomas     | Stoneman  |    8.0 |
| Thomas     | Stoneman  |    8.1 |
| Thomas     | Stoneman  |    7.0 |
| Thomas     | Stoneman  |    7.5 |
| Thomas     | Stoneman  |    9.5 |
| Wyatt      | Skaggs    |    7.5 |
| Wyatt      | Skaggs    |    7.6 |
| Wyatt      | Skaggs    |    9.3 |
| Wyatt      | Skaggs    |    6.5 |
| Wyatt      | Skaggs    |    8.4 |
| Wyatt      | Skaggs    |    9.1 |
| Wyatt      | Skaggs    |    7.8 |
| Wyatt      | Skaggs    |    5.5 |
| Wyatt      | Skaggs    |    8.5 |
| Kimbra     | Masters   |    8.5 |
| Kimbra     | Masters   |    8.0 |
| Kimbra     | Masters   |    7.1 |
| Kimbra     | Masters   |    7.8 |
| Kimbra     | Masters   |    9.0 |
| Kimbra     | Masters   |    7.8 |
| Kimbra     | Masters   |    6.8 |
| Kimbra     | Masters   |    8.0 |
| Kimbra     | Masters   |    8.9 |
| Domingo    | Cortes    |    7.7 |
| Domingo    | Cortes    |    6.0 |
| Domingo    | Cortes    |    8.0 |
| Domingo    | Cortes    |    8.3 |
| Domingo    | Cortes    |    9.1 |
| Domingo    | Cortes    |    8.8 |
| Domingo    | Cortes    |    8.5 |
| Domingo    | Cortes    |    5.8 |
| Domingo    | Cortes    |    7.2 |
| Domingo    | Cortes    |    8.9 |
| Colt       | Steele    |    8.9 |
| Colt       | Steele    |    9.9 |
| Colt       | Steele    |    8.0 |
| Colt       | Steele    |    8.5 |
| Colt       | Steele    |    9.9 |
| Colt       | Steele    |    9.1 |
| Colt       | Steele    |    9.7 |
| Colt       | Steele    |    9.3 |
| Colt       | Steele    |    4.5 |
| Colt       | Steele    |    9.9 |
| Pinkie     | Petit     |    8.4 |
| Pinkie     | Petit     |    7.5 |
| Pinkie     | Petit     |    8.8 |
| Pinkie     | Petit     |    4.3 |
+------------+-----------+--------+
47 rows in set (0.00 sec)

mysql> select title from series where id not in (select series_id from reviews);
+-----------------------+
| title                 |
+-----------------------+
| Malcolm In The Middle |
| Pushing Daisies       |
+-----------------------+
2 rows in set (0.00 sec)

mysql> select genre, avg(rating) as avg_rating from series join reviews on series.id =series_id group by genre order by avg_rating;
+-----------+------------+
| genre     | avg_rating |
+-----------+------------+
| Animation |    7.86000 |
| Drama     |    8.04375 |
| Comedy    |    8.16250 |
+-----------+------------+
3 rows in set (0.00 sec)

mysql> select genre, avg(rating) as avg_rating from series join reviews on series.id =series_id group by genre;
+-----------+------------+
| genre     | avg_rating |
+-----------+------------+
| Animation |    7.86000 |
| Comedy    |    8.16250 |
| Drama     |    8.04375 |
+-----------+------------+
3 rows in set (0.00 sec)

mysql> select genre, round(avg(rating),2) as avg_rating from series join reviews on series.id =series_id group by genre;
+-----------+------------+
| genre     | avg_rating |
+-----------+------------+
| Animation |       7.86 |
| Comedy    |       8.16 |
| Drama     |       8.04 |
+-----------+------------+
3 rows in set (0.00 sec)

mysql> select first_name,last_name, count(*) as COUNT, IFNULL(min(*),0) as MIN, IFNULL(max(*),0) as MAX,IFNULL(avg(*),0) as AVERAGE from series join reviews on series_id=series.id;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '*),0) as MIN, IFNULL(max(*),0) as MAX,IFNULL(avg(*),0) as AVERAGE from series jo' at line 1
mysql> select first_name,last_name, count(*) as 'COUNT', IFNULL(min(*),0) as 'MIN', IFNULL(max(*),0) as 'MAX', IFNULL(avg(*),0) as 'AVERAGE' from series join reviews on series_id=series.id;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '*),0) as 'MIN', IFNULL(max(*),0) as 'MAX', IFNULL(avg(*),0) as 'AVERAGE' from se' at line 1
mysql> select first_name,last_name, count(*) as 'COUNT', min(*) as 'MIN', max(*) as 'MAX', avg(*) as 'AVERAGE' from series join reviews on series_id=series.id;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '*) as 'MIN', max(*) as 'MAX', avg(*) as 'AVERAGE' from series join reviews on se' at line 1
mysql> select first_name,last_name, count(*) as 'COUNT', min(*) as 'MIN', max(*) as 'MAX', avg(*) as 'AVERAGE' from reviewers join reviews on reviews.reviewer_id=reviewer.id group by first_name,last_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '*) as 'MIN', max(*) as 'MAX', avg(*) as 'AVERAGE' from reviewers join reviews on' at line 1
mysql> select first_name,last_name, count(*) as 'COUNT', min(rating) as 'MIN', max(rating) as 'MAX', avg(rating) as 'AVERAGE' from reviewers join reviews on reviews.reviewer_id=reviewer.id group by first_name,last_name;
ERROR 1054 (42S22): Unknown column 'reviewer.id' in 'on clause'
mysql> select first_name,last_name, count(*) as 'COUNT', min(rating) as 'MIN', max(rating) as 'MAX', avg(rating) as 'AVERAGE' from reviewers join reviews on reviews.reviewer_id=reviewers.id group by first_name,last_name;
+------------+-----------+-------+------+------+---------+
| first_name | last_name | COUNT | MIN  | MAX  | AVERAGE |
+------------+-----------+-------+------+------+---------+
| Thomas     | Stoneman  |     5 |  7.0 |  9.5 | 8.02000 |
| Wyatt      | Skaggs    |     9 |  5.5 |  9.3 | 7.80000 |
| Kimbra     | Masters   |     9 |  6.8 |  9.0 | 7.98889 |
| Domingo    | Cortes    |    10 |  5.8 |  9.1 | 7.83000 |
| Colt       | Steele    |    10 |  4.5 |  9.9 | 8.77000 |
| Pinkie     | Petit     |     4 |  4.3 |  8.8 | 7.25000 |
+------------+-----------+-------+------+------+---------+
6 rows in set (0.00 sec)

mysql> select first_name,last_name, count(*) as 'COUNT', min(rating) as 'MIN', max(rating) as 'MAX', avg(rating) as 'AVERAGE' from reviewers join reviews on reviews.reviewer_id=reviewers.id group by first_name,last_name;
```
