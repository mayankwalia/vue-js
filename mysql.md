```sql

SELECT * FROM orders;
SELECT * 
FROM products
ORDER BY Price DESC;
SELECT 
    customerName,
    COUNT(*) AS 'number of orders'
FROM customers
INNER JOIN orders
	ON orders.CustomerID = customers.CustomerID
GROUP BY customers.customerID
ORDER BY "number of orders" DESC;

SELECT 
    username,
    photos.id,
    photos.image_url, 
    COUNT(*) AS total
FROM photos
INNER JOIN likes
    ON likes.photo_id = photos.id
INNER JOIN users
    ON photos.user_id = users.id
GROUP BY photos.id
ORDER BY total DESC
LIMIT 1;

SELECT first_name, 
       last_name, 
       Count(rating)                    AS COUNT, 
       Ifnull(Min(rating), 0)           AS MIN, 
       Ifnull(Max(rating), 0)           AS MAX, 
       Round(Ifnull(Avg(rating), 0), 2) AS AVG, 
       CASE 
         WHEN Count(rating) >= 10 THEN 'POWER USER' 
         WHEN Count(rating) > 0 THEN 'ACTIVE' 
         ELSE 'INACTIVE' 
       end                              AS STATUS 
FROM   reviewers 
       LEFT JOIN reviews 
              ON reviewers.id = reviews.reviewer_id 
GROUP  BY reviewers.id; 

DROP TABLE customers;


mysql> select lower('sADDSd');
+-----------------+
| lower('sADDSd') |
+-----------------+
| saddsd          |
+-----------------+
1 row in set (0.00 sec)

mysql> select lcase('sADDSd');
+-----------------+
| lcase('sADDSd') |
+-----------------+
| saddsd          |
+-----------------+
1 row in set (0.05 sec)

mysql> select ucase('sADDSd');
+-----------------+
| ucase('sADDSd') |
+-----------------+
| SADDSD          |
+-----------------+
1 row in set (0.05 sec)

mysql> select upper('sADDSd');
+-----------------+
| upper('sADDSd') |
+-----------------+
| SADDSD          |
+-----------------+
1 row in set (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| book_shop          |
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| tea_shop           |
| test               |
| world              |
+--------------------+
9 rows in set (0.05 sec)

mysql> use book_shop;
Database changed
mysql> select DATABASE();
+------------+
| DATABASE() |
+------------+
| book_shop  |
+------------+
1 row in set (0.00 sec)

mysql> show tables;
+---------------------+
| Tables_in_book_shop |
+---------------------+
| books               |
+---------------------+
1 row in set (0.04 sec)

mysql> select * from books;
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
| book_id | title                                               | author_fname | author_lname   | released_year | stock_quantity | pages |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
|       1 | The Namesake                                        | Jhumpa       | Lahiri         |          2003 |             32 |   291 |
|       2 | Norse Mythology                                     | Neil         | Gaiman         |          2016 |             43 |   304 |
|       3 | American Gods                                       | Neil         | Gaiman         |          2001 |             12 |   465 |
|       4 | Interpreter of Maladies                             | Jhumpa       | Lahiri         |          1996 |             97 |   198 |
|       5 | A Hologram for the King: A Novel                    | Dave         | Eggers         |          2012 |            154 |   352 |
|       6 | The Circle                                          | Dave         | Eggers         |          2013 |             26 |   504 |
|       7 | The Amazing Adventures of Kavalier & Clay           | Michael      | Chabon         |          2000 |             68 |   634 |
|       8 | Just Kids                                           | Patti        | Smith          |          2010 |             55 |   304 |
|       9 | A Heartbreaking Work of Staggering Genius           | Dave         | Eggers         |          2001 |            104 |   437 |
|      10 | Coraline                                            | Neil         | Gaiman         |          2003 |            100 |   208 |
|      11 | What We Talk About When We Talk About Love: Stories | Raymond      | Carver         |          1981 |             23 |   176 |
|      12 | Where I'm Calling From: Selected Stories            | Raymond      | Carver         |          1989 |             12 |   526 |
|      13 | White Noise                                         | Don          | DeLillo        |          1985 |             49 |   320 |
|      14 | Cannery Row                                         | John         | Steinbeck      |          1945 |             95 |   181 |
|      15 | Oblivion: Stories                                   | David        | Foster Wallace |          2004 |            172 |   329 |
|      16 | Consider the Lobster                                | David        | Foster Wallace |          2005 |             92 |   343 |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
16 rows in set (0.03 sec)

mysql> select ucase(title) as title from books;
+-----------------------------------------------------+
| title                                               |
+-----------------------------------------------------+
| THE NAMESAKE                                        |
| NORSE MYTHOLOGY                                     |
| AMERICAN GODS                                       |
| INTERPRETER OF MALADIES                             |
| A HOLOGRAM FOR THE KING: A NOVEL                    |
| THE CIRCLE                                          |
| THE AMAZING ADVENTURES OF KAVALIER & CLAY           |
| JUST KIDS                                           |
| A HEARTBREAKING WORK OF STAGGERING GENIUS           |
| CORALINE                                            |
| WHAT WE TALK ABOUT WHEN WE TALK ABOUT LOVE: STORIES |
| WHERE I'M CALLING FROM: SELECTED STORIES            |
| WHITE NOISE                                         |
| CANNERY ROW                                         |
| OBLIVION: STORIES                                   |
| CONSIDER THE LOBSTER                                |
+-----------------------------------------------------+
16 rows in set (0.00 sec)

mysql> select concat('I Love ',ucase(title),' !!!') as title from books;
+----------------------------------------------------------------+
| title                                                          |
+----------------------------------------------------------------+
| I Love THE NAMESAKE !!!                                        |
| I Love NORSE MYTHOLOGY !!!                                     |
| I Love AMERICAN GODS !!!                                       |
| I Love INTERPRETER OF MALADIES !!!                             |
| I Love A HOLOGRAM FOR THE KING: A NOVEL !!!                    |
| I Love THE CIRCLE !!!                                          |
| I Love THE AMAZING ADVENTURES OF KAVALIER & CLAY !!!           |
| I Love JUST KIDS !!!                                           |
| I Love A HEARTBREAKING WORK OF STAGGERING GENIUS !!!           |
| I Love CORALINE !!!                                            |
| I Love WHAT WE TALK ABOUT WHEN WE TALK ABOUT LOVE: STORIES !!! |
| I Love WHERE I'M CALLING FROM: SELECTED STORIES !!!            |
| I Love WHITE NOISE !!!                                         |
| I Love CANNERY ROW !!!                                         |
| I Love OBLIVION: STORIES !!!                                   |
| I Love CONSIDER THE LOBSTER !!!                                |
+----------------------------------------------------------------+
16 rows in set (0.00 sec)

mysql> select concat('I Love ',UPPER(title),' !!!') as title from books;
+----------------------------------------------------------------+
| title                                                          |
+----------------------------------------------------------------+
| I Love THE NAMESAKE !!!                                        |
| I Love NORSE MYTHOLOGY !!!                                     |
| I Love AMERICAN GODS !!!                                       |
| I Love INTERPRETER OF MALADIES !!!                             |
| I Love A HOLOGRAM FOR THE KING: A NOVEL !!!                    |
| I Love THE CIRCLE !!!                                          |
| I Love THE AMAZING ADVENTURES OF KAVALIER & CLAY !!!           |
| I Love JUST KIDS !!!                                           |
| I Love A HEARTBREAKING WORK OF STAGGERING GENIUS !!!           |
| I Love CORALINE !!!                                            |
| I Love WHAT WE TALK ABOUT WHEN WE TALK ABOUT LOVE: STORIES !!! |
| I Love WHERE I'M CALLING FROM: SELECTED STORIES !!!            |
| I Love WHITE NOISE !!!                                         |
| I Love CANNERY ROW !!!                                         |
| I Love OBLIVION: STORIES !!!                                   |
| I Love CONSIDER THE LOBSTER !!!                                |
+----------------------------------------------------------------+
16 rows in set (0.00 sec)

mysql> select left(title,3) from books;
+---------------+
| left(title,3) |
+---------------+
| The           |
| Nor           |
| Ame           |
| Int           |
| A H           |
| The           |
| The           |
| Jus           |
| A H           |
| Cor           |
| Wha           |
| Whe           |
| Whi           |
| Can           |
| Obl           |
| Con           |
+---------------+
16 rows in set (0.02 sec)

mysql> select right(title,3) from books;
+----------------+
| right(title,3) |
+----------------+
| ake            |
| ogy            |
| ods            |
| ies            |
| vel            |
| cle            |
| lay            |
| ids            |
| ius            |
| ine            |
| ies            |
| ies            |
| ise            |
| Row            |
| ies            |
| ter            |
+----------------+
16 rows in set (0.00 sec)

mysql> select TRIM(' dsde   ');
+------------------+
| TRIM(' dsde   ') |
+------------------+
| dsde             |
+------------------+
1 row in set (0.04 sec)

mysql> select REPEAT(' dsde   ',3);
+--------------------------+
| REPEAT(' dsde   ',3)     |
+--------------------------+
|  dsde    dsde    dsde    |
+--------------------------+
1 row in set (0.00 sec)

mysql> select trim(LEADING '.' FROM '......leading.......');
+-----------------------------------------------+
| trim(LEADING '.' FROM '......leading.......') |
+-----------------------------------------------+
| leading.......                                |
+-----------------------------------------------+
1 row in set (0.00 sec)

mysql> select trim('.' FROM '......leading.......');
+---------------------------------------+
| trim('.' FROM '......leading.......') |
+---------------------------------------+
| leading                               |
+---------------------------------------+
1 row in set (0.00 sec)

mysql> select trim(TRAILING '.' FROM '......leading.......');
+------------------------------------------------+
| trim(TRAILING '.' FROM '......leading.......') |
+------------------------------------------------+
| ......leading                                  |
+------------------------------------------------+
1 row in set (0.00 sec)

mysql> select REVERSE(UPPER('Why does my cat look at me with such hatred');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> select REVERSE(UPPER('Why does my cat look at me with such hatred'));
+---------------------------------------------------------------+
| REVERSE(UPPER('Why does my cat look at me with such hatred')) |
+---------------------------------------------------------------+
| DERTAH HCUS HTIW EM TA KOOL TAC YM SEOD YHW                   |
+---------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> select REVERSE(UCASE('Why does my cat look at me with such hatred'));
+---------------------------------------------------------------+
| REVERSE(UCASE('Why does my cat look at me with such hatred')) |
+---------------------------------------------------------------+
| DERTAH HCUS HTIW EM TA KOOL TAC YM SEOD YHW                   |
+---------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> select UCASE(REVERSE('Why does my cat look at me with such hatred'));
+---------------------------------------------------------------+
| UCASE(REVERSE('Why does my cat look at me with such hatred')) |
+---------------------------------------------------------------+
| DERTAH HCUS HTIW EM TA KOOL TAC YM SEOD YHW                   |
+---------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> select UPPERE(REVERSE('Why does my cat look at me with such hatred'));
ERROR 1305 (42000): FUNCTION book_shop.UPPERE does not exist
mysql> select UPPER(REVERSE('Why does my cat look at me with such hatred'));
+---------------------------------------------------------------+
| UPPER(REVERSE('Why does my cat look at me with such hatred')) |
+---------------------------------------------------------------+
| DERTAH HCUS HTIW EM TA KOOL TAC YM SEOD YHW                   |
+---------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> select replace(title,' ','->') as title from books;
+--------------------------------------------------------------+
| title                                                        |
+--------------------------------------------------------------+
| The->Namesake                                                |
| Norse->Mythology                                             |
| American->Gods                                               |
| Interpreter->of->Maladies                                    |
| A->Hologram->for->the->King:->A->Novel                       |
| The->Circle                                                  |
| The->Amazing->Adventures->of->Kavalier->&->Clay              |
| Just->Kids                                                   |
| A->Heartbreaking->Work->of->Staggering->Genius               |
| Coraline                                                     |
| What->We->Talk->About->When->We->Talk->About->Love:->Stories |
| Where->I'm->Calling->From:->Selected->Stories                |
| White->Noise                                                 |
| Cannery->Row                                                 |
| Oblivion:->Stories                                           |
| Consider->the->Lobster                                       |
+--------------------------------------------------------------+
16 rows in set (0.00 sec)

mysql> select * from books
    -> ;
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
| book_id | title                                               | author_fname | author_lname   | released_year | stock_quantity | pages |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
|       1 | The Namesake                                        | Jhumpa       | Lahiri         |          2003 |             32 |   291 |
|       2 | Norse Mythology                                     | Neil         | Gaiman         |          2016 |             43 |   304 |
|       3 | American Gods                                       | Neil         | Gaiman         |          2001 |             12 |   465 |
|       4 | Interpreter of Maladies                             | Jhumpa       | Lahiri         |          1996 |             97 |   198 |
|       5 | A Hologram for the King: A Novel                    | Dave         | Eggers         |          2012 |            154 |   352 |
|       6 | The Circle                                          | Dave         | Eggers         |          2013 |             26 |   504 |
|       7 | The Amazing Adventures of Kavalier & Clay           | Michael      | Chabon         |          2000 |             68 |   634 |
|       8 | Just Kids                                           | Patti        | Smith          |          2010 |             55 |   304 |
|       9 | A Heartbreaking Work of Staggering Genius           | Dave         | Eggers         |          2001 |            104 |   437 |
|      10 | Coraline                                            | Neil         | Gaiman         |          2003 |            100 |   208 |
|      11 | What We Talk About When We Talk About Love: Stories | Raymond      | Carver         |          1981 |             23 |   176 |
|      12 | Where I'm Calling From: Selected Stories            | Raymond      | Carver         |          1989 |             12 |   526 |
|      13 | White Noise                                         | Don          | DeLillo        |          1985 |             49 |   320 |
|      14 | Cannery Row                                         | John         | Steinbeck      |          1945 |             95 |   181 |
|      15 | Oblivion: Stories                                   | David        | Foster Wallace |          2004 |            172 |   329 |
|      16 | Consider the Lobster                                | David        | Foster Wallace |          2005 |             92 |   343 |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
16 rows in set (0.00 sec)

mysql> select author_lname as forwards,reverse(author_lname) as backwards from books;
+----------------+----------------+
| forwards       | backwards      |
+----------------+----------------+
| Lahiri         | irihaL         |
| Gaiman         | namiaG         |
| Gaiman         | namiaG         |
| Lahiri         | irihaL         |
| Eggers         | sreggE         |
| Eggers         | sreggE         |
| Chabon         | nobahC         |
| Smith          | htimS          |
| Eggers         | sreggE         |
| Gaiman         | namiaG         |
| Carver         | revraC         |
| Carver         | revraC         |
| DeLillo        | olliLeD        |
| Steinbeck      | kcebnietS      |
| Foster Wallace | ecallaW retsoF |
| Foster Wallace | ecallaW retsoF |
+----------------+----------------+
16 rows in set (0.00 sec)

mysql> select upper(concat(author_fname,' ',author_lname)) from books;
+----------------------------------------------+
| upper(concat(author_fname,' ',author_lname)) |
+----------------------------------------------+
| JHUMPA LAHIRI                                |
| NEIL GAIMAN                                  |
| NEIL GAIMAN                                  |
| JHUMPA LAHIRI                                |
| DAVE EGGERS                                  |
| DAVE EGGERS                                  |
| MICHAEL CHABON                               |
| PATTI SMITH                                  |
| DAVE EGGERS                                  |
| NEIL GAIMAN                                  |
| RAYMOND CARVER                               |
| RAYMOND CARVER                               |
| DON DELILLO                                  |
| JOHN STEINBECK                               |
| DAVID FOSTER WALLACE                         |
| DAVID FOSTER WALLACE                         |
+----------------------------------------------+
16 rows in set (0.00 sec)

mysql> select concat(upper(author_fname),' ',upper(author_lname)) from books;
+-----------------------------------------------------+
| concat(upper(author_fname),' ',upper(author_lname)) |
+-----------------------------------------------------+
| JHUMPA LAHIRI                                       |
| NEIL GAIMAN                                         |
| NEIL GAIMAN                                         |
| JHUMPA LAHIRI                                       |
| DAVE EGGERS                                         |
| DAVE EGGERS                                         |
| MICHAEL CHABON                                      |
| PATTI SMITH                                         |
| DAVE EGGERS                                         |
| NEIL GAIMAN                                         |
| RAYMOND CARVER                                      |
| RAYMOND CARVER                                      |
| DON DELILLO                                         |
| JOHN STEINBECK                                      |
| DAVID FOSTER WALLACE                                |
| DAVID FOSTER WALLACE                                |
+-----------------------------------------------------+
16 rows in set (0.00 sec)

mysql> select concat(upper(author_fname),' ',upper(author_lname)) as 'full name in caps' from books;
+----------------------+
| full name in caps    |
+----------------------+
| JHUMPA LAHIRI        |
| NEIL GAIMAN          |
| NEIL GAIMAN          |
| JHUMPA LAHIRI        |
| DAVE EGGERS          |
| DAVE EGGERS          |
| MICHAEL CHABON       |
| PATTI SMITH          |
| DAVE EGGERS          |
| NEIL GAIMAN          |
| RAYMOND CARVER       |
| RAYMOND CARVER       |
| DON DELILLO          |
| JOHN STEINBECK       |
| DAVID FOSTER WALLACE |
| DAVID FOSTER WALLACE |
+----------------------+
16 rows in set (0.00 sec)

mysql> select concat(title, ' was released in ',release_year) as blurb from books
    -> select concat(title, ' was released in ',release_year) as blurb from books;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'select concat(title, ' was released in ',release_year) as blurb from books' at line 2
mysql> select concat(title, ' was released in ',released_year) as blurb from books;
+--------------------------------------------------------------------------+
| blurb                                                                    |
+--------------------------------------------------------------------------+
| The Namesake was released in 2003                                        |
| Norse Mythology was released in 2016                                     |
| American Gods was released in 2001                                       |
| Interpreter of Maladies was released in 1996                             |
| A Hologram for the King: A Novel was released in 2012                    |
| The Circle was released in 2013                                          |
| The Amazing Adventures of Kavalier & Clay was released in 2000           |
| Just Kids was released in 2010                                           |
| A Heartbreaking Work of Staggering Genius was released in 2001           |
| Coraline was released in 2003                                            |
| What We Talk About When We Talk About Love: Stories was released in 1981 |
| Where I'm Calling From: Selected Stories was released in 1989            |
| White Noise was released in 1985                                         |
| Cannery Row was released in 1945                                         |
| Oblivion: Stories was released in 2004                                   |
| Consider the Lobster was released in 2005                                |
+--------------------------------------------------------------------------+
16 rows in set (0.00 sec)

mysql>
mysql>
mysql> select title,char_length(title) as character count from books;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'character count from books' at line 1
mysql> select title,char_length(title) as 'character count' from books;
+-----------------------------------------------------+-----------------+
| title                                               | character count |
+-----------------------------------------------------+-----------------+
| The Namesake                                        |              12 |
| Norse Mythology                                     |              15 |
| American Gods                                       |              13 |
| Interpreter of Maladies                             |              23 |
| A Hologram for the King: A Novel                    |              32 |
| The Circle                                          |              10 |
| The Amazing Adventures of Kavalier & Clay           |              41 |
| Just Kids                                           |               9 |
| A Heartbreaking Work of Staggering Genius           |              41 |
| Coraline                                            |               8 |
| What We Talk About When We Talk About Love: Stories |              51 |
| Where I'm Calling From: Selected Stories            |              40 |
| White Noise                                         |              11 |
| Cannery Row                                         |              11 |
| Oblivion: Stories                                   |              17 |
| Consider the Lobster                                |              20 |
+-----------------------------------------------------+-----------------+
16 rows in set (0.05 sec)

mysql> select title,length(title) as 'character count' from books;
+-----------------------------------------------------+-----------------+
| title                                               | character count |
+-----------------------------------------------------+-----------------+
| The Namesake                                        |              12 |
| Norse Mythology                                     |              15 |
| American Gods                                       |              13 |
| Interpreter of Maladies                             |              23 |
| A Hologram for the King: A Novel                    |              32 |
| The Circle                                          |              10 |
| The Amazing Adventures of Kavalier & Clay           |              41 |
| Just Kids                                           |               9 |
| A Heartbreaking Work of Staggering Genius           |              41 |
| Coraline                                            |               8 |
| What We Talk About When We Talk About Love: Stories |              51 |
| Where I'm Calling From: Selected Stories            |              40 |
| White Noise                                         |              11 |
| Cannery Row                                         |              11 |
| Oblivion: Stories                                   |              17 |
| Consider the Lobster                                |              20 |
+-----------------------------------------------------+-----------------+
16 rows in set (0.00 sec)

mysql> select concat(substr(title,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, quantity from books;
ERROR 1054 (42S22): Unknown column 'quantity' in 'field list'
mysql> desc books;
+----------------+--------------+------+-----+---------+----------------+
| Field          | Type         | Null | Key | Default | Extra          |
+----------------+--------------+------+-----+---------+----------------+
| book_id        | int          | NO   | PRI | NULL    | auto_increment |
| title          | varchar(100) | YES  |     | NULL    |                |
| author_fname   | varchar(100) | YES  |     | NULL    |                |
| author_lname   | varchar(100) | YES  |     | NULL    |                |
| released_year  | int          | YES  |     | NULL    |                |
| stock_quantity | int          | YES  |     | NULL    |                |
| pages          | int          | YES  |     | NULL    |                |
+----------------+--------------+------+-----+---------+----------------+
7 rows in set (0.06 sec)

mysql> select concat(substr(title,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, stock quantity as quantity from books;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'as quantity from books' at line 1
mysql> select concat(substr(title,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, stock_quantity as quantity from books;
+-----------------------------------------------+----------------------+----------+
| short title                                   | author               | quantity |
+-----------------------------------------------+----------------------+----------+
| ake...                                        | Jhumpa,Lahiri        |       32 |
| hology...                                     | Neil,Gaiman          |       43 |
| Gods...                                       | Neil,Gaiman          |       12 |
| er of Maladies...                             | Jhumpa,Lahiri        |       97 |
| m for the King: A Novel...                    | Dave,Eggers          |      154 |
| e...                                          | Dave,Eggers          |       26 |
| ng Adventures of Kavalier & Clay...           | Michael,Chabon       |       68 |
| ...                                           | Patti,Smith          |       55 |
| eaking Work of Staggering Genius...           | Dave,Eggers          |      104 |
| ...                                           | Neil,Gaiman          |      100 |
| alk About When We Talk About Love: Stories... | Raymond,Carver       |       23 |
|  Calling From: Selected Stories...            | Raymond,Carver       |       12 |
| se...                                         | Don,DeLillo          |       49 |
| ow...                                         | John,Steinbeck       |       95 |
|  Stories...                                   | David,Foster Wallace |      172 |
| the Lobster...                                | David,Foster Wallace |       92 |
+-----------------------------------------------+----------------------+----------+
16 rows in set (0.02 sec)

mysql> select concat(substr(title,0,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, stock_quantity as quantity from books;
+-------------+----------------------+----------+
| short title | author               | quantity |
+-------------+----------------------+----------+
| ...         | Jhumpa,Lahiri        |       32 |
| ...         | Neil,Gaiman          |       43 |
| ...         | Neil,Gaiman          |       12 |
| ...         | Jhumpa,Lahiri        |       97 |
| ...         | Dave,Eggers          |      154 |
| ...         | Dave,Eggers          |       26 |
| ...         | Michael,Chabon       |       68 |
| ...         | Patti,Smith          |       55 |
| ...         | Dave,Eggers          |      104 |
| ...         | Neil,Gaiman          |      100 |
| ...         | Raymond,Carver       |       23 |
| ...         | Raymond,Carver       |       12 |
| ...         | Don,DeLillo          |       49 |
| ...         | John,Steinbeck       |       95 |
| ...         | David,Foster Wallace |      172 |
| ...         | David,Foster Wallace |       92 |
+-------------+----------------------+----------+
16 rows in set (0.00 sec)

mysql> select concat(substr(title,1,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, stock_quantity as quantity from books;
+---------------+----------------------+----------+
| short title   | author               | quantity |
+---------------+----------------------+----------+
| The Namesa... | Jhumpa,Lahiri        |       32 |
| Norse Myth... | Neil,Gaiman          |       43 |
| American G... | Neil,Gaiman          |       12 |
| Interprete... | Jhumpa,Lahiri        |       97 |
| A Hologram... | Dave,Eggers          |      154 |
| The Circle... | Dave,Eggers          |       26 |
| The Amazin... | Michael,Chabon       |       68 |
| Just Kids...  | Patti,Smith          |       55 |
| A Heartbre... | Dave,Eggers          |      104 |
| Coraline...   | Neil,Gaiman          |      100 |
| What We Ta... | Raymond,Carver       |       23 |
| Where I'm ... | Raymond,Carver       |       12 |
| White Nois... | Don,DeLillo          |       49 |
| Cannery Ro... | John,Steinbeck       |       95 |
| Oblivion: ... | David,Foster Wallace |      172 |
| Consider t... | David,Foster Wallace |       92 |
+---------------+----------------------+----------+
16 rows in set (0.00 sec)

mysql> select concat(substr(title,1,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, concat(stock_quantity,' in stock') as quantity from books where released_year=2011;
Empty set (0.00 sec)

mysql> select concat(substr(title,1,10),'...') as 'short title', concat(author_fname,',',author_lname) as author, concat(stock_quantity,' in stock') as quantity from books where released_year=2001;
+---------------+-------------+--------------+
| short title   | author      | quantity     |
+---------------+-------------+--------------+
| American G... | Neil,Gaiman | 12 in stock  |
| A Heartbre... | Dave,Eggers | 104 in stock |
+---------------+-------------+--------------+
2 rows in set (0.00 sec)

mysql> select concat(substr(title,1,10),'...') as 'short title', concat(author_lname,',',author_fname) as author, concat(stock_quantity,' in stock') as quantity from books where released_year=2001;
+---------------+-------------+--------------+
| short title   | author      | quantity     |
+---------------+-------------+--------------+
| American G... | Gaiman,Neil | 12 in stock  |
| A Heartbre... | Eggers,Dave | 104 in stock |
+---------------+-------------+--------------+
2 rows in set (0.00 sec)

mysql> INSERT INTO books
    ->     (title, author_fname, author_lname, released_year, stock_quantity, pages)
    ->     VALUES ('10% Happier', 'Dan', 'Harris', 2014, 29, 256),
    ->            ('fake_book', 'Freida', 'Harris', 2001, 287, 428),
    ->            ('Lincoln In The Bardo', 'George', 'Saunders', 2017, 1000, 367);
Query OK, 3 rows affected (0.06 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> select * from books
    -> ;
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
| book_id | title                                               | author_fname | author_lname   | released_year | stock_quantity | pages |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
|       1 | The Namesake                                        | Jhumpa       | Lahiri         |          2003 |             32 |   291 |
|       2 | Norse Mythology                                     | Neil         | Gaiman         |          2016 |             43 |   304 |
|       3 | American Gods                                       | Neil         | Gaiman         |          2001 |             12 |   465 |
|       4 | Interpreter of Maladies                             | Jhumpa       | Lahiri         |          1996 |             97 |   198 |
|       5 | A Hologram for the King: A Novel                    | Dave         | Eggers         |          2012 |            154 |   352 |
|       6 | The Circle                                          | Dave         | Eggers         |          2013 |             26 |   504 |
|       7 | The Amazing Adventures of Kavalier & Clay           | Michael      | Chabon         |          2000 |             68 |   634 |
|       8 | Just Kids                                           | Patti        | Smith          |          2010 |             55 |   304 |
|       9 | A Heartbreaking Work of Staggering Genius           | Dave         | Eggers         |          2001 |            104 |   437 |
|      10 | Coraline                                            | Neil         | Gaiman         |          2003 |            100 |   208 |
|      11 | What We Talk About When We Talk About Love: Stories | Raymond      | Carver         |          1981 |             23 |   176 |
|      12 | Where I'm Calling From: Selected Stories            | Raymond      | Carver         |          1989 |             12 |   526 |
|      13 | White Noise                                         | Don          | DeLillo        |          1985 |             49 |   320 |
|      14 | Cannery Row                                         | John         | Steinbeck      |          1945 |             95 |   181 |
|      15 | Oblivion: Stories                                   | David        | Foster Wallace |          2004 |            172 |   329 |
|      16 | Consider the Lobster                                | David        | Foster Wallace |          2005 |             92 |   343 |
|      17 | 10% Happier                                         | Dan          | Harris         |          2014 |             29 |   256 |
|      18 | fake_book                                           | Freida       | Harris         |          2001 |            287 |   428 |
|      19 | Lincoln In The Bardo                                | George       | Saunders       |          2017 |           1000 |   367 |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
19 rows in set (0.00 sec)

mysql> select distinct(author_lname) from books;
+----------------+
| author_lname   |
+----------------+
| Lahiri         |
| Gaiman         |
| Eggers         |
| Chabon         |
| Smith          |
| Carver         |
| DeLillo        |
| Steinbeck      |
| Foster Wallace |
| Harris         |
| Saunders       |
+----------------+
11 rows in set (0.00 sec)

mysql> select distinct(released_year) from books;
+---------------+
| released_year |
+---------------+
|          2003 |
|          2016 |
|          2001 |
|          1996 |
|          2012 |
|          2013 |
|          2000 |
|          2010 |
|          1981 |
|          1989 |
|          1985 |
|          1945 |
|          2004 |
|          2005 |
|          2014 |
|          2017 |
+---------------+
16 rows in set (0.00 sec)

mysql> select distint(concat(author_fname,' ',author_lname) from books;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from books' at line 1
mysql> select distint(concat(author_fname,' ',author_lname)) from books;
ERROR 1305 (42000): FUNCTION book_shop.distint does not exist
mysql> select distinct(concat(author_fname,' ',author_lname)) from books;
+-----------------------------------------+
| (concat(author_fname,' ',author_lname)) |
+-----------------------------------------+
| Jhumpa Lahiri                           |
| Neil Gaiman                             |
| Dave Eggers                             |
| Michael Chabon                          |
| Patti Smith                             |
| Raymond Carver                          |
| Don DeLillo                             |
| John Steinbeck                          |
| David Foster Wallace                    |
| Dan Harris                              |
| Freida Harris                           |
| George Saunders                         |
+-----------------------------------------+
12 rows in set (0.05 sec)

mysql> select author_lname,author_fname from books;
+----------------+--------------+
| author_lname   | author_fname |
+----------------+--------------+
| Lahiri         | Jhumpa       |
| Gaiman         | Neil         |
| Gaiman         | Neil         |
| Lahiri         | Jhumpa       |
| Eggers         | Dave         |
| Eggers         | Dave         |
| Chabon         | Michael      |
| Smith          | Patti        |
| Eggers         | Dave         |
| Gaiman         | Neil         |
| Carver         | Raymond      |
| Carver         | Raymond      |
| DeLillo        | Don          |
| Steinbeck      | John         |
| Foster Wallace | David        |
| Foster Wallace | David        |
| Harris         | Dan          |
| Harris         | Freida       |
| Saunders       | George       |
+----------------+--------------+
19 rows in set (0.03 sec)

mysql> select distinct author_fname from books;
+--------------+
| author_fname |
+--------------+
| Jhumpa       |
| Neil         |
| Dave         |
| Michael      |
| Patti        |
| Raymond      |
| Don          |
| John         |
| David        |
| Dan          |
| Freida       |
| George       |
+--------------+
12 rows in set (0.00 sec)

mysql> select author_fname,author_lname from books;
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Jhumpa       | Lahiri         |
| Neil         | Gaiman         |
| Neil         | Gaiman         |
| Jhumpa       | Lahiri         |
| Dave         | Eggers         |
| Dave         | Eggers         |
| Michael      | Chabon         |
| Patti        | Smith          |
| Dave         | Eggers         |
| Neil         | Gaiman         |
| Raymond      | Carver         |
| Raymond      | Carver         |
| Don          | DeLillo        |
| John         | Steinbeck      |
| David        | Foster Wallace |
| David        | Foster Wallace |
| Dan          | Harris         |
| Freida       | Harris         |
| George       | Saunders       |
+--------------+----------------+
19 rows in set (0.00 sec)

mysql> select DISTINCT author_fname,author_lname from books;
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Jhumpa       | Lahiri         |
| Neil         | Gaiman         |
| Dave         | Eggers         |
| Michael      | Chabon         |
| Patti        | Smith          |
| Raymond      | Carver         |
| Don          | DeLillo        |
| John         | Steinbeck      |
| David        | Foster Wallace |
| Dan          | Harris         |
| Freida       | Harris         |
| George       | Saunders       |
+--------------+----------------+
12 rows in set (0.00 sec)

mysql> select DISTINCT author_fname,author_lname from books order by suthor_name;
ERROR 1054 (42S22): Unknown column 'suthor_name' in 'order clause'
mysql> select DISTINCT author_fname,author_lname from books order by author_name;
ERROR 1054 (42S22): Unknown column 'author_name' in 'order clause'
mysql> select DISTINCT author_fname,author_lname from books order_by author_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'author_name' at line 1
mysql> select DISTINCT author_fname,author_lname from books order by author_lname;
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Raymond      | Carver         |
| Michael      | Chabon         |
| Don          | DeLillo        |
| Dave         | Eggers         |
| David        | Foster Wallace |
| Neil         | Gaiman         |
| Dan          | Harris         |
| Freida       | Harris         |
| Jhumpa       | Lahiri         |
| George       | Saunders       |
| Patti        | Smith          |
| John         | Steinbeck      |
+--------------+----------------+
12 rows in set (0.05 sec)

mysql> select DISTINCT author_fname,author_lname from books order by author_fname;
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Dan          | Harris         |
| Dave         | Eggers         |
| David        | Foster Wallace |
| Don          | DeLillo        |
| Freida       | Harris         |
| George       | Saunders       |
| Jhumpa       | Lahiri         |
| John         | Steinbeck      |
| Michael      | Chabon         |
| Neil         | Gaiman         |
| Patti        | Smith          |
| Raymond      | Carver         |
+--------------+----------------+
12 rows in set (0.00 sec)

mysql> select DISTINCT author_fname,author_lname from books order by desc author_fname;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'desc author_fname' at line 1
mysql> select DISTINCT author_fname,author_lname from books order by author_fname desc;
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Raymond      | Carver         |
| Patti        | Smith          |
| Neil         | Gaiman         |
| Michael      | Chabon         |
| John         | Steinbeck      |
| Jhumpa       | Lahiri         |
| George       | Saunders       |
| Freida       | Harris         |
| Don          | DeLillo        |
| David        | Foster Wallace |
| Dave         | Eggers         |
| Dan          | Harris         |
+--------------+----------------+
12 rows in set (0.00 sec)

mysql> select DISTINCT author_fname,author_lname from books order by author_fname asc;
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Dan          | Harris         |
| Dave         | Eggers         |
| David        | Foster Wallace |
| Don          | DeLillo        |
| Freida       | Harris         |
| George       | Saunders       |
| Jhumpa       | Lahiri         |
| John         | Steinbeck      |
| Michael      | Chabon         |
| Neil         | Gaiman         |
| Patti        | Smith          |
| Raymond      | Carver         |
+--------------+----------------+
12 rows in set (0.00 sec)

mysql> desc books;
+----------------+--------------+------+-----+---------+----------------+
| Field          | Type         | Null | Key | Default | Extra          |
+----------------+--------------+------+-----+---------+----------------+
| book_id        | int          | NO   | PRI | NULL    | auto_increment |
| title          | varchar(100) | YES  |     | NULL    |                |
| author_fname   | varchar(100) | YES  |     | NULL    |                |
| author_lname   | varchar(100) | YES  |     | NULL    |                |
| released_year  | int          | YES  |     | NULL    |                |
| stock_quantity | int          | YES  |     | NULL    |                |
| pages          | int          | YES  |     | NULL    |                |
+----------------+--------------+------+-----+---------+----------------+
7 rows in set (0.01 sec)

mysql> select title,pages from books;
+-----------------------------------------------------+-------+
| title                                               | pages |
+-----------------------------------------------------+-------+
| The Namesake                                        |   291 |
| Norse Mythology                                     |   304 |
| American Gods                                       |   465 |
| Interpreter of Maladies                             |   198 |
| A Hologram for the King: A Novel                    |   352 |
| The Circle                                          |   504 |
| The Amazing Adventures of Kavalier & Clay           |   634 |
| Just Kids                                           |   304 |
| A Heartbreaking Work of Staggering Genius           |   437 |
| Coraline                                            |   208 |
| What We Talk About When We Talk About Love: Stories |   176 |
| Where I'm Calling From: Selected Stories            |   526 |
| White Noise                                         |   320 |
| Cannery Row                                         |   181 |
| Oblivion: Stories                                   |   329 |
| Consider the Lobster                                |   343 |
| 10% Happier                                         |   256 |
| fake_book                                           |   428 |
| Lincoln In The Bardo                                |   367 |
+-----------------------------------------------------+-------+
19 rows in set (0.00 sec)

mysql> select title,pages from books order by pages;
+-----------------------------------------------------+-------+
| title                                               | pages |
+-----------------------------------------------------+-------+
| What We Talk About When We Talk About Love: Stories |   176 |
| Cannery Row                                         |   181 |
| Interpreter of Maladies                             |   198 |
| Coraline                                            |   208 |
| 10% Happier                                         |   256 |
| The Namesake                                        |   291 |
| Norse Mythology                                     |   304 |
| Just Kids                                           |   304 |
| White Noise                                         |   320 |
| Oblivion: Stories                                   |   329 |
| Consider the Lobster                                |   343 |
| A Hologram for the King: A Novel                    |   352 |
| Lincoln In The Bardo                                |   367 |
| fake_book                                           |   428 |
| A Heartbreaking Work of Staggering Genius           |   437 |
| American Gods                                       |   465 |
| The Circle                                          |   504 |
| Where I'm Calling From: Selected Stories            |   526 |
| The Amazing Adventures of Kavalier & Clay           |   634 |
+-----------------------------------------------------+-------+
19 rows in set (0.00 sec)

mysql> select title,pages from books order by pages desc;
+-----------------------------------------------------+-------+
| title                                               | pages |
+-----------------------------------------------------+-------+
| The Amazing Adventures of Kavalier & Clay           |   634 |
| Where I'm Calling From: Selected Stories            |   526 |
| The Circle                                          |   504 |
| American Gods                                       |   465 |
| A Heartbreaking Work of Staggering Genius           |   437 |
| fake_book                                           |   428 |
| Lincoln In The Bardo                                |   367 |
| A Hologram for the King: A Novel                    |   352 |
| Consider the Lobster                                |   343 |
| Oblivion: Stories                                   |   329 |
| White Noise                                         |   320 |
| Norse Mythology                                     |   304 |
| Just Kids                                           |   304 |
| The Namesake                                        |   291 |
| 10% Happier                                         |   256 |
| Coraline                                            |   208 |
| Interpreter of Maladies                             |   198 |
| Cannery Row                                         |   181 |
| What We Talk About When We Talk About Love: Stories |   176 |
+-----------------------------------------------------+-------+
19 rows in set (0.00 sec)

mysql> select title,pages from books order by pages desc limit 1;
+-------------------------------------------+-------+
| title                                     | pages |
+-------------------------------------------+-------+
| The Amazing Adventures of Kavalier & Clay |   634 |
+-------------------------------------------+-------+
1 row in set (0.00 sec)

mysql> select title,pages from books order by release_year;
ERROR 1054 (42S22): Unknown column 'release_year' in 'order clause'
mysql> select title,pages from books order by released_year;
+-----------------------------------------------------+-------+
| title                                               | pages |
+-----------------------------------------------------+-------+
| Cannery Row                                         |   181 |
| What We Talk About When We Talk About Love: Stories |   176 |
| White Noise                                         |   320 |
| Where I'm Calling From: Selected Stories            |   526 |
| Interpreter of Maladies                             |   198 |
| The Amazing Adventures of Kavalier & Clay           |   634 |
| American Gods                                       |   465 |
| A Heartbreaking Work of Staggering Genius           |   437 |
| fake_book                                           |   428 |
| The Namesake                                        |   291 |
| Coraline                                            |   208 |
| Oblivion: Stories                                   |   329 |
| Consider the Lobster                                |   343 |
| Just Kids                                           |   304 |
| A Hologram for the King: A Novel                    |   352 |
| The Circle                                          |   504 |
| 10% Happier                                         |   256 |
| Norse Mythology                                     |   304 |
| Lincoln In The Bardo                                |   367 |
+-----------------------------------------------------+-------+
19 rows in set (0.00 sec)

mysql> select title,released_year from books
    -> ;
+-----------------------------------------------------+---------------+
| title                                               | released_year |
+-----------------------------------------------------+---------------+
| The Namesake                                        |          2003 |
| Norse Mythology                                     |          2016 |
| American Gods                                       |          2001 |
| Interpreter of Maladies                             |          1996 |
| A Hologram for the King: A Novel                    |          2012 |
| The Circle                                          |          2013 |
| The Amazing Adventures of Kavalier & Clay           |          2000 |
| Just Kids                                           |          2010 |
| A Heartbreaking Work of Staggering Genius           |          2001 |
| Coraline                                            |          2003 |
| What We Talk About When We Talk About Love: Stories |          1981 |
| Where I'm Calling From: Selected Stories            |          1989 |
| White Noise                                         |          1985 |
| Cannery Row                                         |          1945 |
| Oblivion: Stories                                   |          2004 |
| Consider the Lobster                                |          2005 |
| 10% Happier                                         |          2014 |
| fake_book                                           |          2001 |
| Lincoln In The Bardo                                |          2017 |
+-----------------------------------------------------+---------------+
19 rows in set (0.00 sec)

mysql> select author_fname,title,released_year from books order by 2;
+--------------+-----------------------------------------------------+---------------+
| author_fname | title                                               | released_year |
+--------------+-----------------------------------------------------+---------------+
| Dan          | 10% Happier                                         |          2014 |
| Dave         | A Heartbreaking Work of Staggering Genius           |          2001 |
| Dave         | A Hologram for the King: A Novel                    |          2012 |
| Neil         | American Gods                                       |          2001 |
| John         | Cannery Row                                         |          1945 |
| David        | Consider the Lobster                                |          2005 |
| Neil         | Coraline                                            |          2003 |
| Freida       | fake_book                                           |          2001 |
| Jhumpa       | Interpreter of Maladies                             |          1996 |
| Patti        | Just Kids                                           |          2010 |
| George       | Lincoln In The Bardo                                |          2017 |
| Neil         | Norse Mythology                                     |          2016 |
| David        | Oblivion: Stories                                   |          2004 |
| Michael      | The Amazing Adventures of Kavalier & Clay           |          2000 |
| Dave         | The Circle                                          |          2013 |
| Jhumpa       | The Namesake                                        |          2003 |
| Raymond      | What We Talk About When We Talk About Love: Stories |          1981 |
| Raymond      | Where I'm Calling From: Selected Stories            |          1989 |
| Don          | White Noise                                         |          1985 |
+--------------+-----------------------------------------------------+---------------+
19 rows in set (0.00 sec)

mysql> select author_fname,title,released_year from books order by 1;
+--------------+-----------------------------------------------------+---------------+
| author_fname | title                                               | released_year |
+--------------+-----------------------------------------------------+---------------+
| Dan          | 10% Happier                                         |          2014 |
| Dave         | A Hologram for the King: A Novel                    |          2012 |
| Dave         | The Circle                                          |          2013 |
| Dave         | A Heartbreaking Work of Staggering Genius           |          2001 |
| David        | Oblivion: Stories                                   |          2004 |
| David        | Consider the Lobster                                |          2005 |
| Don          | White Noise                                         |          1985 |
| Freida       | fake_book                                           |          2001 |
| George       | Lincoln In The Bardo                                |          2017 |
| Jhumpa       | The Namesake                                        |          2003 |
| Jhumpa       | Interpreter of Maladies                             |          1996 |
| John         | Cannery Row                                         |          1945 |
| Michael      | The Amazing Adventures of Kavalier & Clay           |          2000 |
| Neil         | Norse Mythology                                     |          2016 |
| Neil         | American Gods                                       |          2001 |
| Neil         | Coraline                                            |          2003 |
| Patti        | Just Kids                                           |          2010 |
| Raymond      | What We Talk About When We Talk About Love: Stories |          1981 |
| Raymond      | Where I'm Calling From: Selected Stories            |          1989 |
+--------------+-----------------------------------------------------+---------------+
19 rows in set (0.00 sec)

mysql> select author_fname,title,released_year from books order by 3;
+--------------+-----------------------------------------------------+---------------+
| author_fname | title                                               | released_year |
+--------------+-----------------------------------------------------+---------------+
| John         | Cannery Row                                         |          1945 |
| Raymond      | What We Talk About When We Talk About Love: Stories |          1981 |
| Don          | White Noise                                         |          1985 |
| Raymond      | Where I'm Calling From: Selected Stories            |          1989 |
| Jhumpa       | Interpreter of Maladies                             |          1996 |
| Michael      | The Amazing Adventures of Kavalier & Clay           |          2000 |
| Neil         | American Gods                                       |          2001 |
| Dave         | A Heartbreaking Work of Staggering Genius           |          2001 |
| Freida       | fake_book                                           |          2001 |
| Jhumpa       | The Namesake                                        |          2003 |
| Neil         | Coraline                                            |          2003 |
| David        | Oblivion: Stories                                   |          2004 |
| David        | Consider the Lobster                                |          2005 |
| Patti        | Just Kids                                           |          2010 |
| Dave         | A Hologram for the King: A Novel                    |          2012 |
| Dave         | The Circle                                          |          2013 |
| Dan          | 10% Happier                                         |          2014 |
| Neil         | Norse Mythology                                     |          2016 |
| George       | Lincoln In The Bardo                                |          2017 |
+--------------+-----------------------------------------------------+---------------+
19 rows in set (0.00 sec)

mysql> select author_fname,title,released_year from books order by 3 desc;
+--------------+-----------------------------------------------------+---------------+
| author_fname | title                                               | released_year |
+--------------+-----------------------------------------------------+---------------+
| George       | Lincoln In The Bardo                                |          2017 |
| Neil         | Norse Mythology                                     |          2016 |
| Dan          | 10% Happier                                         |          2014 |
| Dave         | The Circle                                          |          2013 |
| Dave         | A Hologram for the King: A Novel                    |          2012 |
| Patti        | Just Kids                                           |          2010 |
| David        | Consider the Lobster                                |          2005 |
| David        | Oblivion: Stories                                   |          2004 |
| Jhumpa       | The Namesake                                        |          2003 |
| Neil         | Coraline                                            |          2003 |
| Neil         | American Gods                                       |          2001 |
| Dave         | A Heartbreaking Work of Staggering Genius           |          2001 |
| Freida       | fake_book                                           |          2001 |
| Michael      | The Amazing Adventures of Kavalier & Clay           |          2000 |
| Jhumpa       | Interpreter of Maladies                             |          1996 |
| Raymond      | Where I'm Calling From: Selected Stories            |          1989 |
| Don          | White Noise                                         |          1985 |
| Raymond      | What We Talk About When We Talk About Love: Stories |          1981 |
| John         | Cannery Row                                         |          1945 |
+--------------+-----------------------------------------------------+---------------+
19 rows in set (0.00 sec)

mysql> select author_lname,released_year,substr(title,1,10) from books order by author_lname;
+----------------+---------------+--------------------+
| author_lname   | released_year | substr(title,1,10) |
+----------------+---------------+--------------------+
| Carver         |          1981 | What We Ta         |
| Carver         |          1989 | Where I'm          |
| Chabon         |          2000 | The Amazin         |
| DeLillo        |          1985 | White Nois         |
| Eggers         |          2012 | A Hologram         |
| Eggers         |          2013 | The Circle         |
| Eggers         |          2001 | A Heartbre         |
| Foster Wallace |          2004 | Oblivion:          |
| Foster Wallace |          2005 | Consider t         |
| Gaiman         |          2016 | Norse Myth         |
| Gaiman         |          2001 | American G         |
| Gaiman         |          2003 | Coraline           |
| Harris         |          2014 | 10% Happie         |
| Harris         |          2001 | fake_book          |
| Lahiri         |          2003 | The Namesa         |
| Lahiri         |          1996 | Interprete         |
| Saunders       |          2017 | Lincoln In         |
| Smith          |          2010 | Just Kids          |
| Steinbeck      |          1945 | Cannery Ro         |
+----------------+---------------+--------------------+
19 rows in set (0.00 sec)

mysql> select author_lname,released_year,substr(title,1,10) from books order by author_lname,released_year;
+----------------+---------------+--------------------+
| author_lname   | released_year | substr(title,1,10) |
+----------------+---------------+--------------------+
| Carver         |          1981 | What We Ta         |
| Carver         |          1989 | Where I'm          |
| Chabon         |          2000 | The Amazin         |
| DeLillo        |          1985 | White Nois         |
| Eggers         |          2001 | A Heartbre         |
| Eggers         |          2012 | A Hologram         |
| Eggers         |          2013 | The Circle         |
| Foster Wallace |          2004 | Oblivion:          |
| Foster Wallace |          2005 | Consider t         |
| Gaiman         |          2001 | American G         |
| Gaiman         |          2003 | Coraline           |
| Gaiman         |          2016 | Norse Myth         |
| Harris         |          2001 | fake_book          |
| Harris         |          2014 | 10% Happie         |
| Lahiri         |          1996 | Interprete         |
| Lahiri         |          2003 | The Namesa         |
| Saunders       |          2017 | Lincoln In         |
| Smith          |          2010 | Just Kids          |
| Steinbeck      |          1945 | Cannery Ro         |
+----------------+---------------+--------------------+
19 rows in set (0.00 sec)

mysql> select author_lname,released_year,substr(title,1,10) from books order by author_lname,released_year desc;
+----------------+---------------+--------------------+
| author_lname   | released_year | substr(title,1,10) |
+----------------+---------------+--------------------+
| Carver         |          1989 | Where I'm          |
| Carver         |          1981 | What We Ta         |
| Chabon         |          2000 | The Amazin         |
| DeLillo        |          1985 | White Nois         |
| Eggers         |          2013 | The Circle         |
| Eggers         |          2012 | A Hologram         |
| Eggers         |          2001 | A Heartbre         |
| Foster Wallace |          2005 | Consider t         |
| Foster Wallace |          2004 | Oblivion:          |
| Gaiman         |          2016 | Norse Myth         |
| Gaiman         |          2003 | Coraline           |
| Gaiman         |          2001 | American G         |
| Harris         |          2014 | 10% Happie         |
| Harris         |          2001 | fake_book          |
| Lahiri         |          2003 | The Namesa         |
| Lahiri         |          1996 | Interprete         |
| Saunders       |          2017 | Lincoln In         |
| Smith          |          2010 | Just Kids          |
| Steinbeck      |          1945 | Cannery Ro         |
+----------------+---------------+--------------------+
19 rows in set (0.00 sec)

mysql> select concat(author_lname,released_year) as slug from books order by slug;
+--------------------+
| slug               |
+--------------------+
| Carver1981         |
| Carver1989         |
| Chabon2000         |
| DeLillo1985        |
| Eggers2001         |
| Eggers2012         |
| Eggers2013         |
| Foster Wallace2004 |
| Foster Wallace2005 |
| Gaiman2001         |
| Gaiman2003         |
| Gaiman2016         |
| Harris2001         |
| Harris2014         |
| Lahiri1996         |
| Lahiri2003         |
| Saunders2017       |
| Smith2010          |
| Steinbeck1945      |
+--------------------+
19 rows in set (0.00 sec)

mysql> select concat(author_lname,released_year) as slug from books order by 1;
+--------------------+
| slug               |
+--------------------+
| Carver1981         |
| Carver1989         |
| Chabon2000         |
| DeLillo1985        |
| Eggers2001         |
| Eggers2012         |
| Eggers2013         |
| Foster Wallace2004 |
| Foster Wallace2005 |
| Gaiman2001         |
| Gaiman2003         |
| Gaiman2016         |
| Harris2001         |
| Harris2014         |
| Lahiri1996         |
| Lahiri2003         |
| Saunders2017       |
| Smith2010          |
| Steinbeck1945      |
+--------------------+
19 rows in set (0.00 sec)

mysql> select concat(author_lname,released_year) as slug from books order by 1 desc;
+--------------------+
| slug               |
+--------------------+
| Steinbeck1945      |
| Smith2010          |
| Saunders2017       |
| Lahiri2003         |
| Lahiri1996         |
| Harris2014         |
| Harris2001         |
| Gaiman2016         |
| Gaiman2003         |
| Gaiman2001         |
| Foster Wallace2005 |
| Foster Wallace2004 |
| Eggers2013         |
| Eggers2012         |
| Eggers2001         |
| DeLillo1985        |
| Chabon2000         |
| Carver1989         |
| Carver1981         |
+--------------------+
19 rows in set (0.00 sec)

mysql> select concat(author_lname,released_year) as slug from books order by 1 desc limit 10;
+---------------+
| slug          |
+---------------+
| Steinbeck1945 |
| Smith2010     |
| Saunders2017  |
| Lahiri2003    |
| Lahiri1996    |
| Harris2014    |
| Harris2001    |
| Gaiman2016    |
| Gaiman2003    |
| Gaiman2001    |
+---------------+
10 rows in set (0.03 sec)

mysql> select concat(author_lname,released_year) as slug from books order by 1 desc limit 2;
+---------------+
| slug          |
+---------------+
| Steinbeck1945 |
| Smith2010     |
+---------------+
2 rows in set (0.00 sec)

mysql> select author_fname,title,released_year from books order by 3 limit 5;
+--------------+-----------------------------------------------------+---------------+
| author_fname | title                                               | released_year |
+--------------+-----------------------------------------------------+---------------+
| John         | Cannery Row                                         |          1945 |
| Raymond      | What We Talk About When We Talk About Love: Stories |          1981 |
| Don          | White Noise                                         |          1985 |
| Raymond      | Where I'm Calling From: Selected Stories            |          1989 |
| Jhumpa       | Interpreter of Maladies                             |          1996 |
+--------------+-----------------------------------------------------+---------------+
5 rows in set (0.00 sec)

mysql> select author_fname,title,released_year from books order by 3 limit 5;
+--------------+-----------------------------------------------------+---------------+
| author_fname | title                                               | released_year |
+--------------+-----------------------------------------------------+---------------+
| John         | Cannery Row                                         |          1945 |
| Raymond      | What We Talk About When We Talk About Love: Stories |          1981 |
| Don          | White Noise                                         |          1985 |
| Raymond      | Where I'm Calling From: Selected Stories            |          1989 |
| Jhumpa       | Interpreter of Maladies                             |          1996 |
+--------------+-----------------------------------------------------+---------------+
5 rows in set (0.00 sec)

mysql> select author_fname,released_year from books order by 3 limit 5;
ERROR 1054 (42S22): Unknown column '3' in 'order clause'
mysql> select author_fname,released_year from books order by 2 limit 5;
+--------------+---------------+
| author_fname | released_year |
+--------------+---------------+
| John         |          1945 |
| Raymond      |          1981 |
| Don          |          1985 |
| Raymond      |          1989 |
| Jhumpa       |          1996 |
+--------------+---------------+
5 rows in set (0.00 sec)

mysql> select author_fname,released_year from books order by 2 limit 0,5;
+--------------+---------------+
| author_fname | released_year |
+--------------+---------------+
| John         |          1945 |
| Raymond      |          1981 |
| Don          |          1985 |
| Raymond      |          1989 |
| Jhumpa       |          1996 |
+--------------+---------------+
5 rows in set (0.00 sec)

mysql> select author_fname,released_year from books order by 2 limit 1,5;
+--------------+---------------+
| author_fname | released_year |
+--------------+---------------+
| Raymond      |          1981 |
| Don          |          1985 |
| Raymond      |          1989 |
| Jhumpa       |          1996 |
| Michael      |          2000 |
+--------------+---------------+
5 rows in set (0.00 sec)

mysql> select author_lname from books where author like 'D%';
ERROR 1054 (42S22): Unknown column 'author' in 'where clause'
mysql> select author_lname from books where author like '%da%';
ERROR 1054 (42S22): Unknown column 'author' in 'where clause'
mysql> select author_lname from books where author_lname like '%da%';
Empty set (0.00 sec)

mysql> select author_lname from books where author_fname like '%da%';
+----------------+
| author_lname   |
+----------------+
| Eggers         |
| Eggers         |
| Eggers         |
| Foster Wallace |
| Foster Wallace |
| Harris         |
| Harris         |
+----------------+
7 rows in set (0.00 sec)

mysql> select author_fname,author_lname from books where author_fname like '%da%';
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Dave         | Eggers         |
| Dave         | Eggers         |
| Dave         | Eggers         |
| David        | Foster Wallace |
| David        | Foster Wallace |
| Dan          | Harris         |
| Freida       | Harris         |
+--------------+----------------+
7 rows in set (0.00 sec)

mysql> select author_fname,author_lname from books where author_fname like 'D%';
+--------------+----------------+
| author_fname | author_lname   |
+--------------+----------------+
| Dave         | Eggers         |
| Dave         | Eggers         |
| Dave         | Eggers         |
| Don          | DeLillo        |
| David        | Foster Wallace |
| David        | Foster Wallace |
| Dan          | Harris         |
+--------------+----------------+
7 rows in set (0.00 sec)

mysql> select * from books where title like '%:%';
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
| book_id | title                                               | author_fname | author_lname   | released_year | stock_quantity | pages |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
|       5 | A Hologram for the King: A Novel                    | Dave         | Eggers         |          2012 |            154 |   352 |
|      11 | What We Talk About When We Talk About Love: Stories | Raymond      | Carver         |          1981 |             23 |   176 |
|      12 | Where I'm Calling From: Selected Stories            | Raymond      | Carver         |          1989 |             12 |   526 |
|      15 | Oblivion: Stories                                   | David        | Foster Wallace |          2004 |            172 |   329 |
+---------+-----------------------------------------------------+--------------+----------------+---------------+----------------+-------+
4 rows in set (0.00 sec)

mysql> select * from books where author_fname like '____'
    -> ;
+---------+-------------------------------------------+--------------+--------------+---------------+----------------+-------+
| book_id | title                                     | author_fname | author_lname | released_year | stock_quantity | pages |
+---------+-------------------------------------------+--------------+--------------+---------------+----------------+-------+
|       2 | Norse Mythology                           | Neil         | Gaiman       |          2016 |             43 |   304 |
|       3 | American Gods                             | Neil         | Gaiman       |          2001 |             12 |   465 |
|       5 | A Hologram for the King: A Novel          | Dave         | Eggers       |          2012 |            154 |   352 |
|       6 | The Circle                                | Dave         | Eggers       |          2013 |             26 |   504 |
|       9 | A Heartbreaking Work of Staggering Genius | Dave         | Eggers       |          2001 |            104 |   437 |
|      10 | Coraline                                  | Neil         | Gaiman       |          2003 |            100 |   208 |
|      14 | Cannery Row                               | John         | Steinbeck    |          1945 |             95 |   181 |
+---------+-------------------------------------------+--------------+--------------+---------------+----------------+-------+
7 rows in set (0.00 sec)

mysql> select * from books where author_fname like '_{4}'
    -> ;
Empty set (0.00 sec)

mysql> select * from books where author_fname like '_'
    -> ;
Empty set (0.00 sec)

mysql> select * from books where title like '%\%%'
    -> ;
+---------+-------------+--------------+--------------+---------------+----------------+-------+
| book_id | title       | author_fname | author_lname | released_year | stock_quantity | pages |
+---------+-------------+--------------+--------------+---------------+----------------+-------+
|      17 | 10% Happier | Dan          | Harris       |          2014 |             29 |   256 |
+---------+-------------+--------------+--------------+---------------+----------------+-------+
1 row in set (0.00 sec)

mysql> select title from books where title like '%stories%';
+-----------------------------------------------------+
| title                                               |
+-----------------------------------------------------+
| What We Talk About When We Talk About Love: Stories |
| Where I'm Calling From: Selected Stories            |
| Oblivion: Stories                                   |
+-----------------------------------------------------+
3 rows in set (0.00 sec)

mysql> select title,pages from books order by pages limit 1;
+-----------------------------------------------------+-------+
| title                                               | pages |
+-----------------------------------------------------+-------+
| What We Talk About When We Talk About Love: Stories |   176 |
+-----------------------------------------------------+-------+
1 row in set (0.00 sec)

mysql> select title,pages from books order by pages desc limit 1;
+-------------------------------------------+-------+
| title                                     | pages |
+-------------------------------------------+-------+
| The Amazing Adventures of Kavalier & Clay |   634 |
+-------------------------------------------+-------+
1 row in set (0.00 sec)

mysql> select concat(title,'-',released_year) from books order by released_year desc limit 3;
+---------------------------------+
| concat(title,'-',released_year) |
+---------------------------------+
| Lincoln In The Bardo-2017       |
| Norse Mythology-2016            |
| 10% Happier-2014                |
+---------------------------------+
3 rows in set (0.00 sec)

mysql> select concat(title,'-',released_year)  as summary from books order by released_year desc limit 3;
+---------------------------+
| summary                   |
+---------------------------+
| Lincoln In The Bardo-2017 |
| Norse Mythology-2016      |
| 10% Happier-2014          |
+---------------------------+
3 rows in set (0.00 sec)

mysql> select concat(title,' - ',released_year)  as summary from books order by released_year desc limit 3;
+-----------------------------+
| summary                     |
+-----------------------------+
| Lincoln In The Bardo - 2017 |
| Norse Mythology - 2016      |
| 10% Happier - 2014          |
+-----------------------------+
3 rows in set (0.00 sec)

mysql> select title,author_lname from books where author_lname like '% %';
+----------------------+----------------+
| title                | author_lname   |
+----------------------+----------------+
| Oblivion: Stories    | Foster Wallace |
| Consider the Lobster | Foster Wallace |
+----------------------+----------------+
2 rows in set (0.04 sec)

mysql> select title,released_year,stock_quantity from books order by stock_quantity limit 3;
+-----------------------------------------------------+---------------+----------------+
| title                                               | released_year | stock_quantity |
+-----------------------------------------------------+---------------+----------------+
| Where I'm Calling From: Selected Stories            |          1989 |             12 |
| American Gods                                       |          2001 |             12 |
| What We Talk About When We Talk About Love: Stories |          1981 |             23 |
+-----------------------------------------------------+---------------+----------------+
3 rows in set (0.00 sec)

mysql> select title,released_year,stock_quantity from books order by stock_quantity,released_year desc limit 3;
+-----------------------------------------------------+---------------+----------------+
| title                                               | released_year | stock_quantity |
+-----------------------------------------------------+---------------+----------------+
| American Gods                                       |          2001 |             12 |
| Where I'm Calling From: Selected Stories            |          1989 |             12 |
| What We Talk About When We Talk About Love: Stories |          1981 |             23 |
+-----------------------------------------------------+---------------+----------------+
3 rows in set (0.00 sec)

mysql> select title,author_lname from books order by auther_lname,title;
ERROR 1054 (42S22): Unknown column 'auther_lname' in 'order clause'
mysql> select title,author_lname from books order by author_lname,title;
+-----------------------------------------------------+----------------+
| title                                               | author_lname   |
+-----------------------------------------------------+----------------+
| What We Talk About When We Talk About Love: Stories | Carver         |
| Where I'm Calling From: Selected Stories            | Carver         |
| The Amazing Adventures of Kavalier & Clay           | Chabon         |
| White Noise                                         | DeLillo        |
| A Heartbreaking Work of Staggering Genius           | Eggers         |
| A Hologram for the King: A Novel                    | Eggers         |
| The Circle                                          | Eggers         |
| Consider the Lobster                                | Foster Wallace |
| Oblivion: Stories                                   | Foster Wallace |
| American Gods                                       | Gaiman         |
| Coraline                                            | Gaiman         |
| Norse Mythology                                     | Gaiman         |
| 10% Happier                                         | Harris         |
| fake_book                                           | Harris         |
| Interpreter of Maladies                             | Lahiri         |
| The Namesake                                        | Lahiri         |
| Lincoln In The Bardo                                | Saunders       |
| Just Kids                                           | Smith          |
| Cannery Row                                         | Steinbeck      |
+-----------------------------------------------------+----------------+
19 rows in set (0.00 sec)

mysql> select author_lname from books;
+----------------+
| author_lname   |
+----------------+
| Lahiri         |
| Gaiman         |
| Gaiman         |
| Lahiri         |
| Eggers         |
| Eggers         |
| Chabon         |
| Smith          |
| Eggers         |
| Gaiman         |
| Carver         |
| Carver         |
| DeLillo        |
| Steinbeck      |
| Foster Wallace |
| Foster Wallace |
| Harris         |
| Harris         |
| Saunders       |
+----------------+
19 rows in set (0.00 sec)

mysql> select upper(concat('my favorite author is ',author_fname,' ',author_lname,'!')) from books order by author_lname;
+---------------------------------------------------------------------------+
| upper(concat('my favorite author is ',author_fname,' ',author_lname,'!')) |
+---------------------------------------------------------------------------+
| MY FAVORITE AUTHOR IS RAYMOND CARVER!                                     |
| MY FAVORITE AUTHOR IS RAYMOND CARVER!                                     |
| MY FAVORITE AUTHOR IS MICHAEL CHABON!                                     |
| MY FAVORITE AUTHOR IS DON DELILLO!                                        |
| MY FAVORITE AUTHOR IS DAVE EGGERS!                                        |
| MY FAVORITE AUTHOR IS DAVE EGGERS!                                        |
| MY FAVORITE AUTHOR IS DAVE EGGERS!                                        |
| MY FAVORITE AUTHOR IS DAVID FOSTER WALLACE!                               |
| MY FAVORITE AUTHOR IS DAVID FOSTER WALLACE!                               |
| MY FAVORITE AUTHOR IS NEIL GAIMAN!                                        |
| MY FAVORITE AUTHOR IS NEIL GAIMAN!                                        |
| MY FAVORITE AUTHOR IS NEIL GAIMAN!                                        |
| MY FAVORITE AUTHOR IS DAN HARRIS!                                         |
| MY FAVORITE AUTHOR IS FREIDA HARRIS!                                      |
| MY FAVORITE AUTHOR IS JHUMPA LAHIRI!                                      |
| MY FAVORITE AUTHOR IS JHUMPA LAHIRI!                                      |
| MY FAVORITE AUTHOR IS GEORGE SAUNDERS!                                    |
| MY FAVORITE AUTHOR IS PATTI SMITH!                                        |
| MY FAVORITE AUTHOR IS JOHN STEINBECK!                                     |
+---------------------------------------------------------------------------+
19 rows in set (0.00 sec)

mysql> select count(*) from books;
+----------+
| count(*) |
+----------+
|       19 |
+----------+
1 row in set (0.06 sec)

mysql> select count(*)  as 'total books' from books;
+-------------+
| total books |
+-------------+
|          19 |
+-------------+
1 row in set (0.06 sec)

mysql> select author_fname,count(*) from books group by author_fname;
+--------------+----------+
| author_fname | count(*) |
+--------------+----------+
| Jhumpa       |        2 |
| Neil         |        3 |
| Dave         |        3 |
| Michael      |        1 |
| Patti        |        1 |
| Raymond      |        2 |
| Don          |        1 |
| John         |        1 |
| David        |        2 |
| Dan          |        1 |
| Freida       |        1 |
| George       |        1 |
+--------------+----------+
12 rows in set (0.04 sec)

mysql> select count(pages) from books;
+--------------+
| count(pages) |
+--------------+
|           19 |
+--------------+
1 row in set (0.00 sec)

mysql> select count(distinct(author_fname)) from books;
+-------------------------------+
| count(distinct(author_fname)) |
+-------------------------------+
|                            12 |
+-------------------------------+
1 row in set (0.05 sec)

mysql> select count(*) from books where title like '%The%';
+----------+
| count(*) |
+----------+
|        6 |
+----------+
1 row in set (0.00 sec)

mysql> select released_year,count(*) as 'books released' from books gropu by released_year;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'by released_year' at line 1
mysql> select released_year,count(*) as 'books released' from books group by released_year;
+---------------+----------------+
| released_year | books released |
+---------------+----------------+
|          2003 |              2 |
|          2016 |              1 |
|          2001 |              3 |
|          1996 |              1 |
|          2012 |              1 |
|          2013 |              1 |
|          2000 |              1 |
|          2010 |              1 |
|          1981 |              1 |
|          1989 |              1 |
|          1985 |              1 |
|          1945 |              1 |
|          2004 |              1 |
|          2005 |              1 |
|          2014 |              1 |
|          2017 |              1 |
+---------------+----------------+
16 rows in set (0.00 sec)

mysql> select released_year,count(*) as 'books released' from books group by released_year order by 'books released' desc;
+---------------+----------------+
| released_year | books released |
+---------------+----------------+
|          2003 |              2 |
|          2016 |              1 |
|          2001 |              3 |
|          1996 |              1 |
|          2012 |              1 |
|          2013 |              1 |
|          2000 |              1 |
|          2010 |              1 |
|          1981 |              1 |
|          1989 |              1 |
|          1985 |              1 |
|          1945 |              1 |
|          2004 |              1 |
|          2005 |              1 |
|          2014 |              1 |
|          2017 |              1 |
+---------------+----------------+
16 rows in set (0.00 sec)

mysql> select released_year,count(*) as 'books released' from books group by released_year order by count(*) desc;
+---------------+----------------+
| released_year | books released |
+---------------+----------------+
|          2001 |              3 |
|          2003 |              2 |
|          2016 |              1 |
|          1996 |              1 |
|          2012 |              1 |
|          2013 |              1 |
|          2000 |              1 |
|          2010 |              1 |
|          1981 |              1 |
|          1989 |              1 |
|          1985 |              1 |
|          1945 |              1 |
|          2004 |              1 |
|          2005 |              1 |
|          2014 |              1 |
|          2017 |              1 |
+---------------+----------------+
16 rows in set (0.00 sec)

mysql> select * from books group by released_year;
ERROR 1055 (42000): Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'book_shop.books.book_id' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
mysql> select min(year) from books;
ERROR 1054 (42S22): Unknown column 'year' in 'field list'
mysql> select min(released_year) from books;
+--------------------+
| min(released_year) |
+--------------------+
|               1945 |
+--------------------+
1 row in set (0.04 sec)

mysql> select max(released_year) from books;
+--------------------+
| max(released_year) |
+--------------------+
|               2017 |
+--------------------+
1 row in set (0.00 sec)

mysql> select max(pages) from books;
+------------+
| max(pages) |
+------------+
|        634 |
+------------+
1 row in set (0.00 sec)

mysql> select * from books where pages=max(pages);
ERROR 1111 (HY000): Invalid use of group function
mysql> select min(author_fname) from books;
+-------------------+
| min(author_fname) |
+-------------------+
| Dan               |
+-------------------+
1 row in set (0.02 sec)

mysql> select title from books order by pages desc limit 1;
+-------------------------------------------+
| title                                     |
+-------------------------------------------+
| The Amazing Adventures of Kavalier & Clay |
+-------------------------------------------+
1 row in set (0.00 sec)

mysql> select title from books where pages=(select max(pages) from books);
+-------------------------------------------+
| title                                     |
+-------------------------------------------+
| The Amazing Adventures of Kavalier & Clay |
+-------------------------------------------+
1 row in set (0.04 sec)

mysql> select title,released_year from books where released_year=(select min(year) from books);
ERROR 1054 (42S22): Unknown column 'year' in 'field list'
mysql> select title,released_year from books where released_year=(select min(released_year) from books);
+-------------+---------------+
| title       | released_year |
+-------------+---------------+
| Cannery Row |          1945 |
+-------------+---------------+
1 row in set (0.00 sec)

mysql> select auhtor_fname,author_lname,count(*) as books from booksgroup by author_fname,author_lname;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'by author_fname,author_lname' at line 1
mysql> select auhtor_fname,author_lname,count(*) as books from books group by author_fname,author_lname;
ERROR 1054 (42S22): Unknown column 'auhtor_fname' in 'field list'
mysql> select athtor_fname,author_lname,count(*) as books from books group by author_fname,author_lname;
ERROR 1054 (42S22): Unknown column 'athtor_fname' in 'field list'
mysql> select author_fname,author_lname,count(*) as books from books group by author_fname,author_lname;
+--------------+----------------+-------+
| author_fname | author_lname   | books |
+--------------+----------------+-------+
| Jhumpa       | Lahiri         |     2 |
| Neil         | Gaiman         |     3 |
| Dave         | Eggers         |     3 |
| Michael      | Chabon         |     1 |
| Patti        | Smith          |     1 |
| Raymond      | Carver         |     2 |
| Don          | DeLillo        |     1 |
| John         | Steinbeck      |     1 |
| David        | Foster Wallace |     2 |
| Dan          | Harris         |     1 |
| Freida       | Harris         |     1 |
| George       | Saunders       |     1 |
+--------------+----------------+-------+
12 rows in set (0.00 sec)

mysql> select concat(author_fname,' ',author_lname),count(*) as fullname from books group by fullname;
ERROR 1056 (42000): Can't group on 'fullname'
mysql> select concat(author_fname,' ',author_lname) as fullname,count(*) from books group by fullname;
+----------------------+----------+
| fullname             | count(*) |
+----------------------+----------+
| Jhumpa Lahiri        |        2 |
| Neil Gaiman          |        3 |
| Dave Eggers          |        3 |
| Michael Chabon       |        1 |
| Patti Smith          |        1 |
| Raymond Carver       |        2 |
| Don DeLillo          |        1 |
| John Steinbeck       |        1 |
| David Foster Wallace |        2 |
| Dan Harris           |        1 |
| Freida Harris        |        1 |
| George Saunders      |        1 |
+----------------------+----------+
12 rows in set (0.00 sec)

mysql> select released_year,min(pages) from book group by released_yearl
    -> ;
ERROR 1146 (42S02): Table 'book_shop.book' doesn't exist
mysql> select released_year,min(pages) from book group by released_year;
ERROR 1146 (42S02): Table 'book_shop.book' doesn't exist
mysql> select released_year,min(pages) from books group by released_year;
+---------------+------------+
| released_year | min(pages) |
+---------------+------------+
|          2003 |        208 |
|          2016 |        304 |
|          2001 |        428 |
|          1996 |        198 |
|          2012 |        352 |
|          2013 |        504 |
|          2000 |        634 |
|          2010 |        304 |
|          1981 |        176 |
|          1989 |        526 |
|          1985 |        320 |
|          1945 |        181 |
|          2004 |        329 |
|          2005 |        343 |
|          2014 |        256 |
|          2017 |        367 |
+---------------+------------+
16 rows in set (0.05 sec)

mysql> select author_lname, min(released_year),max(released_year) from books group by author_lname;
+----------------+--------------------+--------------------+
| author_lname   | min(released_year) | max(released_year) |
+----------------+--------------------+--------------------+
| Lahiri         |               1996 |               2003 |
| Gaiman         |               2001 |               2016 |
| Eggers         |               2001 |               2013 |
| Chabon         |               2000 |               2000 |
| Smith          |               2010 |               2010 |
| Carver         |               1981 |               1989 |
| DeLillo        |               1985 |               1985 |
| Steinbeck      |               1945 |               1945 |
| Foster Wallace |               2004 |               2005 |
| Harris         |               2001 |               2014 |
| Saunders       |               2017 |               2017 |
+----------------+--------------------+--------------------+
11 rows in set (0.00 sec)

mysql> select author_fname,author_lname,max(pages) from books group by author_fname,author_lname;
+--------------+----------------+------------+
| author_fname | author_lname   | max(pages) |
+--------------+----------------+------------+
| Jhumpa       | Lahiri         |        291 |
| Neil         | Gaiman         |        465 |
| Dave         | Eggers         |        504 |
| Michael      | Chabon         |        634 |
| Patti        | Smith          |        304 |
| Raymond      | Carver         |        526 |
| Don          | DeLillo        |        320 |
| John         | Steinbeck      |        181 |
| David        | Foster Wallace |        343 |
| Dan          | Harris         |        256 |
| Freida       | Harris         |        428 |
| George       | Saunders       |        367 |
+--------------+----------------+------------+
12 rows in set (0.00 sec)

mysql> select sum(pages) from books;
+------------+
| sum(pages) |
+------------+
|       6623 |
+------------+
1 row in set (0.04 sec)

mysql> select author_lname, sum(pages) from books group by author_lnamel
    -> ;
ERROR 1054 (42S22): Unknown column 'author_lnamel' in 'group statement'
mysql> select author_lname, sum(pages) from books group by author_lname;
+----------------+------------+
| author_lname   | sum(pages) |
+----------------+------------+
| Lahiri         |        489 |
| Gaiman         |        977 |
| Eggers         |       1293 |
| Chabon         |        634 |
| Smith          |        304 |
| Carver         |        702 |
| DeLillo        |        320 |
| Steinbeck      |        181 |
| Foster Wallace |        672 |
| Harris         |        684 |
| Saunders       |        367 |
+----------------+------------+
11 rows in set (0.00 sec)

mysql> select author_lname, sum(pages) from books group by author_lname;
+----------------+------------+
| author_lname   | sum(pages) |
+----------------+------------+
| Lahiri         |        489 |
| Gaiman         |        977 |
| Eggers         |       1293 |
| Chabon         |        634 |
| Smith          |        304 |
| Carver         |        702 |
| DeLillo        |        320 |
| Steinbeck      |        181 |
| Foster Wallace |        672 |
| Harris         |        684 |
| Saunders       |        367 |
+----------------+------------+
11 rows in set (0.00 sec)

mysql> ;
ERROR:
No query specified

mysql> select sum(title) from books;
+------------+
| sum(title) |
+------------+
|         10 |
+------------+
1 row in set, 19 warnings (0.03 sec)

mysql> select sum(author_lname) from books;
+-------------------+
| sum(author_lname) |
+-------------------+
|                 0 |
+-------------------+
1 row in set, 19 warnings (0.00 sec)

mysql> select avg(released_year) from books;
+--------------------+
| avg(released_year) |
+--------------------+
|          1999.7895 |
+--------------------+
1 row in set (0.04 sec)

mysql> select average(released_year) from books;
ERROR 1305 (42000): FUNCTION book_shop.average does not exist
mysql> select avg(pages) from books;
+------------+
| avg(pages) |
+------------+
|   348.5789 |
+------------+
1 row in set (0.00 sec)

mysql> select avg(stock_quantity) from books;
+---------------------+
| avg(stock_quantity) |
+---------------------+
|            128.9474 |
+---------------------+
1 row in set (0.00 sec)

mysql> select released_year,avg(stock_quantity) from books group by released_year;
+---------------+---------------------+
| released_year | avg(stock_quantity) |
+---------------+---------------------+
|          2003 |             66.0000 |
|          2016 |             43.0000 |
|          2001 |            134.3333 |
|          1996 |             97.0000 |
|          2012 |            154.0000 |
|          2013 |             26.0000 |
|          2000 |             68.0000 |
|          2010 |             55.0000 |
|          1981 |             23.0000 |
|          1989 |             12.0000 |
|          1985 |             49.0000 |
|          1945 |             95.0000 |
|          2004 |            172.0000 |
|          2005 |             92.0000 |
|          2014 |             29.0000 |
|          2017 |           1000.0000 |
+---------------+---------------------+
16 rows in set (0.02 sec)

mysql> select count(*) from books;
+----------+
| count(*) |
+----------+
|       19 |
+----------+
1 row in set (0.04 sec)

mysql> select released_year,count(*) from books group by released_year;
+---------------+----------+
| released_year | count(*) |
+---------------+----------+
|          2003 |        2 |
|          2016 |        1 |
|          2001 |        3 |
|          1996 |        1 |
|          2012 |        1 |
|          2013 |        1 |
|          2000 |        1 |
|          2010 |        1 |
|          1981 |        1 |
|          1989 |        1 |
|          1985 |        1 |
|          1945 |        1 |
|          2004 |        1 |
|          2005 |        1 |
|          2014 |        1 |
|          2017 |        1 |
+---------------+----------+
16 rows in set (0.00 sec)

mysql> select sum(stock_quantity) from books;
+---------------------+
| sum(stock_quantity) |
+---------------------+
|                2450 |
+---------------------+
1 row in set (0.00 sec)

mysql> select avg(released_year) from books;
+--------------------+
| avg(released_year) |
+--------------------+
|          1999.7895 |
+--------------------+
1 row in set (0.00 sec)

mysql> select author_fname,author_lname,avg(released_year) from books group by author_fname,author_lname;
+--------------+----------------+--------------------+
| author_fname | author_lname   | avg(released_year) |
+--------------+----------------+--------------------+
| Jhumpa       | Lahiri         |          1999.5000 |
| Neil         | Gaiman         |          2006.6667 |
| Dave         | Eggers         |          2008.6667 |
| Michael      | Chabon         |          2000.0000 |
| Patti        | Smith          |          2010.0000 |
| Raymond      | Carver         |          1985.0000 |
| Don          | DeLillo        |          1985.0000 |
| John         | Steinbeck      |          1945.0000 |
| David        | Foster Wallace |          2004.5000 |
| Dan          | Harris         |          2014.0000 |
| Freida       | Harris         |          2001.0000 |
| George       | Saunders       |          2017.0000 |
+--------------+----------------+--------------------+
12 rows in set (0.00 sec)

mysql> select concat(author_fname,' ',author_lname) from books where pages=(select max(pages) from books);
+---------------------------------------+
| concat(author_fname,' ',author_lname) |
+---------------------------------------+
| Michael Chabon                        |
+---------------------------------------+
1 row in set (0.00 sec)

mysql> select released_year as year,count(*) as '# books', avg(pages) as 'avg pages' from books group by released_year;
+------+---------+-----------+
| year | # books | avg pages |
+------+---------+-----------+
| 2003 |       2 |  249.5000 |
| 2016 |       1 |  304.0000 |
| 2001 |       3 |  443.3333 |
| 1996 |       1 |  198.0000 |
| 2012 |       1 |  352.0000 |
| 2013 |       1 |  504.0000 |
| 2000 |       1 |  634.0000 |
| 2010 |       1 |  304.0000 |
| 1981 |       1 |  176.0000 |
| 1989 |       1 |  526.0000 |
| 1985 |       1 |  320.0000 |
| 1945 |       1 |  181.0000 |
| 2004 |       1 |  329.0000 |
| 2005 |       1 |  343.0000 |
| 2014 |       1 |  256.0000 |
| 2017 |       1 |  367.0000 |
+------+---------+-----------+
16 rows in set (0.00 sec)

mysql> select released_year as year,count(*) as '# books', avg(pages) as 'avg pages' from books group by released_year order by 'avg pages';
+------+---------+-----------+
| year | # books | avg pages |
+------+---------+-----------+
| 2003 |       2 |  249.5000 |
| 2016 |       1 |  304.0000 |
| 2001 |       3 |  443.3333 |
| 1996 |       1 |  198.0000 |
| 2012 |       1 |  352.0000 |
| 2013 |       1 |  504.0000 |
| 2000 |       1 |  634.0000 |
| 2010 |       1 |  304.0000 |
| 1981 |       1 |  176.0000 |
| 1989 |       1 |  526.0000 |
| 1985 |       1 |  320.0000 |
| 1945 |       1 |  181.0000 |
| 2004 |       1 |  329.0000 |
| 2005 |       1 |  343.0000 |
| 2014 |       1 |  256.0000 |
| 2017 |       1 |  367.0000 |
+------+---------+-----------+
16 rows in set (0.00 sec)

mysql> select released_year as year,count(*) as '# books', avg(pages) as 'avg pages' from books group by released_year order by count(*);
+------+---------+-----------+
| year | # books | avg pages |
+------+---------+-----------+
| 2016 |       1 |  304.0000 |
| 1996 |       1 |  198.0000 |
| 2012 |       1 |  352.0000 |
| 2013 |       1 |  504.0000 |
| 2000 |       1 |  634.0000 |
| 2010 |       1 |  304.0000 |
| 1981 |       1 |  176.0000 |
| 1989 |       1 |  526.0000 |
| 1985 |       1 |  320.0000 |
| 1945 |       1 |  181.0000 |
| 2004 |       1 |  329.0000 |
| 2005 |       1 |  343.0000 |
| 2014 |       1 |  256.0000 |
| 2017 |       1 |  367.0000 |
| 2003 |       2 |  249.5000 |
| 2001 |       3 |  443.3333 |
+------+---------+-----------+
16 rows in set (0.00 sec)

mysql> select released_year as year,count(*) as '# books', avg(pages) as 'avg pages' from books group by released_year order by avg(pages);
+------+---------+-----------+
| year | # books | avg pages |
+------+---------+-----------+
| 1981 |       1 |  176.0000 |
| 1945 |       1 |  181.0000 |
| 1996 |       1 |  198.0000 |
| 2003 |       2 |  249.5000 |
| 2014 |       1 |  256.0000 |
| 2016 |       1 |  304.0000 |
| 2010 |       1 |  304.0000 |
| 1985 |       1 |  320.0000 |
| 2004 |       1 |  329.0000 |
| 2005 |       1 |  343.0000 |
| 2012 |       1 |  352.0000 |
| 2017 |       1 |  367.0000 |
| 2001 |       3 |  443.3333 |
| 2013 |       1 |  504.0000 |
| 1989 |       1 |  526.0000 |
| 2000 |       1 |  634.0000 |
+------+---------+-----------+
16 rows in set (0.04 sec)

mysql> select released_year as year,count(*) as '# books', avg(pages) as 'avg pages' from books group by released_year order by avg(pages) desc;
+------+---------+-----------+
| year | # books | avg pages |
+------+---------+-----------+
| 2000 |       1 |  634.0000 |
| 1989 |       1 |  526.0000 |
| 2013 |       1 |  504.0000 |
| 2001 |       3 |  443.3333 |
| 2017 |       1 |  367.0000 |
| 2012 |       1 |  352.0000 |
| 2005 |       1 |  343.0000 |
| 2004 |       1 |  329.0000 |
| 1985 |       1 |  320.0000 |
| 2016 |       1 |  304.0000 |
| 2010 |       1 |  304.0000 |
| 2014 |       1 |  256.0000 |
| 2003 |       2 |  249.5000 |
| 1996 |       1 |  198.0000 |
| 1945 |       1 |  181.0000 |
| 1981 |       1 |  176.0000 |
+------+---------+-----------+
16 rows in set (0.00 sec)

mysql> select released_year as year,count(*) as '# books', avg(pages) as 'avg pages' from books group by released_year order by year;
+------+---------+-----------+
| year | # books | avg pages |
+------+---------+-----------+
| 1945 |       1 |  181.0000 |
| 1981 |       1 |  176.0000 |
| 1985 |       1 |  320.0000 |
| 1989 |       1 |  526.0000 |
| 1996 |       1 |  198.0000 |
| 2000 |       1 |  634.0000 |
| 2001 |       3 |  443.3333 |
| 2003 |       2 |  249.5000 |
| 2004 |       1 |  329.0000 |
| 2005 |       1 |  343.0000 |
| 2010 |       1 |  304.0000 |
| 2012 |       1 |  352.0000 |
| 2013 |       1 |  504.0000 |
| 2014 |       1 |  256.0000 |
| 2016 |       1 |  304.0000 |
| 2017 |       1 |  367.0000 |
+------+---------+-----------+
16 rows in set (0.00 sec)

mysql> CREATE TABLE states(abbr char(2),name varchar(10));
Query OK, 0 rows affected (0.19 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| book_shop          |
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| tea_shop           |
| test               |
| world              |
+--------------------+
9 rows in set (0.04 sec)

mysql> use states;
ERROR 1049 (42000): Unknown database 'states'
mysql> use state;
ERROR 1049 (42000): Unknown database 'state'
mysql> show tables;
+---------------------+
| Tables_in_book_shop |
+---------------------+
| books               |
| states              |
+---------------------+
2 rows in set (0.04 sec)

mysql> desc states;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| abbr  | char(2)     | YES  |     | NULL    |       |
| name  | varchar(10) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.04 sec)

mysql> insert into states values ('IN','India');
Query OK, 1 row affected (0.04 sec)

mysql> insert into states values ('AU','Australia');
Query OK, 1 row affected (0.04 sec)

mysql> select 8 from states;
+---+
| 8 |
+---+
| 8 |
| 8 |
+---+
2 rows in set (0.00 sec)

mysql> select * from states;
+------+-----------+
| abbr | name      |
+------+-----------+
| IN   | India     |
| AU   | Australia |
+------+-----------+
2 rows in set (0.00 sec)

mysql> select char_length(abbr) from states;
+-------------------+
| char_length(abbr) |
+-------------------+
|                 2 |
|                 2 |
+-------------------+
2 rows in set (0.00 sec)

mysql> insert into states values ('A','Australia');
Query OK, 1 row affected (0.06 sec)

mysql> select char_length(abbr) from states;
+-------------------+
| char_length(abbr) |
+-------------------+
|                 2 |
|                 2 |
|                 1 |
+-------------------+
3 rows in set (0.00 sec)

mysql> insert into states values ('Adsdad','Australia');
ERROR 1406 (22001): Data too long for column 'abbr' at row 1
mysql> insert into states values ('ad','Australidsaada');
ERROR 1406 (22001): Data too long for column 'name' at row 1
mysql> create table parent (children TINYINT);
Query OK, 0 rows affected (0.10 sec)

mysql> insert into parent values (2),(4),(5);
Query OK, 3 rows affected (0.06 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> insert into parent values (2232);
ERROR 1264 (22003): Out of range value for column 'children' at row 1
mysql> select * from parent;
+----------+
| children |
+----------+
|        2 |
|        4 |
|        5 |
+----------+
3 rows in set (0.00 sec)

mysql> drop table parent;
Query OK, 0 rows affected (0.13 sec)

mysql> create table parent (children TINYINT unsinged);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'unsinged)' at line 1
mysql> create table parent (children TINYINT unsigned);
Query OK, 0 rows affected (0.09 sec)

mysql> insert into parent values (2232);
ERROR 1264 (22003): Out of range value for column 'children' at row 1
mysql> insert into parent values (2),(4),(5);
Query OK, 3 rows affected (0.05 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> insert into parent values (2),(4),(-5);
ERROR 1264 (22003): Out of range value for column 'children' at row 3
mysql> select * from parent;
+----------+
| children |
+----------+
|        2 |
|        4 |
|        5 |
+----------+
3 rows in set (0.00 sec)

mysql> insert into parent values (2.232);
Query OK, 1 row affected (0.05 sec)

mysql> select * from parent;
+----------+
| children |
+----------+
|        2 |
|        4 |
|        5 |
|        2 |
+----------+
4 rows in set (0.00 sec)

mysql> create table products(price DECIMAL(5,2));
Query OK, 0 rows affected (0.05 sec)

mysql> INSERT INTO products(price) values (3.2)
    -> ;
Query OK, 1 row affected (0.05 sec)

mysql> INSERT INTO products(price) values (332.2);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO products(price) values (332.32);
Query OK, 1 row affected (0.03 sec)

mysql> select * from products;
+--------+
| price  |
+--------+
|   3.20 |
| 332.20 |
| 332.32 |
+--------+
3 rows in set (0.00 sec)

mysql> INSERT INTO products(price) values (33232.32);
ERROR 1264 (22003): Out of range value for column 'price' at row 1
mysql> INSERT INTO products(price) values (33232);
ERROR 1264 (22003): Out of range value for column 'price' at row 1
mysql> INSERT INTO products(price) values (3323.2);
ERROR 1264 (22003): Out of range value for column 'price' at row 1
mysql> INSERT INTO products(price) values (33.23.2);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '.2)' at line 1
mysql> INSERT INTO products(price) values (3.3232);
Query OK, 1 row affected, 1 warning (0.04 sec)

mysql> select * from products;
+--------+
| price  |
+--------+
|   3.20 |
| 332.20 |
| 332.32 |
|   3.32 |
+--------+
4 rows in set (0.00 sec)

mysql> INSERT INTO products(price) values (3.3292);
Query OK, 1 row affected, 1 warning (0.01 sec)

mysql> select * from products;
+--------+
| price  |
+--------+
|   3.20 |
| 332.20 |
| 332.32 |
|   3.32 |
|   3.33 |
+--------+
5 rows in set (0.00 sec)

mysql> create table people(name varchar(50), birthdate DATE, birthtime TIME, birth DATETIME);
Query OK, 0 rows affected (0.12 sec)

mysql> desc people;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| name      | varchar(50) | YES  |     | NULL    |       |
| birthdate | date        | YES  |     | NULL    |       |
| birthtime | time        | YES  |     | NULL    |       |
| birth     | datetime    | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
4 rows in set (0.05 sec)

mysql> insert into people values('elsds','2022-12-22','13:32:12','2333-22-12 14:32:12';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> insert into people values('elsds','2022-12-22','13:32:12','2333-22-12 14:32:12');
ERROR 1292 (22007): Incorrect datetime value: '2333-22-12 14:32:12' for column 'birth' at row 1
mysql> insert into people values('elsds','2022-12-22','13:32:12','2011-02-12 14:32:12');
Query OK, 1 row affected (0.04 sec)

mysql> select * from people;
+-------+------------+-----------+---------------------+
| name  | birthdate  | birthtime | birth               |
+-------+------------+-----------+---------------------+
| elsds | 2022-12-22 | 13:32:12  | 2011-02-12 14:32:12 |
+-------+------------+-----------+---------------------+
1 row in set (0.05 sec)

mysql> select curdate();
+------------+
| curdate()  |
+------------+
| 2023-02-09 |
+------------+
1 row in set (0.00 sec)

mysql> select curtime();
+-----------+
| curtime() |
+-----------+
| 12:36:01  |
+-----------+
1 row in set (0.00 sec)

mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2023-02-09 12:36:07 |
+---------------------+
1 row in set (0.00 sec)

mysql> select current_time()
    -> ;
+----------------+
| current_time() |
+----------------+
| 12:36:31       |
+----------------+
1 row in set (0.00 sec)

mysql> select current_timestamp()
    -> ;
+---------------------+
| current_timestamp() |
+---------------------+
| 2023-02-09 12:36:39 |
+---------------------+
1 row in set (0.00 sec)

mysql> insert into people('Rajesh',curdate(),curtime(),now());
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''Rajesh',curdate(),curtime(),now())' at line 1
mysql> insert into people values('Rajesh',curdate(),curtime(),now());
Query OK, 1 row affected (0.06 sec)

mysql> select * from people;
+--------+------------+-----------+---------------------+
| name   | birthdate  | birthtime | birth               |
+--------+------------+-----------+---------------------+
| elsds  | 2022-12-22 | 13:32:12  | 2011-02-12 14:32:12 |
| Rajesh | 2023-02-09 | 12:37:38  | 2023-02-09 12:37:38 |
+--------+------------+-----------+---------------------+
2 rows in set (0.00 sec)

mysql> insert into people values('Rajesh',current_date(),current_time(),current_timestamp());
Query OK, 1 row affected (0.04 sec)

mysql> select * from people;
+--------+------------+-----------+---------------------+
| name   | birthdate  | birthtime | birth               |
+--------+------------+-----------+---------------------+
| elsds  | 2022-12-22 | 13:32:12  | 2011-02-12 14:32:12 |
| Rajesh | 2023-02-09 | 12:37:38  | 2023-02-09 12:37:38 |
| Rajesh | 2023-02-09 | 12:38:13  | 2023-02-09 12:38:13 |
+--------+------------+-----------+---------------------+
3 rows in set (0.00 sec)

mysql> select day(current_day());
ERROR 1305 (42000): FUNCTION book_shop.current_day does not exist
mysql> select day(current_date());
+---------------------+
| day(current_date()) |
+---------------------+
|                   9 |
+---------------------+
1 row in set (0.04 sec)

mysql> select name, birthdate,day(birthdate) from people;
+--------+------------+----------------+
| name   | birthdate  | day(birthdate) |
+--------+------------+----------------+
| elsds  | 2022-12-22 |             22 |
| Rajesh | 2023-02-09 |              9 |
| Rajesh | 2023-02-09 |              9 |
+--------+------------+----------------+
3 rows in set (0.00 sec)

mysql> select dayofweek(current_date());
+---------------------------+
| dayofweek(current_date()) |
+---------------------------+
|                         5 |
+---------------------------+
1 row in set (0.00 sec)

mysql> select dayofyear(current_date());
+---------------------------+
| dayofyear(current_date()) |
+---------------------------+
|                        40 |
+---------------------------+
1 row in set (0.03 sec)

mysql> select name, birthdate,monthname(birthdate) from people;
+--------+------------+----------------------+
| name   | birthdate  | monthname(birthdate) |
+--------+------------+----------------------+
| elsds  | 2022-12-22 | December             |
| Rajesh | 2023-02-09 | February             |
| Rajesh | 2023-02-09 | February             |
+--------+------------+----------------------+
3 rows in set (0.05 sec)

mysql> select name, birthdate,week(birthdate) from people;
+--------+------------+-----------------+
| name   | birthdate  | week(birthdate) |
+--------+------------+-----------------+
| elsds  | 2022-12-22 |              51 |
| Rajesh | 2023-02-09 |               6 |
| Rajesh | 2023-02-09 |               6 |
+--------+------------+-----------------+
3 rows in set (0.03 sec)

mysql> select birthdate as date, YEAR(birthdate) as year, monthname(birthdate) as month, day(birthdate) as day from people;
+------------+------+----------+------+
| date       | year | month    | day  |
+------------+------+----------+------+
| 2022-12-22 | 2022 | December |   22 |
| 2023-02-09 | 2023 | February |    9 |
| 2023-02-09 | 2023 | February |    9 |
+------------+------+----------+------+
3 rows in set (0.03 sec)

mysql> select birthdate as date, YEAR(birthdate) as year, monthname(birthdate) as month, day(birthdate) as day, dayofweek(birthdate) as 'day of week', dayofyear(birthdate) as 'day of year', week(birthdate) as 'week number' from people;
+------------+------+----------+------+-------------+-------------+-------------+
| date       | year | month    | day  | day of week | day of year | week number |
+------------+------+----------+------+-------------+-------------+-------------+
| 2022-12-22 | 2022 | December |   22 |           5 |         356 |          51 |
| 2023-02-09 | 2023 | February |    9 |           5 |          40 |           6 |
| 2023-02-09 | 2023 | February |    9 |           5 |          40 |           6 |
+------------+------+----------+------+-------------+-------------+-------------+
3 rows in set (0.04 sec)

mysql> select birth from people
    -> ;
+---------------------+
| birth               |
+---------------------+
| 2011-02-12 14:32:12 |
| 2023-02-09 12:37:38 |
| 2023-02-09 12:38:13 |
+---------------------+
3 rows in set (0.00 sec)

mysql> select birth,hour(birth),minutes(birth),seconds(birth) from people;
ERROR 1305 (42000): FUNCTION book_shop.minutes does not exist
mysql> select birth,hour(birth),minute(birth),seconds(birth) from people;
ERROR 1305 (42000): FUNCTION book_shop.seconds does not exist
mysql> select birth,hour(birth),minute(birth),second(birth) from people;
+---------------------+-------------+---------------+---------------+
| birth               | hour(birth) | minute(birth) | second(birth) |
+---------------------+-------------+---------------+---------------+
| 2011-02-12 14:32:12 |          14 |            32 |            12 |
| 2023-02-09 12:37:38 |          12 |            37 |            38 |
| 2023-02-09 12:38:13 |          12 |            38 |            13 |
+---------------------+-------------+---------------+---------------+
3 rows in set (0.00 sec)

mysql> select concat(monthname(birth),' ',day(birth),' ',year(birth)), birth from perople;
ERROR 1146 (42S02): Table 'book_shop.perople' doesn't exist
mysql> select concat(monthname(birth),' ',day(birth),' ',year(birth)), birth from people;
+---------------------------------------------------------+---------------------+
| concat(monthname(birth),' ',day(birth),' ',year(birth)) | birth               |
+---------------------------------------------------------+---------------------+
| February 12 2011                                        | 2011-02-12 14:32:12 |
| February 9 2023                                         | 2023-02-09 12:37:38 |
| February 9 2023                                         | 2023-02-09 12:38:13 |
+---------------------------------------------------------+---------------------+
3 rows in set (0.00 sec)

mysql> select date_format(birth,'%a - %b') from people
    -> ;
+------------------------------+
| date_format(birth,'%a - %b') |
+------------------------------+
| Sat - Feb                    |
| Thu - Feb                    |
| Thu - Feb                    |
+------------------------------+
3 rows in set (0.04 sec)

mysql>


mysql> show tables;
ERROR 1046 (3D000): No database selected
mysql> use book_shop;
Database changed
mysql> show tables;
+---------------------+
| Tables_in_book_shop |
+---------------------+
| books               |
| contact             |
| parent              |
| people              |
| products            |
| states              |
+---------------------+
6 rows in set (0.05 sec)

mysql> insert into contact (name,phone) values ('sdsd','324232342')
    -> ;
Query OK, 1 row affected (0.07 sec)

mysql> select * from contacts;
ERROR 1146 (42S02): Table 'book_shop.contacts' doesn't exist
mysql> select * from contact;
+------+-----------+
| name | phone     |
+------+-----------+
| sdsd | 324232342 |
+------+-----------+
1 row in set (0.00 sec)

mysql> insert into contact (name,phone) values ('timmy','324232342')
    -> ;
ERROR 1062 (23000): Duplicate entry '324232342' for key 'contact.phone'
mysql> select * from contact;
+------+-----------+
| name | phone     |
+------+-----------+
| sdsd | 324232342 |
+------+-----------+
1 row in set (0.00 sec)

mysql> insert into contact (name,phone) values ('sdsd','3242323423')
    -> ;
Query OK, 1 row affected (0.05 sec)

mysql> select * from contact;
+------+------------+
| name | phone      |
+------+------------+
| sdsd | 324232342  |
| sdsd | 3242323423 |
+------+------------+
2 rows in set (0.00 sec)

mysql> create table users (name varchar(10), age int check (age>20));
Query OK, 0 rows affected (0.08 sec)

mysql> insert into users values ('ram',34);
Query OK, 1 row affected (0.01 sec)

mysql> insert into users values ('ram',24);
Query OK, 1 row affected (0.05 sec)

mysql> insert into users values ('ram',14);
ERROR 3819 (HY000): Check constraint 'users_chk_1' is violated.
mysql> select * from users;
+------+------+
| name | age  |
+------+------+
| ram  |   34 |
| ram  |   24 |
+------+------+
2 rows in set (0.04 sec)

mysql> create table palindrome(name varchar(10) check(name=reverse(name));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> create table palindrome(name varchar(10) check(name=reverse(name)));
Query OK, 0 rows affected (0.04 sec)

mysql> insert into palindrome values ('ramar')
    -> ;
Query OK, 1 row affected (0.06 sec)

mysql> insert into palindrome values ('ram')
    -> ;
ERROR 3819 (HY000): Check constraint 'palindrome_chk_1' is violated.
mysql> create table vote(age int not null constraint age_over_18 check (age>18));
Query OK, 0 rows affected (0.07 sec)

mysql> insert into vote values(13);
ERROR 3819 (HY000): Check constraint 'age_over_18' is violated.
mysql> insert into vote values(123);
Query OK, 1 row affected (0.03 sec)

mysql> insert into vote values(23);
Query OK, 1 row affected (0.05 sec)

mysql> select * from vote;
+-----+
| age |
+-----+
| 123 |
|  23 |
+-----+
2 rows in set (0.05 sec)

mysql> ALTER TABLE vote ADD COLUMN (name varchar(20) NOT NULL);
Query OK, 0 rows affected (0.12 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc votes;
ERROR 1146 (42S02): Table 'book_shop.votes' doesn't exist
mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(20) | NO   |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.07 sec)

mysql> select * from vote;
+-----+------+
| age | name |
+-----+------+
| 123 |      |
|  23 |      |
+-----+------+
2 rows in set (0.00 sec)

mysql> ALTER TABLE vote DROP COLUMN name;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from vote;
+-----+
| age |
+-----+
| 123 |
|  23 |
+-----+
2 rows in set (0.00 sec)

mysql> desc vote;
+-------+------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+-------+------+------+-----+---------+-------+
| age   | int  | NO   |     | NULL    |       |
+-------+------+------+-----+---------+-------+
1 row in set (0.04 sec)

mysql> ALTER TABLE vote ADD COLUMN (name varchar(20) NOT NULL DEFAULT 'ram');
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from vote;
+-----+------+
| age | name |
+-----+------+
| 123 | ram  |
|  23 | ram  |
+-----+------+
2 rows in set (0.03 sec)

mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(20) | NO   |     | ram     |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table vote add column (test int);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(20) | NO   |     | ram     |       |
| test  | int         | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.04 sec)

mysql> alter table vote drop column test;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(20) | NO   |     | ram     |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> rename table vote to votes;
Query OK, 0 rows affected (0.07 sec)

mysql> show tables();
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '()' at line 1
mysql> show tables;
+---------------------+
| Tables_in_book_shop |
+---------------------+
| books               |
| contact             |
| palindrome          |
| parent              |
| people              |
| products            |
| states              |
| users               |
| votes               |
+---------------------+
9 rows in set (0.00 sec)

mysql> select * from vote;
ERROR 1146 (42S02): Table 'book_shop.vote' doesn't exist
mysql> select * from votes;
+-----+------+
| age | name |
+-----+------+
| 123 | ram  |
|  23 | ram  |
+-----+------+
2 rows in set (0.00 sec)

mysql> alter table rename votes to vote;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'rename votes to vote' at line 1
mysql> alter table votes rename to vote;
Query OK, 0 rows affected (0.07 sec)

mysql> show tables;
+---------------------+
| Tables_in_book_shop |
+---------------------+
| books               |
| contact             |
| palindrome          |
| parent              |
| people              |
| products            |
| states              |
| users               |
| vote                |
+---------------------+
9 rows in set (0.00 sec)

mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(20) | NO   |     | ram     |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.03 sec)

mysql> alter table vote rename column name to fullname;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc vote;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| age      | int         | NO   |     | NULL    |       |
| fullname | varchar(20) | NO   |     | ram     |       |
+----------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table vote modify fullname varchar(5);
Query OK, 2 rows affected (0.15 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> desc vote;
+----------+------------+------+-----+---------+-------+
| Field    | Type       | Null | Key | Default | Extra |
+----------+------------+------+-----+---------+-------+
| age      | int        | NO   |     | NULL    |       |
| fullname | varchar(5) | YES  |     | NULL    |       |
+----------+------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table vote modify fullname varchar(2);
ERROR 1265 (01000): Data truncated for column 'fullname' at row 1
mysql> select * from vote;
+-----+----------+
| age | fullname |
+-----+----------+
| 123 | ram      |
|  23 | ram      |
+-----+----------+
2 rows in set (0.00 sec)

mysql> desc vote;
+----------+------------+------+-----+---------+-------+
| Field    | Type       | Null | Key | Default | Extra |
+----------+------------+------+-----+---------+-------+
| age      | int        | NO   |     | NULL    |       |
| fullname | varchar(5) | YES  |     | NULL    |       |
+----------+------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table vote chang fullname name varchar(10);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'chang fullname name varchar(10)' at line 1
mysql> alter table vote change fullname name varchar(10);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(10) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table vote add constraint 'age_is_positive' check (age>=0);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''age_is_positive' check (age>=0)' at line 1
mysql> alter table vote add constraint age_is_positive check (age>=0);
Query OK, 2 rows affected (0.06 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> desc vote;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| age   | int         | NO   |     | NULL    |       |
| name  | varchar(10) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> insert into vote values(-12,'da');
ERROR 3819 (HY000): Check constraint 'age_is_positive' is violated.
mysql> insert into vote values(12,'da');
ERROR 3819 (HY000): Check constraint 'age_over_18' is violated.
mysql> insert into vote values(1s2,'da');
ERROR 1054 (42S22): Unknown column '1s2' in 'field list'
mysql> insert into vote values(1232,'da');
Query OK, 1 row affected (0.04 sec)

mysql> insert into vote values(1232,'da');
Query OK, 1 row affected (0.05 sec)

mysql> select * from vote;
+------+------+
| age  | name |
+------+------+
|  123 | ram  |
|   23 | ram  |
| 1232 | da   |
| 1232 | da   |
+------+------+
4 rows in set (0.00 sec)

mysql> alter table vote drop constraint age_over_18;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> insert into vote values(12,'da');
Query OK, 1 row affected (0.01 sec)

mysql> insert into vote values(12,'da');
Query OK, 1 row affected (0.00 sec)

mysql> select * from vote;
+------+------+
| age  | name |
+------+------+
|  123 | ram  |
|   23 | ram  |
| 1232 | da   |
| 1232 | da   |
|   12 | da   |
|   12 | da   |
+------+------+
6 rows in set (0.00 sec)

mysql> create table customers(id int auto_increment primary key, first_name varchar(20) , last_name varchar(20) , email varchar(40));
ERROR 1046 (3D000): No database selected
mysql> use book_shop;
Database changed
mysql> create table customers(id int auto_increment primary key, first_name varchar(20) , last_name varchar(20) , email varchar(40));
Query OK, 0 rows affected (0.14 sec)

mysql> create table customers(id int auto_increment primary key, first_name varchar(20) , last_name varchar(20) , email varchar(40));
ERROR 1050 (42S01): Table 'customers' already exists
mysql> create table orders (id int auto_increment primary key, order_date DATE, maount DECIMAL(8,2), customer_id int, foreign key (customer_id) references customers);
ERROR 1239 (42000): Incorrect foreign key definition for 'foreign key without name': Key reference and table reference don't match
mysql> create table orders (id int auto_increment primary key, order_date DATE, maount DECIMAL(8,2), customer_id int, foreign key (customer_id) references customers(id));
Query OK, 0 rows affected (0.16 sec)

mysql> show tables;
+---------------------+
| Tables_in_book_shop |
+---------------------+
| books               |
| contact             |
| customers           |
| orders              |
| palindrome          |
| parent              |
| people              |
| products            |
| states              |
| users               |
| vote                |
+---------------------+
11 rows in set (0.04 sec)

mysql> create database shop;
Query OK, 1 row affected (0.02 sec)

mysql> use shop;
Database changed
mysql> show database();
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'database()' at line 1
mysql> show database;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'database' at line 1
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
10 rows in set (0.04 sec)

mysql> select database;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> select database();
+------------+
| database() |
+------------+
| shop       |
+------------+
1 row in set (0.00 sec)

mysql> show tables;
Empty set (0.00 sec)

mysql> CREATE TABLE customers (
    ->     id INT PRIMARY KEY AUTO_INCREMENT,
    ->     first_name VARCHAR(50),
    ->     last_name VARCHAR(50),
    ->     email VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.07 sec)

mysql> CREATE TABLE orders (
    ->     id INT PRIMARY KEY AUTO_INCREMENT,
    ->     order_date DATE,
    ->     amount DECIMAL(8,2),
    ->     customer_id INT,
    ->     FOREIGN KEY (customer_id) REFERENCES customers(id)
    -> );
Query OK, 0 rows affected (0.10 sec)

mysql>
mysql> INSERT INTO orders (order_date, amount, customer_id)
    -> VALUES ('2016-02-10', 99.99, 1),
    ->        ('2017-11-11', 35.50, 1),
    ->        ('2014-12-12', 800.67, 2),
    ->        ('2015-01-03', 12.50, 2),
    ->        ('1999-04-11', 450.25, 5);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`shop`.`orders`, CONSTRAINT `orders_ibfk_1` FOREIGN KEY (`customer_id`) REFERENCES `customers` (`id`))
mysql> INSERT INTO customers (first_name, last_name, email)
    -> VALUES ('Boy', 'George', 'george@gmail.com'),
    ->        ('George', 'Michael', 'gm@gmail.com'),
    ->        ('David', 'Bowie', 'david@gmail.com'),
    ->        ('Blue', 'Steele', 'blue@gmail.com'),
    ->        ('Bette', 'Davis', 'bette@aol.com');
Query OK, 5 rows affected (0.03 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO orders (order_date, amount, customer_id)
    -> VALUES ('2016-02-10', 99.99, 1),
    ->        ('2017-11-11', 35.50, 1),
    ->        ('2014-12-12', 800.67, 2),
    ->        ('2015-01-03', 12.50, 2),
    ->        ('1999-04-11', 450.25, 5);
Query OK, 5 rows affected (0.04 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> show tables;
+----------------+
| Tables_in_shop |
+----------------+
| customers      |
| orders         |
+----------------+
2 rows in set (0.05 sec)

mysql> desc customers;
+------------+-------------+------+-----+---------+----------------+
| Field      | Type        | Null | Key | Default | Extra          |
+------------+-------------+------+-----+---------+----------------+
| id         | int         | NO   | PRI | NULL    | auto_increment |
| first_name | varchar(50) | YES  |     | NULL    |                |
| last_name  | varchar(50) | YES  |     | NULL    |                |
| email      | varchar(50) | YES  |     | NULL    |                |
+------------+-------------+------+-----+---------+----------------+
4 rows in set (0.04 sec)

mysql> desc orders;
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| id          | int          | NO   | PRI | NULL    | auto_increment |
| order_date  | date         | YES  |     | NULL    |                |
| amount      | decimal(8,2) | YES  |     | NULL    |                |
| customer_id | int          | YES  | MUL | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> select * from orders;
+----+------------+--------+-------------+
| id | order_date | amount | customer_id |
+----+------------+--------+-------------+
|  6 | 2016-02-10 |  99.99 |           1 |
|  7 | 2017-11-11 |  35.50 |           1 |
|  8 | 2014-12-12 | 800.67 |           2 |
|  9 | 2015-01-03 |  12.50 |           2 |
| 10 | 1999-04-11 | 450.25 |           5 |
+----+------------+--------+-------------+
5 rows in set (0.00 sec)

mysql> select * from customers;
+----+------------+-----------+------------------+
| id | first_name | last_name | email            |
+----+------------+-----------+------------------+
|  1 | Boy        | George    | george@gmail.com |
|  2 | George     | Michael   | gm@gmail.com     |
|  3 | David      | Bowie     | david@gmail.com  |
|  4 | Blue       | Steele    | blue@gmail.com   |
|  5 | Bette      | Davis     | bette@aol.com    |
+----+------------+-----------+------------------+
5 rows in set (0.00 sec)

mysql> select * from customers join orders on customer.id=orders.customer_id ;
ERROR 1054 (42S22): Unknown column 'customer.id' in 'on clause'
mysql> select * from customers join orders ;
+----+------------+-----------+------------------+----+------------+--------+-------------+
| id | first_name | last_name | email            | id | order_date | amount | customer_id |
+----+------------+-----------+------------------+----+------------+--------+-------------+
|  5 | Bette      | Davis     | bette@aol.com    |  6 | 2016-02-10 |  99.99 |           1 |
|  4 | Blue       | Steele    | blue@gmail.com   |  6 | 2016-02-10 |  99.99 |           1 |
|  3 | David      | Bowie     | david@gmail.com  |  6 | 2016-02-10 |  99.99 |           1 |
|  2 | George     | Michael   | gm@gmail.com     |  6 | 2016-02-10 |  99.99 |           1 |
|  1 | Boy        | George    | george@gmail.com |  6 | 2016-02-10 |  99.99 |           1 |
|  5 | Bette      | Davis     | bette@aol.com    |  7 | 2017-11-11 |  35.50 |           1 |
|  4 | Blue       | Steele    | blue@gmail.com   |  7 | 2017-11-11 |  35.50 |           1 |
|  3 | David      | Bowie     | david@gmail.com  |  7 | 2017-11-11 |  35.50 |           1 |
|  2 | George     | Michael   | gm@gmail.com     |  7 | 2017-11-11 |  35.50 |           1 |
|  1 | Boy        | George    | george@gmail.com |  7 | 2017-11-11 |  35.50 |           1 |
|  5 | Bette      | Davis     | bette@aol.com    |  8 | 2014-12-12 | 800.67 |           2 |
|  4 | Blue       | Steele    | blue@gmail.com   |  8 | 2014-12-12 | 800.67 |           2 |
|  3 | David      | Bowie     | david@gmail.com  |  8 | 2014-12-12 | 800.67 |           2 |
|  2 | George     | Michael   | gm@gmail.com     |  8 | 2014-12-12 | 800.67 |           2 |
|  1 | Boy        | George    | george@gmail.com |  8 | 2014-12-12 | 800.67 |           2 |
|  5 | Bette      | Davis     | bette@aol.com    |  9 | 2015-01-03 |  12.50 |           2 |
|  4 | Blue       | Steele    | blue@gmail.com   |  9 | 2015-01-03 |  12.50 |           2 |
|  3 | David      | Bowie     | david@gmail.com  |  9 | 2015-01-03 |  12.50 |           2 |
|  2 | George     | Michael   | gm@gmail.com     |  9 | 2015-01-03 |  12.50 |           2 |
|  1 | Boy        | George    | george@gmail.com |  9 | 2015-01-03 |  12.50 |           2 |
|  5 | Bette      | Davis     | bette@aol.com    | 10 | 1999-04-11 | 450.25 |           5 |
|  4 | Blue       | Steele    | blue@gmail.com   | 10 | 1999-04-11 | 450.25 |           5 |
|  3 | David      | Bowie     | david@gmail.com  | 10 | 1999-04-11 | 450.25 |           5 |
|  2 | George     | Michael   | gm@gmail.com     | 10 | 1999-04-11 | 450.25 |           5 |
|  1 | Boy        | George    | george@gmail.com | 10 | 1999-04-11 | 450.25 |           5 |
+----+------------+-----------+------------------+----+------------+--------+-------------+
25 rows in set (0.00 sec)

mysql> select * from customers natural join orders ;
Empty set (0.00 sec)

mysql> select * from customers;
+----+------------+-----------+------------------+
| id | first_name | last_name | email            |
+----+------------+-----------+------------------+
|  1 | Boy        | George    | george@gmail.com |
|  2 | George     | Michael   | gm@gmail.com     |
|  3 | David      | Bowie     | david@gmail.com  |
|  4 | Blue       | Steele    | blue@gmail.com   |
|  5 | Bette      | Davis     | bette@aol.com    |
+----+------------+-----------+------------------+
5 rows in set (0.00 sec)

mysql> select * from orders where customer_id=(select id from customers where first_name='Boy' and last_name='George');
+----+------------+--------+-------------+
| id | order_date | amount | customer_id |
+----+------------+--------+-------------+
|  6 | 2016-02-10 |  99.99 |           1 |
|  7 | 2017-11-11 |  35.50 |           1 |
+----+------------+--------+-------------+
2 rows in set (0.02 sec)

mysql> select amount, first_name,last_name from orders,curstomers where orders.customer_id=customers.id;
ERROR 1146 (42S02): Table 'shop.curstomers' doesn't exist
mysql> select amount, first_name,last_name from orders,customers where orders.customer_id=customers.id;
+--------+------------+-----------+
| amount | first_name | last_name |
+--------+------------+-----------+
|  99.99 | Boy        | George    |
|  35.50 | Boy        | George    |
| 800.67 | George     | Michael   |
|  12.50 | George     | Michael   |
| 450.25 | Bette      | Davis     |
+--------+------------+-----------+
5 rows in set (0.00 sec)

mysql> select * from customers,orders
    -> ;
+----+------------+-----------+------------------+----+------------+--------+-------------+
| id | first_name | last_name | email            | id | order_date | amount | customer_id |
+----+------------+-----------+------------------+----+------------+--------+-------------+
|  5 | Bette      | Davis     | bette@aol.com    |  6 | 2016-02-10 |  99.99 |           1 |
|  4 | Blue       | Steele    | blue@gmail.com   |  6 | 2016-02-10 |  99.99 |           1 |
|  3 | David      | Bowie     | david@gmail.com  |  6 | 2016-02-10 |  99.99 |           1 |
|  2 | George     | Michael   | gm@gmail.com     |  6 | 2016-02-10 |  99.99 |           1 |
|  1 | Boy        | George    | george@gmail.com |  6 | 2016-02-10 |  99.99 |           1 |
|  5 | Bette      | Davis     | bette@aol.com    |  7 | 2017-11-11 |  35.50 |           1 |
|  4 | Blue       | Steele    | blue@gmail.com   |  7 | 2017-11-11 |  35.50 |           1 |
|  3 | David      | Bowie     | david@gmail.com  |  7 | 2017-11-11 |  35.50 |           1 |
|  2 | George     | Michael   | gm@gmail.com     |  7 | 2017-11-11 |  35.50 |           1 |
|  1 | Boy        | George    | george@gmail.com |  7 | 2017-11-11 |  35.50 |           1 |
|  5 | Bette      | Davis     | bette@aol.com    |  8 | 2014-12-12 | 800.67 |           2 |
|  4 | Blue       | Steele    | blue@gmail.com   |  8 | 2014-12-12 | 800.67 |           2 |
|  3 | David      | Bowie     | david@gmail.com  |  8 | 2014-12-12 | 800.67 |           2 |
|  2 | George     | Michael   | gm@gmail.com     |  8 | 2014-12-12 | 800.67 |           2 |
|  1 | Boy        | George    | george@gmail.com |  8 | 2014-12-12 | 800.67 |           2 |
|  5 | Bette      | Davis     | bette@aol.com    |  9 | 2015-01-03 |  12.50 |           2 |
|  4 | Blue       | Steele    | blue@gmail.com   |  9 | 2015-01-03 |  12.50 |           2 |
|  3 | David      | Bowie     | david@gmail.com  |  9 | 2015-01-03 |  12.50 |           2 |
|  2 | George     | Michael   | gm@gmail.com     |  9 | 2015-01-03 |  12.50 |           2 |
|  1 | Boy        | George    | george@gmail.com |  9 | 2015-01-03 |  12.50 |           2 |
|  5 | Bette      | Davis     | bette@aol.com    | 10 | 1999-04-11 | 450.25 |           5 |
|  4 | Blue       | Steele    | blue@gmail.com   | 10 | 1999-04-11 | 450.25 |           5 |
|  3 | David      | Bowie     | david@gmail.com  | 10 | 1999-04-11 | 450.25 |           5 |
|  2 | George     | Michael   | gm@gmail.com     | 10 | 1999-04-11 | 450.25 |           5 |
|  1 | Boy        | George    | george@gmail.com | 10 | 1999-04-11 | 450.25 |           5 |
+----+------------+-----------+------------------+----+------------+--------+-------------+
25 rows in set (0.00 sec)

mysql> select * from customers join orders on customer.id=orders.customer_id;
ERROR 1054 (42S22): Unknown column 'customer.id' in 'on clause'
mysql> select * from customers join orders on customers.id=orders.customer_id;
+----+------------+-----------+------------------+----+------------+--------+-------------+
| id | first_name | last_name | email            | id | order_date | amount | customer_id |
+----+------------+-----------+------------------+----+------------+--------+-------------+
|  1 | Boy        | George    | george@gmail.com |  6 | 2016-02-10 |  99.99 |           1 |
|  1 | Boy        | George    | george@gmail.com |  7 | 2017-11-11 |  35.50 |           1 |
|  2 | George     | Michael   | gm@gmail.com     |  8 | 2014-12-12 | 800.67 |           2 |
|  2 | George     | Michael   | gm@gmail.com     |  9 | 2015-01-03 |  12.50 |           2 |
|  5 | Bette      | Davis     | bette@aol.com    | 10 | 1999-04-11 | 450.25 |           5 |
+----+------------+-----------+------------------+----+------------+--------+-------------+
5 rows in set (0.00 sec)

mysql> select first_name,last_name,sum(amount) from customers join orders on orders.customer_id=customers.id group by first_name,last_name;
+------------+-----------+-------------+
| first_name | last_name | sum(amount) |
+------------+-----------+-------------+
| Boy        | George    |      135.49 |
| George     | Michael   |      813.17 |
| Bette      | Davis     |      450.25 |
+------------+-----------+-------------+
3 rows in set (0.04 sec)

mysql> select first_name,last_name,sum(amount) total from customers join orders on orders.customer_id=customers.id group by first_name,last_name order by total;
+------------+-----------+--------+
| first_name | last_name | total  |
+------------+-----------+--------+
| Boy        | George    | 135.49 |
| Bette      | Davis     | 450.25 |
| George     | Michael   | 813.17 |
+------------+-----------+--------+
3 rows in set (0.03 sec)

mysql> select first_name,last_name,sum(amount) as total from customers join orders on orders.customer_id=customers.id group by first_name,last_name order by total;
+------------+-----------+--------+
| first_name | last_name | total  |
+------------+-----------+--------+
| Boy        | George    | 135.49 |
| Bette      | Davis     | 450.25 |
| George     | Michael   | 813.17 |
+------------+-----------+--------+
3 rows in set (0.00 sec)

mysql> select first_name,last_name,sum(amount) as total from customers join orders on orders.customer_id=customers.id group by first_name,last_name order by total desc;
+------------+-----------+--------+
| first_name | last_name | total  |
+------------+-----------+--------+
| George     | Michael   | 813.17 |
| Bette      | Davis     | 450.25 |
| Boy        | George    | 135.49 |
+------------+-----------+--------+
3 rows in set (0.00 sec)

mysql> select * from customers left join orders;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> select * from customers left join orders on customers.id=orders.customer_id;
+----+------------+-----------+------------------+------+------------+--------+-------------+
| id | first_name | last_name | email            | id   | order_date | amount | customer_id |
+----+------------+-----------+------------------+------+------------+--------+-------------+
|  1 | Boy        | George    | george@gmail.com |    6 | 2016-02-10 |  99.99 |           1 |
|  1 | Boy        | George    | george@gmail.com |    7 | 2017-11-11 |  35.50 |           1 |
|  2 | George     | Michael   | gm@gmail.com     |    8 | 2014-12-12 | 800.67 |           2 |
|  2 | George     | Michael   | gm@gmail.com     |    9 | 2015-01-03 |  12.50 |           2 |
|  3 | David      | Bowie     | david@gmail.com  | NULL | NULL       |   NULL |        NULL |
|  4 | Blue       | Steele    | blue@gmail.com   | NULL | NULL       |   NULL |        NULL |
|  5 | Bette      | Davis     | bette@aol.com    |   10 | 1999-04-11 | 450.25 |           5 |
+----+------------+-----------+------------------+------+------------+--------+-------------+
7 rows in set (0.00 sec)

mysql> select * from customers right join orders on customers.id=orders.customer_id;
+------+------------+-----------+------------------+----+------------+--------+-------------+
| id   | first_name | last_name | email            | id | order_date | amount | customer_id |
+------+------------+-----------+------------------+----+------------+--------+-------------+
|    1 | Boy        | George    | george@gmail.com |  6 | 2016-02-10 |  99.99 |           1 |
|    1 | Boy        | George    | george@gmail.com |  7 | 2017-11-11 |  35.50 |           1 |
|    2 | George     | Michael   | gm@gmail.com     |  8 | 2014-12-12 | 800.67 |           2 |
|    2 | George     | Michael   | gm@gmail.com     |  9 | 2015-01-03 |  12.50 |           2 |
|    5 | Bette      | Davis     | bette@aol.com    | 10 | 1999-04-11 | 450.25 |           5 |
+------+------------+-----------+------------------+----+------------+--------+-------------+
5 rows in set (0.00 sec)

mysql> select first_name,last_name,sum(amount) as total from customers left join orders on orders.customer_id=customers.id group by first_name,last_name order by total desc;
+------------+-----------+--------+
| first_name | last_name | total  |
+------------+-----------+--------+
| George     | Michael   | 813.17 |
| Bette      | Davis     | 450.25 |
| Boy        | George    | 135.49 |
| David      | Bowie     |   NULL |
| Blue       | Steele    |   NULL |
+------------+-----------+--------+
5 rows in set (0.00 sec)

mysql> select first_name,last_name,sum(amount) as total from customers left join orders on orders.customer_id=customers.id group by first_name,last_name order by total desc;
+------------+-----------+--------+
| first_name | last_name | total  |
+------------+-----------+--------+
| George     | Michael   | 813.17 |
| Bette      | Davis     | 450.25 |
| Boy        | George    | 135.49 |
| David      | Bowie     |   NULL |
| Blue       | Steele    |   NULL |
+------------+-----------+--------+
5 rows in set (0.00 sec)

mysql> select first_name,last_name,IFNULL(sum(amount),0) as total from customers left join orders on orders.customer_id=customers.id group by first_name,last_name order by total desc;
+------------+-----------+--------+
| first_name | last_name | total  |
+------------+-----------+--------+
| George     | Michael   | 813.17 |
| Bette      | Davis     | 450.25 |
| Boy        | George    | 135.49 |
| David      | Bowie     |   0.00 |
| Blue       | Steele    |   0.00 |
+------------+-----------+--------+
5 rows in set (0.05 sec)

mysql> delete from customers where first_name='George';
ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails (`shop`.`orders`, CONSTRAINT `orders_ibfk_1` FOREIGN KEY (`customer_id`) REFERENCES `customers` (`id`))
mysql> select ucase('On delete cascade');
+----------------------------+
| ucase('On delete cascade') |
+----------------------------+
| ON DELETE CASCADE          |
+----------------------------+
1 row in set (0.00 sec)

mysql> drop table customers;
ERROR 3730 (HY000): Cannot drop table 'customers' referenced by a foreign key constraint 'orders_ibfk_1' on table 'orders'.
mysql> drop table orders;
Query OK, 0 rows affected (0.04 sec)

mysql> drop table customers;
Query OK, 0 rows affected (0.09 sec)

mysql> CREATE TABLE customers (
    ->     id INT PRIMARY KEY AUTO_INCREMENT,
    ->     first_name VARCHAR(50),
    ->     last_name VARCHAR(50),
    ->     email VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> REATE TABLE orders (
    ->     id INT PRIMARY KEY AUTO_INCREMENT,
    ->     order_date DATE,
    ->     amount DECIMAL(8 , 2 ),
    ->     customer_id INT,
    ->     FOREIGN KEY (customer_id)
    ->         REFERENCES customers (id)
    ->         ON DELETE CASCADE
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'REATE TABLE orders (
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_date DATE,' at line 1
mysql> CREATE TABLE orders (
    ->     id INT PRIMARY KEY AUTO_INCREMENT,
    ->     order_date DATE,
    ->     amount DECIMAL(8 , 2 ),
    ->     customer_id INT,
    ->     FOREIGN KEY (customer_id)
    ->         REFERENCES customers (id)
    ->         ON DELETE CASCADE
    -> );
Query OK, 0 rows affected (0.10 sec)

mysql> INSERT INTO students (first_name) VALUES
    -> ('Caleb'), ('Samantha'), ('Raj'), ('Carlos'), ('Lisa');
ERROR 1146 (42S02): Table 'shop.students' doesn't exist
mysql>
mysql> INSERT INTO papers (student_id, title, grade ) VALUES
    -> (1, 'My First Book Report', 60),
    -> (1, 'My Second Book Report', 75),
    -> (2, 'Russian Lit Through The Ages', 94),
    -> (2, 'De Montaigne and The Art of The Essay', 98),
    -> (4, 'Borges and Magical Realism', 89);^C
mysql> create table students(id int auto_increment primary key, first_name varchar(20);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
mysql> create table students(id int auto_increment primary key, first_name varchar(20));
Query OK, 0 rows affected (0.05 sec)

mysql> create table papers(title varchar(20),grade int, student_id int, foreign key (student_id) references students(id) on delete cascade);
Query OK, 0 rows affected (0.06 sec)

mysql> show tables;
+----------------+
| Tables_in_shop |
+----------------+
| customers      |
| orders         |
| papers         |
| students       |
+----------------+
4 rows in set (0.00 sec)

mysql> desc students;
+------------+-------------+------+-----+---------+----------------+
| Field      | Type        | Null | Key | Default | Extra          |
+------------+-------------+------+-----+---------+----------------+
| id         | int         | NO   | PRI | NULL    | auto_increment |
| first_name | varchar(20) | YES  |     | NULL    |                |
+------------+-------------+------+-----+---------+----------------+
2 rows in set (0.05 sec)

mysql> desc papers;
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| title      | varchar(20) | YES  |     | NULL    |       |
| grade      | int         | YES  |     | NULL    |       |
| student_id | int         | YES  | MUL | NULL    |       |
+------------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> INSERT INTO students (first_name) VALUES
    -> ('Caleb'), ('Samantha'), ('Raj'), ('Carlos'), ('Lisa');
Query OK, 5 rows affected (0.03 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> INSERT INTO papers (student_id, title, grade ) VALUES
    -> (1, 'My First Book Report', 60),
    -> (1, 'My Second Book Report', 75),
    -> (2, 'Russian Lit Through The Ages', 94),
    -> (2, 'De Montaigne and The Art of The Essay', 98),
    -> (4, 'Borges and Magical Realism', 89);
ERROR 1406 (22001): Data too long for column 'title' at row 2
mysql> alter table papers modify title varchar(100);
Query OK, 0 rows affected (0.11 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> (2, 'De Montaigne and The Art of The Essay', 98),^C
mysql> INSERT INTO papers (student_id, title, grade ) VALUES
    -> (1, 'My First Book Report', 60),
    -> (1, 'My Second Book Report', 75),
    -> (2, 'Russian Lit Through The Ages', 94),
    -> (2, 'De Montaigne and The Art of The Essay', 98),
    -> (4, 'Borges and Magical Realism', 89);
Query OK, 5 rows affected (0.04 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> select * from students;
+----+------------+
| id | first_name |
+----+------------+
|  1 | Caleb      |
|  2 | Samantha   |
|  3 | Raj        |
|  4 | Carlos     |
|  5 | Lisa       |
+----+------------+
5 rows in set (0.00 sec)

mysql> select * from papers;
+---------------------------------------+-------+------------+
| title                                 | grade | student_id |
+---------------------------------------+-------+------------+
| My First Book Report                  |    60 |          1 |
| My Second Book Report                 |    75 |          1 |
| Russian Lit Through The Ages          |    94 |          2 |
| De Montaigne and The Art of The Essay |    98 |          2 |
| Borges and Magical Realism            |    89 |          4 |
+---------------------------------------+-------+------------+
5 rows in set (0.00 sec)

mysql> select first_name,title,grade from students join papers on student.id=papers.student_id;
ERROR 1054 (42S22): Unknown column 'student.id' in 'on clause'
mysql> select first_name,title,grade from students join papers on students.id=papers.student_id;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Caleb      | My First Book Report                  |    60 |
| Caleb      | My Second Book Report                 |    75 |
| Samantha   | Russian Lit Through The Ages          |    94 |
| Samantha   | De Montaigne and The Art of The Essay |    98 |
| Carlos     | Borges and Magical Realism            |    89 |
+------------+---------------------------------------+-------+
5 rows in set (0.00 sec)

mysql> select first_name,title,grade from students join papers on students.id=papers.student_id order by grade desc;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Samantha   | De Montaigne and The Art of The Essay |    98 |
| Samantha   | Russian Lit Through The Ages          |    94 |
| Carlos     | Borges and Magical Realism            |    89 |
| Caleb      | My Second Book Report                 |    75 |
| Caleb      | My First Book Report                  |    60 |
+------------+---------------------------------------+-------+
5 rows in set (0.00 sec)

mysql> select first_name,title,grade from students left join papers on students.id=papers.student_id order by grade desc;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Samantha   | De Montaigne and The Art of The Essay |    98 |
| Samantha   | Russian Lit Through The Ages          |    94 |
| Carlos     | Borges and Magical Realism            |    89 |
| Caleb      | My Second Book Report                 |    75 |
| Caleb      | My First Book Report                  |    60 |
| Raj        | NULL                                  |  NULL |
| Lisa       | NULL                                  |  NULL |
+------------+---------------------------------------+-------+
7 rows in set (0.00 sec)

mysql> select first_name,title,grade from students outer join papers on students.id=papers.student_id order by grade desc;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'outer join papers on students.id=papers.student_id order by grade desc' at line 1
mysql> select first_name,title,grade from students inner join papers on students.id=papers.student_id order by grade desc;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Samantha   | De Montaigne and The Art of The Essay |    98 |
| Samantha   | Russian Lit Through The Ages          |    94 |
| Carlos     | Borges and Magical Realism            |    89 |
| Caleb      | My Second Book Report                 |    75 |
| Caleb      | My First Book Report                  |    60 |
+------------+---------------------------------------+-------+
5 rows in set (0.00 sec)

mysql> select first_name,title,grade from students left join papers on students.id=papers.student_id order by title;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Raj        | NULL                                  |  NULL |
| Lisa       | NULL                                  |  NULL |
| Carlos     | Borges and Magical Realism            |    89 |
| Samantha   | De Montaigne and The Art of The Essay |    98 |
| Caleb      | My First Book Report                  |    60 |
| Caleb      | My Second Book Report                 |    75 |
| Samantha   | Russian Lit Through The Ages          |    94 |
+------------+---------------------------------------+-------+
7 rows in set (0.00 sec)

mysql> select first_name,title,grade from students left join papers on students.id=papers.student_id order by first_name;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Caleb      | My First Book Report                  |    60 |
| Caleb      | My Second Book Report                 |    75 |
| Carlos     | Borges and Magical Realism            |    89 |
| Lisa       | NULL                                  |  NULL |
| Raj        | NULL                                  |  NULL |
| Samantha   | Russian Lit Through The Ages          |    94 |
| Samantha   | De Montaigne and The Art of The Essay |    98 |
+------------+---------------------------------------+-------+
7 rows in set (0.00 sec)

mysql> select first_name,title,grade from students left join papers on students.id=papers.student_id;
+------------+---------------------------------------+-------+
| first_name | title                                 | grade |
+------------+---------------------------------------+-------+
| Caleb      | My First Book Report                  |    60 |
| Caleb      | My Second Book Report                 |    75 |
| Samantha   | Russian Lit Through The Ages          |    94 |
| Samantha   | De Montaigne and The Art of The Essay |    98 |
| Raj        | NULL                                  |  NULL |
| Carlos     | Borges and Magical Realism            |    89 |
| Lisa       | NULL                                  |  NULL |
+------------+---------------------------------------+-------+
7 rows in set (0.00 sec)

mysql> select first_name,IFNULL(title,'MISSING'),IFNULL(grade,0) from students left join papers on students.id=papers.student_id;
+------------+---------------------------------------+-----------------+
| first_name | IFNULL(title,'MISSING')               | IFNULL(grade,0) |
+------------+---------------------------------------+-----------------+
| Caleb      | My First Book Report                  |              60 |
| Caleb      | My Second Book Report                 |              75 |
| Samantha   | Russian Lit Through The Ages          |              94 |
| Samantha   | De Montaigne and The Art of The Essay |              98 |
| Raj        | MISSING                               |               0 |
| Carlos     | Borges and Magical Realism            |              89 |
| Lisa       | MISSING                               |               0 |
+------------+---------------------------------------+-----------------+
7 rows in set (0.00 sec)

mysql> select first_name, IFNULL(avg(grade),0) as average  from students left join papers on students.id=papers.student_id;
ERROR 1140 (42000): In aggregated query without GROUP BY, expression #1 of SELECT list contains nonaggregated column 'shop.students.first_name'; this is incompatible with sql_mode=only_full_group_by
mysql> select first_name, IFNULL(avg(grade),0) as average  from students left join papers on students.id=papers.student_id group by first_name;
+------------+---------+
| first_name | average |
+------------+---------+
| Caleb      | 67.5000 |
| Samantha   | 96.0000 |
| Raj        |  0.0000 |
| Carlos     | 89.0000 |
| Lisa       |  0.0000 |
+------------+---------+
5 rows in set (0.05 sec)

mysql> select first_name, IFNULL(avg(grade),0) as average  from students left join papers on students.id=papers.student_id group by first_name order byy average;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'byy average' at line 1
mysql> select first_name, IFNULL(avg(grade),0) as average  from students left join papers on students.id=papers.student_id group by first_name order by average;
+------------+---------+
| first_name | average |
+------------+---------+
| Raj        |  0.0000 |
| Lisa       |  0.0000 |
| Caleb      | 67.5000 |
| Carlos     | 89.0000 |
| Samantha   | 96.0000 |
+------------+---------+
5 rows in set (0.00 sec)

mysql> select first_name, IFNULL(avg(grade),0) as average  from students left join papers on students.id=papers.student_id group by first_name order by average desc;
+------------+---------+
| first_name | average |
+------------+---------+
| Samantha   | 96.0000 |
| Carlos     | 89.0000 |
| Caleb      | 67.5000 |
| Raj        |  0.0000 |
| Lisa       |  0.0000 |
+------------+---------+
5 rows in set (0.00 sec)

mysql> select first_name, IFNULL(avg(grade),0) as average, case ifnull(avg(grade,0))>70 then 'passing' else 'failing' end as passing_status  from students left join papers on students.id=papers.student_id group by first_name order by average desc;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',0))>70 then 'passing' else 'failing' end as passing_status  from students left ' at line 1
mysql>
-- show databases;
-- use test;
-- select database();
-- select * from test;
-- use tea_shop;
-- show tables;
-- show columns from menu;
-- desc menu;

-- create table pastries(name varchar(50), quantity int) ;
-- show columns from pastries;
-- describe pastries;
-- drop table pastries;

-- use tea_shop;
-- select database();
-- create table people(first_name VARCHAR(20), last_name VARCHAR(20), age INT);
-- INSERT INTO people VALUES ('ram','mohan',34);
-- select * from people;

-- use tea_shop;
-- show tables;
-- create table people(first_name VARCHAR(20), last_name VARCHAR(20), age INT);
-- INSERT INTO people VALUES ('ram','mohan',34);
-- select * from people;


use books;
select first_name,last_name, count(rating) as 'COUNT', 
IFNULL(min(rating),0) as 'MIN', IFNULL(max(rating),0) as 'MAX', 
ROUND(IFNULL(avg(rating),0),2) as 'AVERAGE',
CASE
	WHEN count(rating)>0
    THEN 'active'
    ELSE 'inactive'
END as 'status'
from reviewers left join reviews 
on reviews.reviewer_id=reviewers.id 
group by first_name,last_name;

select first_name,last_name, count(rating) as 'COUNT', 
IFNULL(min(rating),0) as 'MIN', IFNULL(max(rating),0) as 'MAX', 
ROUND(IFNULL(avg(rating),0),2) as 'AVERAGE',
IF(count(rating)>0,'active','inactive') as 'status'
from reviewers left join reviews 
on reviews.reviewer_id=reviewers.id 
group by first_name,last_name;

select title, rating,concat(first_name,' ',last_name) as reviewer
from series join reviews
on series_id=series.id
join reviewers 
on reviewers.id=reviewer_id;
```

### What is database?
- A Collection of data
eg Phone Book
### What is SQL?
### Why it is required?
