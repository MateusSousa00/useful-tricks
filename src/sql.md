# SQL basic commands

## creating table
CREATE TABLE "table"."user" (
    id uuid NOT NULL DEFAULT uuid_generate_v4(),
    email varchar NOT NULL,
    "password" varchar NOT NULL,
    "token" varchar NULL
);


## inserting into table
INSERT INTO "table"."user" (id,email,"password","token") VALUES ('uuid-generated-to-id','user@test.com','super-secret-hashed-password','token.from.jwt');

## generate dump file
file = dbeaver > postgres > Databases > postgres > Tools > backup

## enter in postgres cmd
psql -U <username>

## enter in msyql/mariadb cmd
mysql -u <username> -p

## create UUID in postgres:
CREATE EXTENSION "uuid-ossp";

## using dump file in postgres:
pg_restore -U <username> -d <database_name> /tmp/file

## useful commands in pgsql
\l => show databases
\c db => connect on database
\dn => show schemas
\q => quit

## turning root root again
SELECT user, host, plugin FROM mysql.user WHERE user='root';
ALTER USER 'root'@'%' IDENTIFIED WITH 'mysql_native_password' BY 'password';

## Mysql error on DBeaver (Public Key Retrieval is not allowed):
Fix it by changing the url to: jdbc:mysql://localhost:3306/db?allowPublicKeyRetrieval=true&useSSL=false
