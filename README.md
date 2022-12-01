# dbms
 sudo -u postgres psql postgres
[sudo] password for kali: 
psql (15.0 (Debian 15.0-2), server 14.5 (Debian 14.5-3))
Type "help" for help.
postgres=# create table movie(mno int primary key,mname varchar(33),year int);
CREATE TABLE



postgres=# select *from movie
;
 mno | mname | year 
-----+-------+------
(0 rows)



postgres=# insert into movie values(1,'rrr',2019);
INSERT 0 1
postgres=# insert into movie values(1,'kgf',2020);
ERROR:  duplicate key value violates unique constraint "movie_pkey"
DETAIL:  Key (mno)=(1) already exists.
postgres=# insert into movie values(2,'kgf',2020);
INSERT 0 1
postgres=# insert into movie values(3,'kgf3',2022);
INSERT 0 1
postgres=# insert into movie values(4,'boy3',2021);
INSERT 0 1


postgres=# select * from movie;
 mno | mname | year 
-----+-------+------
   1 | rrr   | 2019
   2 | kgf   | 2020
   3 | kgf3  | 2022
   4 | boy3  | 2021
(4 rows)

                                                              ^
postgres=# create table actor(ano int primary key, aname varchar(34));

CREATE TABLE
postgres=# 
postgres=# SELECT * FROM ACTOR;
 ano | aname 
-----+-------
(0 rows)


postgres=# insert into actor values(1,'ak');
INSERT 0 1
postgres=# insert into actor values(2,'rk');
INSERT 0 1
postgres=# insert into actor values(3,'jc');
INSERT 0 1
postgres=# insert into actor values(4,'gg');
INSERT 0 1
postgres=# select * from actor
postgres-# ;
 ano | aname 
-----+-------
   1 | ak
   2 | rk
   3 | jc
   4 | gg
(4 rows)

postgres=# select * from movie;
 mno | mname | year 
-----+-------+------
   1 | rrr   | 2019
   2 | kgf   | 2020
   3 | kgf3  | 2022
   4 | boy3  | 2021
(4 rows)

                                                             ^
postgres=# create table movie_actor(mno int references movie on delete cascade,ano int references actor on delete cascade);
CREATE TABLE
postgres=# select * from movie_actor;
 mno | ano 
-----+-----
(0 rows)



postgres=# insert into movie_actor values(1,4);
INSERT 0 1
postgres=# insert into movie_actor values(2,3);
INSERT 0 1
postgres=# insert into movie_actor values(3,2);
INSERT 0 1
postgres=# insert into movie_actor values(4,1);
INSERT 0 1
postgres=# select * from movie_actor;
 mno | ano 
-----+-----
   1 |   4
   2 |   3
   3 |   2
   4 |   1
(4 rows)

postgres=# select * from movie_actor;
 mno | ano 
-----+-----
   1 |   4
   2 |   3
   3 |   2
   4 |   1
(4 rows)

postgres=# select * from actor;
 ano | aname 
-----+-------
   1 | ak
   2 | rk
   3 | jc
   4 | gg
(4 rows)

postgres=# select * from movie;
 mno | mname | year 
-----+-------+------
   1 | rrr   | 2019
   2 | kgf   | 2020
   3 | kgf3  | 2022
   4 | boy3  | 2021
(4 rows)

