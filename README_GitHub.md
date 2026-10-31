User Management System

A full-stack user management application built with Node.js,
Express.js, EJS, and MySQL**. Users can register and log in, while
authenticated users can manage records through a responsive dashboard
and CRUD interface.

## Overview
This is a learning project that demonstrates how to build a
server-rendered web application with user authentication and
database-backed user management.

The application uses Express for server-side routing, EJS for page
templates, and MySQL for persistent data storage.

## Features

-   User registration with server-side validation
-   Password hashing 
-   Login and logout using Express sessions
-   Protected dashboard and user-management pages
-   MySQL database integration
-   Create, read, update, and delete (CRUD) user records
-   Responsive dashboard and user-management interface
-   JSON API endpoints for user operations

## Tech Stack

  Technology              Purpose
  ----------------------- ------------------------------
  Node.js                 JavaScript runtime
  Express.js              Web server and routing
  EJS                     Server-rendered templates
  MySQL                   Relational database
  mysql2                  MySQL driver
  bcrypt                  Password hashing
  express-session         Session-based authentication
  dotenv                  Environment configuration
  HTML, CSS, JavaScript   Frontend

### Prerequisites

Install:

-   [Node.js](https://nodejs.org/)
-   [MySQL Server](https://dev.mysql.com/downloads/mysql/)
-   npm (included with Node.js)

### 1. Clone the repository

Replace the placeholder URL with your GitHub repository URL.

``` bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
cd YOUR-REPOSITORY
```

If you already have the project on your computer, open a terminal in the
project folder instead.

### 2. Install dependencies

``` bash
npm install
```

### 3. Create the MySQL database

Open MySQL and run:

``` sql
CREATE DATABASE suvarna_project;

USE suvarna_project;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    age INT NULL,
    gender VARCHAR(30) NULL
);
```

If the `users` table already exists but does not yet have the `age` and
`gender` columns, run:

``` sql
ALTER TABLE users
ADD COLUMN age INT NULL,
ADD COLUMN gender VARCHAR(30) NULL;
```

Do not run the `CREATE TABLE` statement again if the table already
exists.

### 4. Configure environment variables

Create a `.env` file in the project root:

``` dotenv
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=suvarna_project
DB_PORT=3306
SESSION_SECRET=replace_with_a_long_random_secret
```

Replace the example values with your own local credentials and a long,
random session secret.

Important: Never commit `.env` or publish database credentials and
session secrets.

### 5. Start the application

``` bash
node server.js
```

Open these routes in your browser:

  Page              URL
  ----------------- ---------------------------------
  Registration      http://localhost:3000/
  Login             http://localhost:3000/login
  Dashboard         http://localhost:3000/dashboard
  User Management   http://localhost:3000/users

The dashboard and user-management page require a logged-in session.

## API Documentation

All user API routes require authentication.

  HTTP Method   Endpoint           Description
  ------------- ------------------ -------------------------
  `GET`         `/api/users`       Get all users
  `GET`         `/api/users/:id`   Get a user by ID
  `POST`        `/api/users`       Create a user
  `PUT`         `/api/users/:id`   Update a user's details
  `DELETE`      `/api/users/:id`   Delete a user

### Example: Create a user

`POST /api/users`

Request body:

``` json
{
  "name": "Example User",
  "email": "example@example.com",
  "age": 22,
  "gender": "Other",
  "password": "ExamplePass123"
}
```

The password must contain at least eight characters. The server hashes
passwords before storing them. Password hashes are not included in user
API responses.

## Learning Outcomes

This project provides practice with:

-   Building server-side applications using Node.js and Express
-   Rendering pages with EJS
-   Connecting an application to MySQL
-   Implementing password hashing and session-based authentication
-   Creating REST-style CRUD APIs
-   Connecting frontend JavaScript to backend APIs
-   Organizing a small full-stack application