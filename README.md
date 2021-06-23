# cloud-sql

Create a VM instance

## comamnd to connect
amitkumardube@instance:~$ psql "sslmode=disable dbname=postgres user=postgres hostaddr=192.168.32.3" \
Password for user postgres: \
psql (11.12 (Debian 11.12-0+deb10u1), server 13.2) \
WARNING: psql major version 11, server major version 13. \
         Some psql features might not work. \
Type "help" for help. \

postgres=> 

## how to enable cloud sql proxy
./cloud_sql_proxy -instances=indian-food1:us-central1:postgre-1=tcp:1234 & \

##  connection via cloud sql proxy
amitkumardube@instance:~$ psql "sslmode=disable dbname=postgres user=postgres hostaddr=127.0.0.1 port=1234"
2021/06/23 19:35:38 New connection for "indian-food1:us-central1:postgre-1"
Password for user postgres: 2021/06/23 19:35:38 Client closed local connection on 127.0.0.1:1234

2021/06/23 19:35:48 New connection for "indian-food1:us-central1:postgre-1"
psql (11.12 (Debian 11.12-0+deb10u1), server 13.2)
WARNING: psql major version 11, server major version 13.
         Some psql features might not work.
Type "help" for help.

postgres=> 

## usage

postgres=> CREATE DATABASE guestbook;
CREATE DATABASE
postgres=> \connect guestbook;
2021/06/23 19:39:46 New connection for "indian-food1:us-central1:postgre-1"
psql (11.12 (Debian 11.12-0+deb10u1), server 13.2)
WARNING: psql major version 11, server major version 13.
         Some psql features might not work.
You are now connected to database "guestbook" as user "postgres".
2021/06/23 19:39:46 Client closed local connection on 127.0.0.1:1234
guestbook=> CREATE TABLE entries (guestName VARCHAR(255), content VARCHAR(255),
guestbook(>                         entryID SERIAL PRIMARY KEY);
CREATE TABLE
guestbook=> INSERT INTO entries (guestName, content) values ('first guest', 'I got here!');
INSERT 0 1
guestbook=> INSERT INTO entries (guestName, content) values ('second guest', 'Me too!');
INSERT 0 1
guestbook=> 
guestbook=> SELECT * FROM entries;
  guestname   |   content   | entryid 
--------------+-------------+---------
 first guest  | I got here! |       1
 second guest | Me too!     |       2
(2 rows)
