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

mysql> show tables;
ERROR 1046 (3D000): No database selected
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| book_shop          |
| books              |
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
11 rows in set (0.09 sec)

mysql> use books;
Database changed
mysql> show tables;
+-----------------+
| Tables_in_books |
+-----------------+
| reviewers       |
| reviews         |
| series          |
+-----------------+
3 rows in set (0.05 sec)

mysql> create view full_reviews as select title,released_year,rating,genre,first_name,last_name from reviews join series on series.id=reviews.series_id join reviewers on reviewers.id=reviews.reviewer_id;
Query OK, 0 rows affected (0.08 sec)

mysql> show tables;
+-----------------+
| Tables_in_books |
+-----------------+
| full_reviews    |
| reviewers       |
| reviews         |
| series          |
+-----------------+
4 rows in set (0.00 sec)

mysql> select * from full_reviews;
+----------------------+---------------+--------+-----------+------------+-----------+
| title                | released_year | rating | genre     | first_name | last_name |
+----------------------+---------------+--------+-----------+------------+-----------+
| Archer               |          2009 |    8.0 | Animation | Thomas     | Stoneman  |
| Arrested Development |          2003 |    8.1 | Comedy    | Thomas     | Stoneman  |
| Bob's Burgers        |          2011 |    7.0 | Animation | Thomas     | Stoneman  |
| Bojack Horseman      |          2014 |    7.5 | Animation | Thomas     | Stoneman  |
| Breaking Bad         |          2008 |    9.5 | Drama     | Thomas     | Stoneman  |
| Archer               |          2009 |    7.5 | Animation | Wyatt      | Skaggs    |
| Bojack Horseman      |          2014 |    7.6 | Animation | Wyatt      | Skaggs    |
| Breaking Bad         |          2008 |    9.3 | Drama     | Wyatt      | Skaggs    |
| Curb Your Enthusiasm |          2000 |    6.5 | Comedy    | Wyatt      | Skaggs    |
| Curb Your Enthusiasm |          2000 |    8.4 | Comedy    | Wyatt      | Skaggs    |
| Fargo                |          2014 |    9.1 | Drama     | Wyatt      | Skaggs    |
| Freaks and Geeks     |          1999 |    7.8 | Comedy    | Wyatt      | Skaggs    |
| General Hospital     |          1963 |    5.5 | Drama     | Wyatt      | Skaggs    |
| Stranger Things      |          2016 |    8.5 | Drama     | Wyatt      | Skaggs    |
| Archer               |          2009 |    8.5 | Animation | Kimbra     | Masters   |
| Arrested Development |          2003 |    8.0 | Comedy    | Kimbra     | Masters   |
| Bob's Burgers        |          2011 |    7.1 | Animation | Kimbra     | Masters   |
| Bojack Horseman      |          2014 |    7.8 | Animation | Kimbra     | Masters   |
| Breaking Bad         |          2008 |    9.0 | Drama     | Kimbra     | Masters   |
| Curb Your Enthusiasm |          2000 |    7.8 | Comedy    | Kimbra     | Masters   |
| General Hospital     |          1963 |    6.8 | Drama     | Kimbra     | Masters   |
| Seinfeld             |          1989 |    8.0 | Comedy    | Kimbra     | Masters   |
| Stranger Things      |          2016 |    8.9 | Drama     | Kimbra     | Masters   |
| Archer               |          2009 |    7.7 | Animation | Domingo    | Cortes    |
| Arrested Development |          2003 |    6.0 | Comedy    | Domingo    | Cortes    |
| Bob's Burgers        |          2011 |    8.0 | Animation | Domingo    | Cortes    |
| Bojack Horseman      |          2014 |    8.3 | Animation | Domingo    | Cortes    |
| Breaking Bad         |          2008 |    9.1 | Drama     | Domingo    | Cortes    |
| Curb Your Enthusiasm |          2000 |    8.8 | Comedy    | Domingo    | Cortes    |
| Freaks and Geeks     |          1999 |    8.5 | Comedy    | Domingo    | Cortes    |
| General Hospital     |          1963 |    5.8 | Drama     | Domingo    | Cortes    |
| Seinfeld             |          1989 |    7.2 | Comedy    | Domingo    | Cortes    |
| Stranger Things      |          2016 |    8.9 | Drama     | Domingo    | Cortes    |
| Archer               |          2009 |    8.9 | Animation | Colt       | Steele    |
| Arrested Development |          2003 |    9.9 | Comedy    | Colt       | Steele    |
| Bob's Burgers        |          2011 |    8.0 | Animation | Colt       | Steele    |
| Bojack Horseman      |          2014 |    8.5 | Animation | Colt       | Steele    |
| Breaking Bad         |          2008 |    9.9 | Drama     | Colt       | Steele    |
| Curb Your Enthusiasm |          2000 |    9.1 | Comedy    | Colt       | Steele    |
| Fargo                |          2014 |    9.7 | Drama     | Colt       | Steele    |
| Freaks and Geeks     |          1999 |    9.3 | Comedy    | Colt       | Steele    |
| General Hospital     |          1963 |    4.5 | Drama     | Colt       | Steele    |
| Halt and Catch Fire  |          2014 |    9.9 | Drama     | Colt       | Steele    |
| Arrested Development |          2003 |    8.4 | Comedy    | Pinkie     | Petit     |
| Bob's Burgers        |          2011 |    7.5 | Animation | Pinkie     | Petit     |
| Freaks and Geeks     |          1999 |    8.8 | Comedy    | Pinkie     | Petit     |
| General Hospital     |          1963 |    4.3 | Drama     | Pinkie     | Petit     |
+----------------------+---------------+--------+-----------+------------+-----------+
47 rows in set (0.01 sec)

mysql> select * from full_reviews where genre='Animation';
+-----------------+---------------+--------+-----------+------------+-----------+
| title           | released_year | rating | genre     | first_name | last_name |
+-----------------+---------------+--------+-----------+------------+-----------+
| Archer          |          2009 |    8.0 | Animation | Thomas     | Stoneman  |
| Archer          |          2009 |    7.5 | Animation | Wyatt      | Skaggs    |
| Archer          |          2009 |    8.5 | Animation | Kimbra     | Masters   |
| Archer          |          2009 |    7.7 | Animation | Domingo    | Cortes    |
| Archer          |          2009 |    8.9 | Animation | Colt       | Steele    |
| Bob's Burgers   |          2011 |    7.0 | Animation | Thomas     | Stoneman  |
| Bob's Burgers   |          2011 |    7.5 | Animation | Pinkie     | Petit     |
| Bob's Burgers   |          2011 |    8.0 | Animation | Domingo    | Cortes    |
| Bob's Burgers   |          2011 |    7.1 | Animation | Kimbra     | Masters   |
| Bob's Burgers   |          2011 |    8.0 | Animation | Colt       | Steele    |
| Bojack Horseman |          2014 |    7.5 | Animation | Thomas     | Stoneman  |
| Bojack Horseman |          2014 |    7.8 | Animation | Kimbra     | Masters   |
| Bojack Horseman |          2014 |    8.3 | Animation | Domingo    | Cortes    |
| Bojack Horseman |          2014 |    7.6 | Animation | Wyatt      | Skaggs    |
| Bojack Horseman |          2014 |    8.5 | Animation | Colt       | Steele    |
+-----------------+---------------+--------+-----------+------------+-----------+
15 rows in set (0.00 sec)

mysql> select genre,avg(rating) as rating from full_reviews group by genre;
+-----------+---------+
| genre     | rating  |
+-----------+---------+
| Animation | 7.86000 |
| Comedy    | 8.16250 |
| Drama     | 8.04375 |
+-----------+---------+
3 rows in set (0.06 sec)

