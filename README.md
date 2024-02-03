# Web Programming
A Full stack web application

# VUE Project setup

```
cd frontend
npm install
npm run format
npm run dev
```

## To Create MongoDB Database
From the Root directory run 

```
docker compose up

```

## To Create Database and add authenticated user to connect
//connect with mongosh shell 

```
use admin 

db.createUser({
   user: 'admin',
   pwd: 'admin',
   roles: [{ role: 'root', db: 'admin' }]
 });
 
 ```

 ## Authenticate 
 ```
 db.auth('admin','admin')
```
## create database 

```
 use esiea
```

## create user for the database to login in 

```
 db.createUser({ user: 'admin', pwd: 'admin', roles: [{ role: 'readWrite', db: 'esiea' }] });

```