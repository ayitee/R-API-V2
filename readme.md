# RESTaurant API

The RESTaurant API provides a digital menu and online ordering system optimized for restaurant management. This API allows for role-based access control, with JWT authentication for secure routes. It features CRUD operations for managing users, menu categories, items, and menu formulas.

## Table of Contents

 - Features
 - Setup and Installation
 - Database Setup
 - Running the API
 - API Endpoints
 - Testing the API
 - Technologies Used

## Features

 - **Role-Based Authentication**: Includes admin and client roles with JWT-secured access.
 - **CRUD Operations**: Endpoints to create, read, update, and delete users, categories, items, and formulas.
 - **Data Relationships**: Categories are associated with items, and formulas can link multiple categories and items.

## Setup and Installation

1.	**Clone the repository:**
     ```bash
     git clone Mars7attack/REST_API
     cd RESTaurant-API
     ```
     
	2.	**Install Dependencies:**

Ensure Node.js and npm are installed, then run:
     ```bash
     npm install
     ```


## Database Setup

**1.	Using Docker:**

Start the database with Docker using:

    ```bash
    docker-compose up -d
    ```

**2.	Manual Setup:**
	•	Import the database.sql file into your MySQL database to set up the necessary tables.

## Running the API

To start the API server:

      ```bash
      npm start
      ```
**The API will run on** `http://localhost:4224`

---

## API Endpoints

### Authentication Routes

- **POST** `/register`: Register a new user.
  - **Body**: `{ username, password, role }`
  - The password is hashed, and user roles (admin or client) are supported.
- **POST** `/login`: Authenticate and receive a JWT token.
  - **Body**: `{ username, password }`

### Category Routes (Admin Role Required)

- **GET** `/categories`: Retrieve all categories.
- **GET** `/categories/:id`: Retrieve a specific category by ID, including its items.
- **POST** `/categories`: Add a new category.
  - **Body**: `{ category_name }`
- **PUT** `/categories/:id`: Update a category by ID.
  - **Body**: `{ category_name }`
- **DELETE** `/categories/:id`: Delete a category by ID.

### Item Routes (Admin Role Required)

- **GET** `/items`: Retrieve all items.
- **GET** `/items/:id`: Retrieve a specific item by ID.
- **POST** `/items`: Add a new item.
  - **Body**: `{ item_name, item_description, item_price, category_id }`
- **PUT** `/items/:id`: Update an item by ID.
  - **Body**: `{ item_name, item_description, item_price, category_id }`
- **DELETE** `/items/:id`: Delete an item by ID.

### Formula Routes (Admin Role Required)

- **GET** `/formulas`: Retrieve all formulas.
- **GET** `/formulas/:id`: Retrieve a specific formula by ID, including linked categories and items.
- **POST** `/formulas`: Add a new formula with associated categories.
  - **Body**: `{ formula_name, formula_price, category_ids }`
- **DELETE** `/formulas/:id`: Delete a formula by ID.

### Test Route

- **GET** `/test`: Check the server’s health.

---

## Testing the API

To test the API endpoints, use the provided `Restaurant_API.postman_collection.json` file with [Postman](https://www.postman.com/). Import the collection and configure the required environment variables to match those in `.env`.

---

## Technologies Used

- **Node.js & Express**: Server and API framework.
- **MySQL**: Database solution for storing user, category, item, and formula data.
- **Docker**: For containerized deployment.
- **Postman**: For testing API endpoints.