mysql> create view ordered_series as select * from series order by released_year;
Query OK, 0 rows affected (0.07 sec)

mysql> select * from ordered_series;
+----+-----------------------+---------------+-----------+
| id | title                 | released_year | genre     |
+----+-----------------------+---------------+-----------+
|  9 | General Hospital      |          1963 | Drama     |
| 13 | Seinfeld              |          1989 | Comedy    |
|  8 | Freaks and Geeks      |          1999 | Comedy    |
|  6 | Curb Your Enthusiasm  |          2000 | Comedy    |
| 11 | Malcolm In The Middle |          2000 | Comedy    |
|  2 | Arrested Development  |          2003 | Comedy    |
| 12 | Pushing Daisies       |          2007 | Comedy    |
|  5 | Breaking Bad          |          2008 | Drama     |
|  1 | Archer                |          2009 | Animation |
|  3 | Bob's Burgers         |          2011 | Animation |
|  4 | Bojack Horseman       |          2014 | Animation |
|  7 | Fargo                 |          2014 | Drama     |
| 10 | Halt and Catch Fire   |          2014 | Drama     |
| 14 | Stranger Things       |          2016 | Drama     |
+----+-----------------------+---------------+-----------+
14 rows in set (0.04 sec)

mysql> insert into ordered_series values ('ans',2012,'Comedy');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into ordered_series values (15,'ans',2012,'Comedy');
Query OK, 1 row affected (0.06 sec)

mysql> select * from ordered_series;
+----+-----------------------+---------------+-----------+
| id | title                 | released_year | genre     |
+----+-----------------------+---------------+-----------+
|  9 | General Hospital      |          1963 | Drama     |
| 13 | Seinfeld              |          1989 | Comedy    |
|  8 | Freaks and Geeks      |          1999 | Comedy    |
|  6 | Curb Your Enthusiasm  |          2000 | Comedy    |
| 11 | Malcolm In The Middle |          2000 | Comedy    |
|  2 | Arrested Development  |          2003 | Comedy    |
| 12 | Pushing Daisies       |          2007 | Comedy    |
|  5 | Breaking Bad          |          2008 | Drama     |
|  1 | Archer                |          2009 | Animation |
|  3 | Bob's Burgers         |          2011 | Animation |
| 15 | ans                   |          2012 | Comedy    |
|  4 | Bojack Horseman       |          2014 | Animation |
|  7 | Fargo                 |          2014 | Drama     |
| 10 | Halt and Catch Fire   |          2014 | Drama     |
| 14 | Stranger Things       |          2016 | Drama     |
+----+-----------------------+---------------+-----------+
15 rows in set (0.00 sec)

mysql> delete from ordered_species where title=abc
    -> ;
ERROR 1146 (42S02): Table 'books.ordered_species' doesn't exist
mysql> delete from ordered_series where title=abc;
ERROR 1054 (42S22): Unknown column 'abc' in 'where clause'
mysql> delete from ordered_series where title='abc';
Query OK, 0 rows affected (0.03 sec)

mysql> select * from ordered_series;
+----+-----------------------+---------------+-----------+
| id | title                 | released_year | genre     |
+----+-----------------------+---------------+-----------+
|  9 | General Hospital      |          1963 | Drama     |
| 13 | Seinfeld              |          1989 | Comedy    |
|  8 | Freaks and Geeks      |          1999 | Comedy    |
|  6 | Curb Your Enthusiasm  |          2000 | Comedy    |
| 11 | Malcolm In The Middle |          2000 | Comedy    |
|  2 | Arrested Development  |          2003 | Comedy    |
| 12 | Pushing Daisies       |          2007 | Comedy    |
|  5 | Breaking Bad          |          2008 | Drama     |
|  1 | Archer                |          2009 | Animation |
|  3 | Bob's Burgers         |          2011 | Animation |
| 15 | ans                   |          2012 | Comedy    |
|  4 | Bojack Horseman       |          2014 | Animation |
|  7 | Fargo                 |          2014 | Drama     |
| 10 | Halt and Catch Fire   |          2014 | Drama     |
| 14 | Stranger Things       |          2016 | Drama     |
+----+-----------------------+---------------+-----------+
15 rows in set (0.00 sec)

mysql> delete from ordered_species where title is 'abc';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''abc'' at line 1
mysql> ALTER VIEW ordered_series as select * from series order by released_year desc;
Query OK, 0 rows affected (0.07 sec)

mysql> select * from ordered_series;
+----+-----------------------+---------------+-----------+
| id | title                 | released_year | genre     |
+----+-----------------------+---------------+-----------+
| 14 | Stranger Things       |          2016 | Drama     |
|  4 | Bojack Horseman       |          2014 | Animation |
|  7 | Fargo                 |          2014 | Drama     |
| 10 | Halt and Catch Fire   |          2014 | Drama     |
| 15 | ans                   |          2012 | Comedy    |
|  3 | Bob's Burgers         |          2011 | Animation |
|  1 | Archer                |          2009 | Animation |
|  5 | Breaking Bad          |          2008 | Drama     |
| 12 | Pushing Daisies       |          2007 | Comedy    |
|  2 | Arrested Development  |          2003 | Comedy    |
|  6 | Curb Your Enthusiasm  |          2000 | Comedy    |
| 11 | Malcolm In The Middle |          2000 | Comedy    |
|  8 | Freaks and Geeks      |          1999 | Comedy    |
| 13 | Seinfeld              |          1989 | Comedy    |
|  9 | General Hospital      |          1963 | Drama     |
+----+-----------------------+---------------+-----------+
15 rows in set (0.00 sec)

mysql> drop view ordered_series;
Query OK, 0 rows affected (0.05 sec)

mysql> select * from ordered_series;
ERROR 1146 (42S02): Table 'books.ordered_series' doesn't exist
mysql> select * from full_reviews
    -> ;
