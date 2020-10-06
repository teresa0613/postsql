Create a "db_1" database which contains a "users" table which corresponds to the database that we created in the previous course on express:

const db_user = {
alice : '123' ,
bob : '456' ,
charlie : '789' ,
}

postgres=> CREATE TABLE users (id SERIAL PRIMARY KEY , name VARCHAR ( 30 ), password VARCHAR ( 30 ));
CREATE TABLE
postgres=> INSERT INTO users (name, password) VALUES ( ' alice ' , ' 123' ), ( ' bob ' , ' 456 ' ), ('charlie', '789');
INSERT 0 3
postgres=> SELECT \* FROM users;
id | name | password
----+---------+----------
1 | alice | 123
2 | bob | 456
3 | charlie | 789
(3 rows)

Add 3 users 'dan', 'eve', 'faythe' who will have respectively the passwords '101112', '131415', '161718'.
Display all the rows of the "users" table of the "db_1" database.
You will need to provide the SQL commands entered as well as all the outputs of these comman

postgres=> INSERT INTO users (name, password) VALUES ( ' dan ' , ' 101112 ' ), ( ' eve ' , ' 131415 ' ), ('faythe', '161718');
INSERT 0 3
postgres=> SELECT \* FROM users;
id | name | password
----+---------+----------
1 | alice | 123
2 | bob | 456
3 | charlie | 789
4 | dan | 101112
5 | eve | 131415
6 | faythe | 161718
(6 rows)

Display all the lines of the "users" table of the "db_1" database whose password has more than 3 characters. For that you will have to use the function LENGTH.
You will need to provide the SQL commands entered as well as all the outputs of these commands.

postgres=> SELECT \* FROM users WHERE length(password) > 5;
id | name | password
----+--------+----------
4 | dan | 101112
5 | eve | 131415
6 | faythe | 161718
(3 rows)

postgres=> ALTER TABLE users ADD COLUMN bio TEXT DEFAULT 'hello world';
ALTER TABLE
postgres=> SELECT \* FROM users;
id | name | password | bio  
----+---------+----------+-------------
1 | alice | 123 | hello world
2 | bob | 456 | hello world
3 | charlie | 789 | hello world
4 | dan | 101112 | hello world
5 | eve | 131415 | hello world
6 | faythe | 161718 | hello world
(6 rows)

ostgres=> UPDATE users SET bio = Concat('Hello I am', name);
UPDATE 12
postgres=> SELECT \* FROM users;
id | name | password | bio  
----+---------+----------+-------------------
1 | alice | 123 | Hello I am alice
2 | bob | 456 | Hello I am bob
3 | charlie | 789 | Hello I amcharlie
4 | dan | 101112 | Hello I am dan
5 | eve | 131415 | Hello I am eve
6 | faythe | 161718 | Hello I amfaythe
(6 rows)

postgres=> SELECT \* FROM users ORDER BY id DESC LIMIT 2;
id | name | password | bio  
----+--------+----------+------------------
6 | faythe | 161718 | Hello I amfaythe
5 | eve | 131415 | Hello I am eve
(2 rows)
