# sql_learning
# MySQL<br>
## connect mysql<br>
mysql-ctl cli<br>
exit<br>
## create/drop/use database<br>
CREATE DATABASE IF NOT EXITS *database_name* DEFAULT CAHRSET utf8 COLLATE utf8_general_cli; <br>
DROP/USE DATABASE *database_name*;<br>
## data type<br>
char/varchar decimal/double int timestamp/datetime/year/date/time;<br>
char: fixed lengths, paded with spaces, used in fixed lenths; varchar: most often used; text: less used;<br>
decimal: highest accuracy, then double;<br>
## create table<br>
CREATE TABLE *table_name* (column_name column_type);<br>
NOT NULL, AUTO_INCREAMENT;<br>
## drop table<br>
DROP TABLE *table_name*;<br>
case you donot need the table any more, then use drop;<br>
case you need the table and delete all data, then use truncate;<br>
case you donot need part of data, then use delete;<br>
## insert data<br>
INSERT INTO table_name (column_name1, ...) VALUES (value1,...);<br>
## select data<br>
SELECT column_name1,... FROM table_name [WHERE clause] [LIMIT N,M] [OFFSET M];<br>
** performancce analysis **<br>
??? subquery, join -> too much data;<br>
= "str", like "str%", BETWEEN AND, in (), AND, OR, ORDER BY, DESC;<br>
## WHERE clause<br>
??? where, group by, having:<br>
??? execution order: FROM, including JOIN -> GROUP BY -> HAVING -> WINDOW functions -> SELECT -> DISTINCT -> UNION -> ORDER BY -> LIMIT and OFFSET;<br>
## update data<br>
UPDATE table_name SET column_name1=,... [WHERE clause];<br>
## delete data<br>
DELETE FROM table_name [WHERE clause];<br>
## LIKE clause<br>
LIKE "%sth%";<br>
## UNION clause<br>
concatenate the results of two or more SELECT statements into a single result set;<br>
 Multiple SELECT statements remove duplicate data;<br>
SELECT exp1,... FROM tables UNION [ALL | DISTINCT] SELECT exp1,... FROM tables;<br>
## ORDER BY clause<br>
SELECT exp1,... FROM table_names ORDER BY exp ASC/DESC;<br>
## GROUP BY clause<br>
SELECT COUNT/SUM/AVG(column_name1) FROM table_name;<br>
## JOIN clause<br>
INNER/OUTER/LEFT/RIGHT JOIN;<br>
## NULL value handling<br>
IS NULL, IS NOT NULL;<br>
## DUPLICATE data handling<br>
prevent duplicate data in tables -> PRIMARY KEY/UNIQUE;<br>
statisticcs duplicate data -> COUNT(*) AS repetitions GROUP BY HAVING repetitions > 1;<br>
filter duplicate data -> GROUP BY;<br>
delete duplicate data -> CREATE TABLE new_table GROUP BY, DROP TABLE old_table, ALTER TABLE new_table RENAME old_table/<br>
ALTER TABLE old_table ADD INDEX/PRIMARY KEY();<br>
## AUTO_INCREAMENT<br>
AUTO_INCREAMENT clause;<br>
## regular expression<br>
REGEXP sth just like LIKE;<br>
## transaction<br>
4 conditions must be met: Atomicity/Consistency/Isolation/Durability;<br>
BEGIN: start a ts, SAVEPOINT identifier, ROLLBACK (TO identifier): ts rollback, COMMIT: ts confirmation;<br>
SET AUTOCOMMIT=0/1 disable/turns on autocommit;<br>
## ALTER<br>
delete/add table fields -> ALTER TABLE table_name DROP/ADD (FIRST/AFTER);<br>
modify field name, type, default value -> ALTER TABLE table_name MODIFY/CHANGE/SET DEFAULT;<br>
rename table -> ALTER TABLE table_name1 RENAME TO table_name2;<br>
change engine -> ALTER TABLE table_name engine=new_engine;<br>
remove foreign key constrains -> ALTER TABLE table_name DROP FOREIGN KEY key_name;<br>
## INDEX<br>
inde makes search faster, update slower;<br>
CREATE INDEX index_name ON table_name (column_name);<br>
## TEMPORARY TABLE<br>
CREATE/DROP/SELECT/UPDATE/INSERT TEMPORARY TABLE;<br>
## CLONE TABLE<br>
clone table structure -> SHOW CREATE TABLE table_name/ CREATE TABLE table_name1 LIKE table_name2;<br>
clone table contents -> INSERT INTO SELECT/ INSERT INTO table_name1 SELECT * FROM table_name2;<br>
## METADATA<br>
query results info, db and table info, server info;<br>
## INJECTION<br>
takes data entered by the users and insert it into a table;<br>
## OUTPUT/ INPYT<br> 
SELECT ... INTO OUTFILE ''/ LOAD DATA LOCAL INFILE '' INTO TABLE table_name;<br>
## FUNCTIONS<br>
CONCAT, CONCAT_WS, LOWER, UPPER, REPLACE, SUBSTR, COUNT, NOW, TIMESTAMP, DATEDIFF, DATE_FORMAT, ISNULL;<br>
## OPERATOR<br>
<>;<br>
## Subqueries<br>
a subquery is a SELECT statement within another statement, returns a scalar, column, row, and table <br>
## Window Fuctions<br>
SELECT val, ROW_NUMBER() OVER w AS 'row_number', RANK() OVER w AS 'rank', DENSE_RANK' OVER w AS 'dense_rank' FROM numbers WINDOW w AS (ORDER BY val);<br>
SELECT ...,SUM(sth) OVER() AS sth, SUM(sth) OVER(PARTION BY sth) AS sth FROM sth ORDER BY sth;<br>
SELECT ...,ROW_NUMBER() OVER(PARTITION BY sth ORDER BY sth) AS sth FROM sth; <br>
## SQL optimization<br>
load data, perform action, output;<br>
partition; sample limit; <br>