+----------------------+---------------+--------+-----------+------------+-----------+
| title                | released_year | rating | genre     | first_name | last_name |
+----------------------+---------------+--------+-----------+------------+-----------+
| Archer               |          2009 |    8.0 | Animation | Thomas     | Stoneman  |
| Arrested Development |          2003 |    8.1 | Comedy    | Thomas     | Stoneman  |
| Bob's Burgers        |          2011 |    7.0 | Animation | Thomas     | Stoneman  |
| Bojack Horseman      |          2014 |    7.5 | Animation | Thomas     | Stoneman  |
| Breaking Bad         |          2008 |    9.5 | Drama     | Thomas     | Stoneman  |
| Archer               |          2009 |    7.5 | Animation | Wyatt      | Skaggs    |
| Bojack Horseman      |          2014 |    7.6 | Animation | Wyatt      | Skaggs    |
| Breaking Bad         |          2008 |    9.3 | Drama     | Wyatt      | Skaggs    |
| Curb Your Enthusiasm |          2000 |    6.5 | Comedy    | Wyatt      | Skaggs    |
| Curb Your Enthusiasm |          2000 |    8.4 | Comedy    | Wyatt      | Skaggs    |
| Fargo                |          2014 |    9.1 | Drama     | Wyatt      | Skaggs    |
| Freaks and Geeks     |          1999 |    7.8 | Comedy    | Wyatt      | Skaggs    |
| General Hospital     |          1963 |    5.5 | Drama     | Wyatt      | Skaggs    |
| Stranger Things      |          2016 |    8.5 | Drama     | Wyatt      | Skaggs    |
| Archer               |          2009 |    8.5 | Animation | Kimbra     | Masters   |
| Arrested Development |          2003 |    8.0 | Comedy    | Kimbra     | Masters   |
| Bob's Burgers        |          2011 |    7.1 | Animation | Kimbra     | Masters   |
| Bojack Horseman      |          2014 |    7.8 | Animation | Kimbra     | Masters   |
| Breaking Bad         |          2008 |    9.0 | Drama     | Kimbra     | Masters   |
| Curb Your Enthusiasm |          2000 |    7.8 | Comedy    | Kimbra     | Masters   |
| General Hospital     |          1963 |    6.8 | Drama     | Kimbra     | Masters   |
| Seinfeld             |          1989 |    8.0 | Comedy    | Kimbra     | Masters   |
| Stranger Things      |          2016 |    8.9 | Drama     | Kimbra     | Masters   |
| Archer               |          2009 |    7.7 | Animation | Domingo    | Cortes    |
| Arrested Development |          2003 |    6.0 | Comedy    | Domingo    | Cortes    |
| Bob's Burgers        |          2011 |    8.0 | Animation | Domingo    | Cortes    |
| Bojack Horseman      |          2014 |    8.3 | Animation | Domingo    | Cortes    |
| Breaking Bad         |          2008 |    9.1 | Drama     | Domingo    | Cortes    |
| Curb Your Enthusiasm |          2000 |    8.8 | Comedy    | Domingo    | Cortes    |
| Freaks and Geeks     |          1999 |    8.5 | Comedy    | Domingo    | Cortes    |
| General Hospital     |          1963 |    5.8 | Drama     | Domingo    | Cortes    |
| Seinfeld             |          1989 |    7.2 | Comedy    | Domingo    | Cortes    |
| Stranger Things      |          2016 |    8.9 | Drama     | Domingo    | Cortes    |
| Archer               |          2009 |    8.9 | Animation | Colt       | Steele    |
| Arrested Development |          2003 |    9.9 | Comedy    | Colt       | Steele    |
| Bob's Burgers        |          2011 |    8.0 | Animation | Colt       | Steele    |
| Bojack Horseman      |          2014 |    8.5 | Animation | Colt       | Steele    |
| Breaking Bad         |          2008 |    9.9 | Drama     | Colt       | Steele    |
| Curb Your Enthusiasm |          2000 |    9.1 | Comedy    | Colt       | Steele    |
| Fargo                |          2014 |    9.7 | Drama     | Colt       | Steele    |
| Freaks and Geeks     |          1999 |    9.3 | Comedy    | Colt       | Steele    |
| General Hospital     |          1963 |    4.5 | Drama     | Colt       | Steele    |
| Halt and Catch Fire  |          2014 |    9.9 | Drama     | Colt       | Steele    |
| Arrested Development |          2003 |    8.4 | Comedy    | Pinkie     | Petit     |
| Bob's Burgers        |          2011 |    7.5 | Animation | Pinkie     | Petit     |
| Freaks and Geeks     |          1999 |    8.8 | Comedy    | Pinkie     | Petit     |
| General Hospital     |          1963 |    4.3 | Drama     | Pinkie     | Petit     |
+----------------------+---------------+--------+-----------+------------+-----------+
47 rows in set (0.03 sec)

mysql> show table^Z^C
mysql> select title,avg(rating),count(rating) from full_reviews group by title;
+----------------------+-------------+---------------+
| title                | avg(rating) | count(rating) |
+----------------------+-------------+---------------+
| Archer               |     8.12000 |             5 |
| Arrested Development |     8.08000 |             5 |
| Bob's Burgers        |     7.52000 |             5 |
| Bojack Horseman      |     7.94000 |             5 |
| Breaking Bad         |     9.36000 |             5 |
| Curb Your Enthusiasm |     8.12000 |             5 |
| Fargo                |     9.40000 |             2 |
| Freaks and Geeks     |     8.60000 |             4 |
| General Hospital     |     5.38000 |             5 |
| Halt and Catch Fire  |     9.90000 |             1 |
| Seinfeld             |     7.60000 |             2 |
| Stranger Things      |     8.76667 |             3 |
+----------------------+-------------+---------------+
12 rows in set (0.00 sec)

mysql> select title,avg(rating),count(rating) from full_reviews group by title having avg(rating) >5;
+----------------------+-------------+---------------+
| title                | avg(rating) | count(rating) |
+----------------------+-------------+---------------+
| Archer               |     8.12000 |             5 |
| Arrested Development |     8.08000 |             5 |
| Bob's Burgers        |     7.52000 |             5 |
| Bojack Horseman      |     7.94000 |             5 |
| Breaking Bad         |     9.36000 |             5 |
| Curb Your Enthusiasm |     8.12000 |             5 |
| Fargo                |     9.40000 |             2 |
| Freaks and Geeks     |     8.60000 |             4 |
| General Hospital     |     5.38000 |             5 |
| Halt and Catch Fire  |     9.90000 |             1 |
| Seinfeld             |     7.60000 |             2 |
| Stranger Things      |     8.76667 |             3 |
+----------------------+-------------+---------------+
12 rows in set (0.04 sec)

mysql> select title,avg(rating),count(rating) from full_reviews group by title having avg(rating) >9;
+---------------------+-------------+---------------+
| title               | avg(rating) | count(rating) |
+---------------------+-------------+---------------+
| Breaking Bad        |     9.36000 |             5 |
| Fargo               |     9.40000 |             2 |
| Halt and Catch Fire |     9.90000 |             1 |
+---------------------+-------------+---------------+
3 rows in set (0.00 sec)

mysql> select title,avg(rating) as avg,count(rating) from full_reviews group by title having avg > 9;
+---------------------+---------+---------------+
| title               | avg     | count(rating) |
+---------------------+---------+---------------+
| Breaking Bad        | 9.36000 |             5 |
| Fargo               | 9.40000 |             2 |
| Halt and Catch Fire | 9.90000 |             1 |
+---------------------+---------+---------------+
3 rows in set (0.00 sec)

mysql> select title,avg(rating) as avg,count(rating) from full_reviews group by title having avg > 9;^C
mysql>
mysql> select avg(rating) from full_reviews;
+-------------+
| avg(rating) |
+-------------+
|     8.02553 |
+-------------+
1 row in set (0.00 sec)

mysql> select avg(rating) from full_reviews group by titlr;
ERROR 1054 (42S22): Unknown column 'titlr' in 'group statement'
mysql> select avg(rating) from full_reviews group by titlr;
ERROR 1054 (42S22): Unknown column 'titlr' in 'group statement'
mysql> select avg(rating) from full_reviews group by title;
+-------------+
| avg(rating) |
+-------------+
|     8.12000 |
|     8.08000 |
|     7.52000 |
|     7.94000 |
|     9.36000 |
|     8.12000 |
|     9.40000 |
|     8.60000 |
|     5.38000 |
|     9.90000 |
|     7.60000 |
|     8.76667 |
+-------------+
12 rows in set (0.00 sec)

mysql> select title,avg(rating) from full_reviews group by title;
+----------------------+-------------+
| title                | avg(rating) |
+----------------------+-------------+
| Archer               |     8.12000 |
| Arrested Development |     8.08000 |
| Bob's Burgers        |     7.52000 |
| Bojack Horseman      |     7.94000 |
| Breaking Bad         |     9.36000 |
| Curb Your Enthusiasm |     8.12000 |
| Fargo                |     9.40000 |
| Freaks and Geeks     |     8.60000 |
| General Hospital     |     5.38000 |
| Halt and Catch Fire  |     9.90000 |
| Seinfeld             |     7.60000 |
| Stranger Things      |     8.76667 |
+----------------------+-------------+
12 rows in set (0.00 sec)

