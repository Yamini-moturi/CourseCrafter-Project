# CourseCrafter
A full-stack application utilizing Vue.js for the frontend, Express.js for the backend, and MongoDB for database management, with Node.js serving as the runtime environment. Implemented user authentication functionalities with two levels of authorization: admin and user. Admin privileges enabled the management of course details, including posting and modification, while user privileges allowed for image uploads to personal feeds and the updating of profile information. Designed intuitive user interfaces for seamless navigation, ensuring a smooth experience for both admin and user roles. Implemented robust security measures to protect sensitive user data. Integrated session management and data storage mechanisms to enable users to access and view their updated profile details and stored images securely from any location.

# VUE Project setup
 To install and configure frontend

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
 use dbname
```

## create user for the database to login in 

```
 db.createUser({ user: 'admin', pwd: 'admin', roles: [{ role: 'readWrite', db: 'dbname' }] });

```