mysql> select title,avg(rating) from full_reviews group by title with roll up;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'with roll up' at line 1
mysql> select title,avg(rating) from full_reviews group by title with rollup;
+----------------------+-------------+
| title                | avg(rating) |
+----------------------+-------------+
| Archer               |     8.12000 |
| Arrested Development |     8.08000 |
| Bob's Burgers        |     7.52000 |
| Bojack Horseman      |     7.94000 |
| Breaking Bad         |     9.36000 |
| Curb Your Enthusiasm |     8.12000 |
| Fargo                |     9.40000 |
| Freaks and Geeks     |     8.60000 |
| General Hospital     |     5.38000 |
| Halt and Catch Fire  |     9.90000 |
| Seinfeld             |     7.60000 |
| Stranger Things      |     8.76667 |
| NULL                 |     8.02553 |
+----------------------+-------------+
13 rows in set (0.02 sec)

mysql> select released_year,avg(rating) from full_reviews group by released_year witho rollup;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'witho rollup' at line 1
mysql> select released_year,avg(rating) from full_reviews group by released_year with rollup;
+---------------+-------------+
| released_year | avg(rating) |
+---------------+-------------+
|          1963 |     5.38000 |
|          1989 |     7.60000 |
|          1999 |     8.60000 |
|          2000 |     8.12000 |
|          2003 |     8.08000 |
|          2008 |     9.36000 |
|          2009 |     8.12000 |
|          2011 |     7.52000 |
|          2014 |     8.55000 |
|          2016 |     8.76667 |
|          NULL |     8.02553 |
+---------------+-------------+
11 rows in set (0.02 sec)

mysql> select released_year,count(rating) from full_reviews group by released_year with rollup;
+---------------+---------------+
| released_year | count(rating) |
+---------------+---------------+
|          1963 |             5 |
|          1989 |             2 |
|          1999 |             4 |
|          2000 |             5 |
|          2003 |             5 |
|          2008 |             5 |
|          2009 |             5 |
|          2011 |             5 |
|          2014 |             8 |
|          2016 |             3 |
|          NULL |            47 |
+---------------+---------------+
11 rows in set (0.00 sec)

mysql> select released_year,genre,count(rating) from full_reviews group by released_year,genre with rollup;
+---------------+-----------+---------------+
| released_year | genre     | count(rating) |
+---------------+-----------+---------------+
|          1963 | Drama     |             5 |
|          1963 | NULL      |             5 |
|          1989 | Comedy    |             2 |
|          1989 | NULL      |             2 |
|          1999 | Comedy    |             4 |
|          1999 | NULL      |             4 |
|          2000 | Comedy    |             5 |
|          2000 | NULL      |             5 |
|          2003 | Comedy    |             5 |
|          2003 | NULL      |             5 |
|          2008 | Drama     |             5 |
|          2008 | NULL      |             5 |
|          2009 | Animation |             5 |
|          2009 | NULL      |             5 |
|          2011 | Animation |             5 |
|          2011 | NULL      |             5 |
|          2014 | Animation |             5 |
|          2014 | Drama     |             3 |
|          2014 | NULL      |             8 |
|          2016 | Drama     |             3 |
|          2016 | NULL      |             3 |
|          NULL | NULL      |            47 |
+---------------+-----------+---------------+
22 rows in set (0.00 sec)

mysql> select genre,released_year,avg(rating) from full_reviews group by genre,released_year with rollup;
+-----------+---------------+-------------+
| genre     | released_year | avg(rating) |
+-----------+---------------+-------------+
| Animation |          2009 |     8.12000 |
| Animation |          2011 |     7.52000 |
| Animation |          2014 |     7.94000 |
| Animation |          NULL |     7.86000 |
| Comedy    |          1989 |     7.60000 |
| Comedy    |          1999 |     8.60000 |
| Comedy    |          2000 |     8.12000 |
| Comedy    |          2003 |     8.08000 |
| Comedy    |          NULL |     8.16250 |
| Drama     |          1963 |     5.38000 |
| Drama     |          2008 |     9.36000 |
| Drama     |          2014 |     9.56667 |
| Drama     |          2016 |     8.76667 |
| Drama     |          NULL |     8.04375 |
| NULL      |          NULL |     8.02553 |
+-----------+---------------+-------------+
15 rows in set (0.00 sec)

mysql> select @@global.sql_mode;
+-----------------------------------------------------------------------------------------------------------------------+
| @@global.sql_mode                                                                                                     |
+-----------------------------------------------------------------------------------------------------------------------+
| ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION |
+-----------------------------------------------------------------------------------------------------------------------+
1 row in set (0.04 sec)

mysql> select @@session.sql_mode;
+-----------------------------------------------------------------------------------------------------------------------+
| @@session.sql_mode                                                                                                    |
+-----------------------------------------------------------------------------------------------------------------------+
| ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION |
+-----------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> show warnings;
Empty set (0.00 sec)

mysql> CREATE TABLE employees (
    ->     emp_no INT PRIMARY KEY AUTO_INCREMENT,
    ->     department VARCHAR(20),
    ->     salary INT
    -> );
Query OK, 0 rows affected (0.11 sec)

mysql>
mysql> INSERT INTO employees (department, salary) VALUES
    -> ('engineering', 80000),
    -> ('engineering', 69000),
    -> ('engineering', 70000),
    -> ('engineering', 103000),
    -> ('engineering', 67000),
    -> ('engineering', 89000),
    -> ('engineering', 91000),
    -> ('sales', 59000),
    -> ('sales', 70000),
    -> ('sales', 159000),
    -> ('sales', 72000),
    -> ('sales', 60000),
    -> ('sales', 61000),
    -> ('sales', 61000),
    -> ('customer service', 38000),
    -> ('customer service', 45000),
    -> ('customer service', 61000),
    -> ('customer service', 40000),
    -> ('customer service', 31000),
    -> ('customer service', 56000),
    -> ('customer service', 55000);
Query OK, 21 rows affected (0.07 sec)
Records: 21  Duplicates: 0  Warnings: 0

mysql>
mysql>
mysql> SELECT emp_no, department, salary, AVG(salary) OVER() FROM employees;
+--------+------------------+--------+--------------------+
| emp_no | department       | salary | AVG(salary) OVER() |
+--------+------------------+--------+--------------------+
|      1 | engineering      |  80000 |         68428.5714 |
|      2 | engineering      |  69000 |         68428.5714 |
|      3 | engineering      |  70000 |         68428.5714 |
|      4 | engineering      | 103000 |         68428.5714 |
|      5 | engineering      |  67000 |         68428.5714 |
|      6 | engineering      |  89000 |         68428.5714 |
|      7 | engineering      |  91000 |         68428.5714 |
|      8 | sales            |  59000 |         68428.5714 |
|      9 | sales            |  70000 |         68428.5714 |
|     10 | sales            | 159000 |         68428.5714 |
|     11 | sales            |  72000 |         68428.5714 |
|     12 | sales            |  60000 |         68428.5714 |
|     13 | sales            |  61000 |         68428.5714 |
|     14 | sales            |  61000 |         68428.5714 |
|     15 | customer service |  38000 |         68428.5714 |
|     16 | customer service |  45000 |         68428.5714 |
|     17 | customer service |  61000 |         68428.5714 |
|     18 | customer service |  40000 |         68428.5714 |
|     19 | customer service |  31000 |         68428.5714 |
|     20 | customer service |  56000 |         68428.5714 |
|     21 | customer service |  55000 |         68428.5714 |
+--------+------------------+--------+--------------------+
21 rows in set (0.01 sec)

mysql>
mysql> SELECT
    ->     emp_no,
    ->     department,
    ->     salary,
    ->     MIN(salary) OVER(),
    ->     MAX(salary) OVER()
    -> FROM employees;
+--------+------------------+--------+--------------------+--------------------+
| emp_no | department       | salary | MIN(salary) OVER() | MAX(salary) OVER() |
+--------+------------------+--------+--------------------+--------------------+
|      1 | engineering      |  80000 |              31000 |             159000 |
|      2 | engineering      |  69000 |              31000 |             159000 |
|      3 | engineering      |  70000 |              31000 |             159000 |
|      4 | engineering      | 103000 |              31000 |             159000 |
|      5 | engineering      |  67000 |              31000 |             159000 |
|      6 | engineering      |  89000 |              31000 |             159000 |
|      7 | engineering      |  91000 |              31000 |             159000 |
|      8 | sales            |  59000 |              31000 |             159000 |
|      9 | sales            |  70000 |              31000 |             159000 |
|     10 | sales            | 159000 |              31000 |             159000 |
|     11 | sales            |  72000 |              31000 |             159000 |
|     12 | sales            |  60000 |              31000 |             159000 |
|     13 | sales            |  61000 |              31000 |             159000 |
|     14 | sales            |  61000 |              31000 |             159000 |
|     15 | customer service |  38000 |              31000 |             159000 |
|     16 | customer service |  45000 |              31000 |             159000 |
|     17 | customer service |  61000 |              31000 |             159000 |
|     18 | customer service |  40000 |              31000 |             159000 |
|     19 | customer service |  31000 |              31000 |             159000 |
|     20 | customer service |  56000 |              31000 |             159000 |
|     21 | customer service |  55000 |              31000 |             159000 |
+--------+------------------+--------+--------------------+--------------------+
21 rows in set (0.00 sec)

mysql>
mysql> INSERT INTO employees (department, salary) VALUES
    -> ('engineering', 80000),
    -> ('engineering', 69000),
    -> ('engineering', 70000),
    -> ('engineering', 103000),
    -> ('engineering', 67000),
    -> ('engineering', 89000),
    -> ('engineering', 91000),
    -> ('sales', 59000),
    -> ('sales', 70000),
    -> ('sales', 159000),
    -> ('sales', 72000),
    -> ('sales', 60000),
    -> ('sales', 61000),
    -> ('sales', 61000),
    -> ('customer service', 38000),
    -> ('customer service', 45000),
    -> ('customer service', 61000),
    -> ('customer service', 40000),
    -> ('customer service', 31000),
    -> ('customer service', 56000),
    -> ('customer service', 55000);
Query OK, 21 rows affected (0.01 sec)
Records: 21  Duplicates: 0  Warnings: 0

mysql>
mysql>
mysql> SELECT emp_no, department, salary, AVG(salary) OVER() FROM employees;
+--------+------------------+--------+--------------------+
| emp_no | department       | salary | AVG(salary) OVER() |
+--------+------------------+--------+--------------------+
|      1 | engineering      |  80000 |         68428.5714 |
|      2 | engineering      |  69000 |         68428.5714 |
|      3 | engineering      |  70000 |         68428.5714 |
|      4 | engineering      | 103000 |         68428.5714 |
|      5 | engineering      |  67000 |         68428.5714 |
|      6 | engineering      |  89000 |         68428.5714 |
|      7 | engineering      |  91000 |         68428.5714 |
|      8 | sales            |  59000 |         68428.5714 |
|      9 | sales            |  70000 |         68428.5714 |
|     10 | sales            | 159000 |         68428.5714 |
|     11 | sales            |  72000 |         68428.5714 |
|     12 | sales            |  60000 |         68428.5714 |
|     13 | sales            |  61000 |         68428.5714 |
|     14 | sales            |  61000 |         68428.5714 |
|     15 | customer service |  38000 |         68428.5714 |
|     16 | customer service |  45000 |         68428.5714 |
|     17 | customer service |  61000 |         68428.5714 |
|     18 | customer service |  40000 |         68428.5714 |
|     19 | customer service |  31000 |         68428.5714 |
|     20 | customer service |  56000 |         68428.5714 |
|     21 | customer service |  55000 |         68428.5714 |
|     22 | engineering      |  80000 |         68428.5714 |
|     23 | engineering      |  69000 |         68428.5714 |
|     24 | engineering      |  70000 |         68428.5714 |
|     25 | engineering      | 103000 |         68428.5714 |
|     26 | engineering      |  67000 |         68428.5714 |
|     27 | engineering      |  89000 |         68428.5714 |
|     28 | engineering      |  91000 |         68428.5714 |
|     29 | sales            |  59000 |         68428.5714 |
|     30 | sales            |  70000 |         68428.5714 |
|     31 | sales            | 159000 |         68428.5714 |
|     32 | sales            |  72000 |         68428.5714 |
|     33 | sales            |  60000 |         68428.5714 |
|     34 | sales            |  61000 |         68428.5714 |
|     35 | sales            |  61000 |         68428.5714 |
|     36 | customer service |  38000 |         68428.5714 |
|     37 | customer service |  45000 |         68428.5714 |
|     38 | customer service |  61000 |         68428.5714 |
|     39 | customer service |  40000 |         68428.5714 |
|     40 | customer service |  31000 |         68428.5714 |
|     41 | customer service |  56000 |         68428.5714 |
|     42 | customer service |  55000 |         68428.5714 |
+--------+------------------+--------+--------------------+
42 rows in set (0.00 sec)

mysql>
mysql> SELECT
    ->     emp_no,
    ->     department,
    ->     salary,
    ->     MIN(salary) OVER(),
    ->     MAX(salary) OVER()
    -> FROM employees;
+--------+------------------+--------+--------------------+--------------------+
| emp_no | department       | salary | MIN(salary) OVER() | MAX(salary) OVER() |
+--------+------------------+--------+--------------------+--------------------+
|      1 | engineering      |  80000 |              31000 |             159000 |
|      2 | engineering      |  69000 |              31000 |             159000 |
|      3 | engineering      |  70000 |              31000 |             159000 |
|      4 | engineering      | 103000 |              31000 |             159000 |
|      5 | engineering      |  67000 |              31000 |             159000 |
|      6 | engineering      |  89000 |              31000 |             159000 |
|      7 | engineering      |  91000 |              31000 |             159000 |
|      8 | sales            |  59000 |              31000 |             159000 |
|      9 | sales            |  70000 |              31000 |             159000 |
|     10 | sales            | 159000 |              31000 |             159000 |
|     11 | sales            |  72000 |              31000 |             159000 |
|     12 | sales            |  60000 |              31000 |             159000 |
|     13 | sales            |  61000 |              31000 |             159000 |
|     14 | sales            |  61000 |              31000 |             159000 |
|     15 | customer service |  38000 |              31000 |             159000 |
|     16 | customer service |  45000 |              31000 |             159000 |
|     17 | customer service |  61000 |              31000 |             159000 |
|     18 | customer service |  40000 |              31000 |             159000 |
|     19 | customer service |  31000 |              31000 |             159000 |
|     20 | customer service |  56000 |              31000 |             159000 |
|     21 | customer service |  55000 |              31000 |             159000 |
|     22 | engineering      |  80000 |              31000 |             159000 |
|     23 | engineering      |  69000 |              31000 |             159000 |
|     24 | engineering      |  70000 |              31000 |             159000 |
|     25 | engineering      | 103000 |              31000 |             159000 |
|     26 | engineering      |  67000 |              31000 |             159000 |
|     27 | engineering      |  89000 |              31000 |             159000 |
|     28 | engineering      |  91000 |              31000 |             159000 |
|     29 | sales            |  59000 |              31000 |             159000 |
|     30 | sales            |  70000 |              31000 |             159000 |
|     31 | sales            | 159000 |              31000 |             159000 |
|     32 | sales            |  72000 |              31000 |             159000 |
|     33 | sales            |  60000 |              31000 |             159000 |
|     34 | sales            |  61000 |              31000 |             159000 |
|     35 | sales            |  61000 |              31000 |             159000 |
|     36 | customer service |  38000 |              31000 |             159000 |
|     37 | customer service |  45000 |              31000 |             159000 |
|     38 | customer service |  61000 |              31000 |             159000 |
|     39 | customer service |  40000 |              31000 |             159000 |
|     40 | customer service |  31000 |              31000 |             159000 |
|     41 | customer service |  56000 |              31000 |             159000 |
|     42 | customer service |  55000 |              31000 |             159000 |
+--------+------------------+--------+--------------------+--------------------+
42 rows in set (0.00 sec)

mysql>     select * from employees;
+--------+------------------+--------+
| emp_no | department       | salary |
+--------+------------------+--------+
|      1 | engineering      |  80000 |
|      2 | engineering      |  69000 |
|      3 | engineering      |  70000 |
|      4 | engineering      | 103000 |
|      5 | engineering      |  67000 |
|      6 | engineering      |  89000 |
|      7 | engineering      |  91000 |
|      8 | sales            |  59000 |
|      9 | sales            |  70000 |
|     10 | sales            | 159000 |
|     11 | sales            |  72000 |
|     12 | sales            |  60000 |
|     13 | sales            |  61000 |
|     14 | sales            |  61000 |
|     15 | customer service |  38000 |
|     16 | customer service |  45000 |
|     17 | customer service |  61000 |
|     18 | customer service |  40000 |
|     19 | customer service |  31000 |
|     20 | customer service |  56000 |
|     21 | customer service |  55000 |
|     22 | engineering      |  80000 |
|     23 | engineering      |  69000 |
|     24 | engineering      |  70000 |
|     25 | engineering      | 103000 |
|     26 | engineering      |  67000 |
|     27 | engineering      |  89000 |
|     28 | engineering      |  91000 |
|     29 | sales            |  59000 |
|     30 | sales            |  70000 |
|     31 | sales            | 159000 |
|     32 | sales            |  72000 |
|     33 | sales            |  60000 |
|     34 | sales            |  61000 |
|     35 | sales            |  61000 |
|     36 | customer service |  38000 |
|     37 | customer service |  45000 |
|     38 | customer service |  61000 |
|     39 | customer service |  40000 |
|     40 | customer service |  31000 |
|     41 | customer service |  56000 |
|     42 | customer service |  55000 |
+--------+------------------+--------+
42 rows in set (0.00 sec)

mysql> SELECT
    ->     emp_no, department, salary, MIN(salary), MAX(salary)
    -> FROM
    ->     employees;
ERROR 1140 (42000): In aggregated query without GROUP BY, expression #1 of SELECT list contains nonaggregated column 'books.employees.emp_no'; this is incompatible with sql_mode=only_full_group_by
mysql>
mysql>  SELECT
    ->     emp_no, department, salary, MIN(salary), MAX(salary)
    -> FROM
    ->     emp_no, department, salary, MIN(salary), MAX(salary)^C
mysql>  SELECT emp_no,department, min(salary) over(),max(salary) over() from employees;
+--------+------------------+--------------------+--------------------+
| emp_no | department       | min(salary) over() | max(salary) over() |
+--------+------------------+--------------------+--------------------+
|      1 | engineering      |              31000 |             159000 |
|      2 | engineering      |              31000 |             159000 |
|      3 | engineering      |              31000 |             159000 |
|      4 | engineering      |              31000 |             159000 |
|      5 | engineering      |              31000 |             159000 |
|      6 | engineering      |              31000 |             159000 |
|      7 | engineering      |              31000 |             159000 |
|      8 | sales            |              31000 |             159000 |
|      9 | sales            |              31000 |             159000 |
|     10 | sales            |              31000 |             159000 |
|     11 | sales            |              31000 |             159000 |
|     12 | sales            |              31000 |             159000 |
|     13 | sales            |              31000 |             159000 |
|     14 | sales            |              31000 |             159000 |
|     15 | customer service |              31000 |             159000 |
|     16 | customer service |              31000 |             159000 |
|     17 | customer service |              31000 |             159000 |
|     18 | customer service |              31000 |             159000 |
|     19 | customer service |              31000 |             159000 |
|     20 | customer service |              31000 |             159000 |
|     21 | customer service |              31000 |             159000 |
|     22 | engineering      |              31000 |             159000 |
|     23 | engineering      |              31000 |             159000 |
|     24 | engineering      |              31000 |             159000 |
|     25 | engineering      |              31000 |             159000 |
|     26 | engineering      |              31000 |             159000 |
|     27 | engineering      |              31000 |             159000 |
|     28 | engineering      |              31000 |             159000 |
|     29 | sales            |              31000 |             159000 |
|     30 | sales            |              31000 |             159000 |
|     31 | sales            |              31000 |             159000 |
|     32 | sales            |              31000 |             159000 |
|     33 | sales            |              31000 |             159000 |
|     34 | sales            |              31000 |             159000 |
|     35 | sales            |              31000 |             159000 |
|     36 | customer service |              31000 |             159000 |
|     37 | customer service |              31000 |             159000 |
|     38 | customer service |              31000 |             159000 |
|     39 | customer service |              31000 |             159000 |
|     40 | customer service |              31000 |             159000 |
|     41 | customer service |              31000 |             159000 |
|     42 | customer service |              31000 |             159000 |
+--------+------------------+--------------------+--------------------+
42 rows in set (0.00 sec)

mysql>  SELECT emp_no,department, avg(salary) over(partition by department) as dept_avg from employees;
+--------+------------------+------------+
| emp_no | department       | dept_avg   |
+--------+------------------+------------+
|     15 | customer service | 46571.4286 |
|     16 | customer service | 46571.4286 |
|     17 | customer service | 46571.4286 |
|     18 | customer service | 46571.4286 |
|     19 | customer service | 46571.4286 |
|     42 | customer service | 46571.4286 |
|     20 | customer service | 46571.4286 |
|     21 | customer service | 46571.4286 |
|     41 | customer service | 46571.4286 |
|     40 | customer service | 46571.4286 |
|     39 | customer service | 46571.4286 |
|     38 | customer service | 46571.4286 |
|     36 | customer service | 46571.4286 |
|     37 | customer service | 46571.4286 |
|      1 | engineering      | 81285.7143 |
|      2 | engineering      | 81285.7143 |
|      3 | engineering      | 81285.7143 |
|      4 | engineering      | 81285.7143 |
|      5 | engineering      | 81285.7143 |
|      7 | engineering      | 81285.7143 |
|     22 | engineering      | 81285.7143 |
|      6 | engineering      | 81285.7143 |
|     23 | engineering      | 81285.7143 |
|     24 | engineering      | 81285.7143 |
|     25 | engineering      | 81285.7143 |
|     26 | engineering      | 81285.7143 |
|     27 | engineering      | 81285.7143 |
|     28 | engineering      | 81285.7143 |
|      8 | sales            | 77428.5714 |
|     30 | sales            | 77428.5714 |
|     31 | sales            | 77428.5714 |
|     14 | sales            | 77428.5714 |
|     33 | sales            | 77428.5714 |
|     34 | sales            | 77428.5714 |
|     35 | sales            | 77428.5714 |
|     13 | sales            | 77428.5714 |
|     29 | sales            | 77428.5714 |
|     12 | sales            | 77428.5714 |
|     11 | sales            | 77428.5714 |
|     10 | sales            | 77428.5714 |
|      9 | sales            | 77428.5714 |
|     32 | sales            | 77428.5714 |
+--------+------------------+------------+
42 rows in set (0.00 sec)

mysql>  SELECT emp_no,department, salary, avg(salary) over(partition by department) as dept_avg from employees;
+--------+------------------+--------+------------+
| emp_no | department       | salary | dept_avg   |
+--------+------------------+--------+------------+
|     15 | customer service |  38000 | 46571.4286 |
|     16 | customer service |  45000 | 46571.4286 |
|     17 | customer service |  61000 | 46571.4286 |
|     18 | customer service |  40000 | 46571.4286 |
|     19 | customer service |  31000 | 46571.4286 |
|     42 | customer service |  55000 | 46571.4286 |
|     20 | customer service |  56000 | 46571.4286 |
|     21 | customer service |  55000 | 46571.4286 |
|     41 | customer service |  56000 | 46571.4286 |
|     40 | customer service |  31000 | 46571.4286 |
|     39 | customer service |  40000 | 46571.4286 |
|     38 | customer service |  61000 | 46571.4286 |
|     36 | customer service |  38000 | 46571.4286 |
|     37 | customer service |  45000 | 46571.4286 |
|      1 | engineering      |  80000 | 81285.7143 |
|      2 | engineering      |  69000 | 81285.7143 |
|      3 | engineering      |  70000 | 81285.7143 |
|      4 | engineering      | 103000 | 81285.7143 |
|      5 | engineering      |  67000 | 81285.7143 |
|      7 | engineering      |  91000 | 81285.7143 |
|     22 | engineering      |  80000 | 81285.7143 |
|      6 | engineering      |  89000 | 81285.7143 |
|     23 | engineering      |  69000 | 81285.7143 |
|     24 | engineering      |  70000 | 81285.7143 |
|     25 | engineering      | 103000 | 81285.7143 |
|     26 | engineering      |  67000 | 81285.7143 |
|     27 | engineering      |  89000 | 81285.7143 |
|     28 | engineering      |  91000 | 81285.7143 |
|      8 | sales            |  59000 | 77428.5714 |
|     30 | sales            |  70000 | 77428.5714 |
|     31 | sales            | 159000 | 77428.5714 |
|     14 | sales            |  61000 | 77428.5714 |
|     33 | sales            |  60000 | 77428.5714 |
|     34 | sales            |  61000 | 77428.5714 |
|     35 | sales            |  61000 | 77428.5714 |
|     13 | sales            |  61000 | 77428.5714 |
|     29 | sales            |  59000 | 77428.5714 |
|     12 | sales            |  60000 | 77428.5714 |
|     11 | sales            |  72000 | 77428.5714 |
|     10 | sales            | 159000 | 77428.5714 |
|      9 | sales            |  70000 | 77428.5714 |
|     32 | sales            |  72000 | 77428.5714 |
+--------+------------------+--------+------------+
42 rows in set (0.00 sec)

mysql> select * from employees;
+--------+------------------+--------+
| emp_no | department       | salary |
+--------+------------------+--------+
|      1 | engineering      |  80000 |
|      2 | engineering      |  69000 |
|      3 | engineering      |  70000 |
|      4 | engineering      | 103000 |
|      5 | engineering      |  67000 |
|      6 | engineering      |  89000 |
|      7 | engineering      |  91000 |
|      8 | sales            |  59000 |
|      9 | sales            |  70000 |
|     10 | sales            | 159000 |
|     11 | sales            |  72000 |
|     12 | sales            |  60000 |
|     13 | sales            |  61000 |
|     14 | sales            |  61000 |
|     15 | customer service |  38000 |
|     16 | customer service |  45000 |
|     17 | customer service |  61000 |
|     18 | customer service |  40000 |
|     19 | customer service |  31000 |
|     20 | customer service |  56000 |
|     21 | customer service |  55000 |
|     22 | engineering      |  80000 |
|     23 | engineering      |  69000 |
|     24 | engineering      |  70000 |
|     25 | engineering      | 103000 |
|     26 | engineering      |  67000 |
|     27 | engineering      |  89000 |
|     28 | engineering      |  91000 |
|     29 | sales            |  59000 |
|     30 | sales            |  70000 |
|     31 | sales            | 159000 |
|     32 | sales            |  72000 |
|     33 | sales            |  60000 |
|     34 | sales            |  61000 |
|     35 | sales            |  61000 |
|     36 | customer service |  38000 |
|     37 | customer service |  45000 |
|     38 | customer service |  61000 |
|     39 | customer service |  40000 |
|     40 | customer service |  31000 |
|     41 | customer service |  56000 |
|     42 | customer service |  55000 |
+--------+------------------+--------+
42 rows in set (0.00 sec)

mysql> select department,salary,sum(salary) over(partition by department) from employees;
+------------------+--------+-------------------------------------------+
| department       | salary | sum(salary) over(partition by department) |
+------------------+--------+-------------------------------------------+
| customer service |  38000 |                                    652000 |
| customer service |  45000 |                                    652000 |
| customer service |  61000 |                                    652000 |
| customer service |  40000 |                                    652000 |
| customer service |  31000 |                                    652000 |
| customer service |  55000 |                                    652000 |
| customer service |  56000 |                                    652000 |
| customer service |  55000 |                                    652000 |
| customer service |  56000 |                                    652000 |
| customer service |  31000 |                                    652000 |
| customer service |  40000 |                                    652000 |
| customer service |  61000 |                                    652000 |
| customer service |  38000 |                                    652000 |
| customer service |  45000 |                                    652000 |
| engineering      |  80000 |                                   1138000 |
| engineering      |  69000 |                                   1138000 |
| engineering      |  70000 |                                   1138000 |
| engineering      | 103000 |                                   1138000 |
| engineering      |  67000 |                                   1138000 |
| engineering      |  91000 |                                   1138000 |
| engineering      |  80000 |                                   1138000 |
| engineering      |  89000 |                                   1138000 |
| engineering      |  69000 |                                   1138000 |
| engineering      |  70000 |                                   1138000 |
| engineering      | 103000 |                                   1138000 |
| engineering      |  67000 |                                   1138000 |
| engineering      |  89000 |                                   1138000 |
| engineering      |  91000 |                                   1138000 |
| sales            |  59000 |                                   1084000 |
| sales            |  70000 |                                   1084000 |
| sales            | 159000 |                                   1084000 |
| sales            |  61000 |                                   1084000 |
| sales            |  60000 |                                   1084000 |
| sales            |  61000 |                                   1084000 |
| sales            |  61000 |                                   1084000 |
| sales            |  61000 |                                   1084000 |
| sales            |  59000 |                                   1084000 |
| sales            |  60000 |                                   1084000 |
| sales            |  72000 |                                   1084000 |
| sales            | 159000 |                                   1084000 |
| sales            |  70000 |                                   1084000 |
| sales            |  72000 |                                   1084000 |
+------------------+--------+-------------------------------------------+
42 rows in set (0.00 sec)

mysql> select department,salary,sum(salary) over(partition by department order by salary) from employees;
+------------------+--------+-----------------------------------------------------------+
| department       | salary | sum(salary) over(partition by department order by salary) |
+------------------+--------+-----------------------------------------------------------+
| customer service |  31000 |                                                     62000 |
| customer service |  31000 |                                                     62000 |
| customer service |  38000 |                                                    138000 |
| customer service |  38000 |                                                    138000 |
| customer service |  40000 |                                                    218000 |
| customer service |  40000 |                                                    218000 |
| customer service |  45000 |                                                    308000 |
| customer service |  45000 |                                                    308000 |
| customer service |  55000 |                                                    418000 |
| customer service |  55000 |                                                    418000 |
| customer service |  56000 |                                                    530000 |
| customer service |  56000 |                                                    530000 |
| customer service |  61000 |                                                    652000 |
| customer service |  61000 |                                                    652000 |
| engineering      |  67000 |                                                    134000 |
| engineering      |  67000 |                                                    134000 |
| engineering      |  69000 |                                                    272000 |
| engineering      |  69000 |                                                    272000 |
| engineering      |  70000 |                                                    412000 |
| engineering      |  70000 |                                                    412000 |
| engineering      |  80000 |                                                    572000 |
| engineering      |  80000 |                                                    572000 |
| engineering      |  89000 |                                                    750000 |
| engineering      |  89000 |                                                    750000 |
| engineering      |  91000 |                                                    932000 |
| engineering      |  91000 |                                                    932000 |
| engineering      | 103000 |                                                   1138000 |
| engineering      | 103000 |                                                   1138000 |
| sales            |  59000 |                                                    118000 |
| sales            |  59000 |                                                    118000 |
| sales            |  60000 |                                                    238000 |
| sales            |  60000 |                                                    238000 |
| sales            |  61000 |                                                    482000 |
| sales            |  61000 |                                                    482000 |
| sales            |  61000 |                                                    482000 |
| sales            |  61000 |                                                    482000 |
| sales            |  70000 |                                                    622000 |
| sales            |  70000 |                                                    622000 |
| sales            |  72000 |                                                    766000 |
| sales            |  72000 |                                                    766000 |
| sales            | 159000 |                                                   1084000 |
| sales            | 159000 |                                                   1084000 |
+------------------+--------+-----------------------------------------------------------+
42 rows in set (0.05 sec)

mysql> select department,salary,sum(salary) over(partition by department order by salary) as roll_salary from employees;
+------------------+--------+-------------+
| department       | salary | roll_salary |
+------------------+--------+-------------+
| customer service |  31000 |       62000 |
| customer service |  31000 |       62000 |
| customer service |  38000 |      138000 |
| customer service |  38000 |      138000 |
| customer service |  40000 |      218000 |
| customer service |  40000 |      218000 |
| customer service |  45000 |      308000 |
| customer service |  45000 |      308000 |
| customer service |  55000 |      418000 |
| customer service |  55000 |      418000 |
| customer service |  56000 |      530000 |
| customer service |  56000 |      530000 |
| customer service |  61000 |      652000 |
| customer service |  61000 |      652000 |
| engineering      |  67000 |      134000 |
| engineering      |  67000 |      134000 |
| engineering      |  69000 |      272000 |
| engineering      |  69000 |      272000 |
| engineering      |  70000 |      412000 |
| engineering      |  70000 |      412000 |
| engineering      |  80000 |      572000 |
| engineering      |  80000 |      572000 |
| engineering      |  89000 |      750000 |
| engineering      |  89000 |      750000 |
| engineering      |  91000 |      932000 |
| engineering      |  91000 |      932000 |
| engineering      | 103000 |     1138000 |
| engineering      | 103000 |     1138000 |
| sales            |  59000 |      118000 |
| sales            |  59000 |      118000 |
| sales            |  60000 |      238000 |
| sales            |  60000 |      238000 |
| sales            |  61000 |      482000 |
| sales            |  61000 |      482000 |
| sales            |  61000 |      482000 |
| sales            |  61000 |      482000 |
| sales            |  70000 |      622000 |
| sales            |  70000 |      622000 |
| sales            |  72000 |      766000 |
| sales            |  72000 |      766000 |
| sales            | 159000 |     1084000 |
| sales            | 159000 |     1084000 |
+------------------+--------+-------------+
42 rows in set (0.00 sec)

mysql> select department,salary,rank() sum(salary) over(partition by department order by salary) as roll_salary from employees order by department;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'sum(salary) over(partition by department order by salary) as roll_salary from em' at line 1
mysql> select department,salary,rank() over(partition by department order by salary) as roll_salary from employees order by department;
+------------------+--------+-------------+
| department       | salary | roll_salary |
+------------------+--------+-------------+
| customer service |  31000 |           1 |
| customer service |  31000 |           1 |
| customer service |  38000 |           3 |
| customer service |  38000 |           3 |
| customer service |  40000 |           5 |
| customer service |  40000 |           5 |
| customer service |  45000 |           7 |
| customer service |  45000 |           7 |
| customer service |  55000 |           9 |
| customer service |  55000 |           9 |
| customer service |  56000 |          11 |
| customer service |  56000 |          11 |
| customer service |  61000 |          13 |
| customer service |  61000 |          13 |
| engineering      |  67000 |           1 |
| engineering      |  67000 |           1 |
| engineering      |  69000 |           3 |
| engineering      |  69000 |           3 |
| engineering      |  70000 |           5 |
| engineering      |  70000 |           5 |
| engineering      |  80000 |           7 |
| engineering      |  80000 |           7 |
| engineering      |  89000 |           9 |
| engineering      |  89000 |           9 |
| engineering      |  91000 |          11 |
| engineering      |  91000 |          11 |
| engineering      | 103000 |          13 |
| engineering      | 103000 |          13 |
| sales            |  59000 |           1 |
| sales            |  59000 |           1 |
| sales            |  60000 |           3 |
| sales            |  60000 |           3 |
| sales            |  61000 |           5 |
| sales            |  61000 |           5 |
| sales            |  61000 |           5 |
| sales            |  61000 |           5 |
| sales            |  70000 |           9 |
| sales            |  70000 |           9 |
| sales            |  72000 |          11 |
| sales            |  72000 |          11 |
| sales            | 159000 |          13 |
| sales            | 159000 |          13 |
+------------------+--------+-------------+
42 rows in set (0.04 sec)

mysql> select * from employees;
+--------+------------------+--------+
| emp_no | department       | salary |
+--------+------------------+--------+
|      1 | engineering      |  80000 |
|      2 | engineering      |  69000 |
|      3 | engineering      |  70000 |
|      4 | engineering      | 103000 |
|      5 | engineering      |  67000 |
|      6 | engineering      |  89000 |
|      7 | engineering      |  91000 |
|      8 | sales            |  59000 |
|      9 | sales            |  70000 |
|     10 | sales            | 159000 |
|     11 | sales            |  72000 |
|     12 | sales            |  60000 |
|     13 | sales            |  61000 |
|     14 | sales            |  61000 |
|     15 | customer service |  38000 |
|     16 | customer service |  45000 |
|     17 | customer service |  61000 |
|     18 | customer service |  40000 |
|     19 | customer service |  31000 |
|     20 | customer service |  56000 |
|     21 | customer service |  55000 |
|     22 | engineering      |  80000 |
|     23 | engineering      |  69000 |
|     24 | engineering      |  70000 |
|     25 | engineering      | 103000 |
|     26 | engineering      |  67000 |
|     27 | engineering      |  89000 |
|     28 | engineering      |  91000 |
|     29 | sales            |  59000 |
|     30 | sales            |  70000 |
|     31 | sales            | 159000 |
|     32 | sales            |  72000 |
|     33 | sales            |  60000 |
|     34 | sales            |  61000 |
|     35 | sales            |  61000 |
|     36 | customer service |  38000 |
|     37 | customer service |  45000 |
|     38 | customer service |  61000 |
|     39 | customer service |  40000 |
|     40 | customer service |  31000 |
|     41 | customer service |  56000 |
|     42 | customer service |  55000 |
+--------+------------------+--------+
42 rows in set (0.00 sec)

mysql>
```
