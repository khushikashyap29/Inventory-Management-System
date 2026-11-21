# Inventory and Data Management System

A RESTful Inventory Management System built using **Node.js, Express.js, MongoDB, and Mongoose**. This application helps manage product records, track stock levels, perform inventory operations, and generate inventory reports.

## 1. Project Overview

The Inventory and Data Management System is designed to manage product information and inventory efficiently through RESTful APIs.

It supports product creation, retrieval, updating, deletion, stock adjustments, filtering, sorting, pagination, and inventory reports using MongoDB aggregation.

## 2. Technologies Used

- **Node.js** – JavaScript runtime environment
- **Express.js** – Backend web framework
- **MongoDB** – NoSQL database
- **Mongoose** – MongoDB object modeling tool
- **dotenv** – Environment variable management
- **Postman** – API testing

## 3. Features

### Product Management (CRUD)
- Create new products.
- Retrieve all products.
- Retrieve a single product using its ID.
- Update existing product details.
- Delete products.

### Inventory Management
- Increase product stock through restocking.
- Decrease product stock through sales.
- Prevent stock from becoming negative.
- Generate low-stock alerts based on reorder levels.

### Advanced Product Querying
- Filter products by category.
- Filter products by minimum and maximum price.
- Sort products by name, price, quantity, and creation date.
- Implement pagination using page and limit parameters.

### Inventory Reports
- Generate low-stock reports.
- Generate category-wise inventory summaries.
- Calculate total products, total quantity, total stock value, and average price using MongoDB aggregation.

### Validation and Error Handling
- Mongoose schema-level validation.
- Custom input validation middleware.
- Centralized error handling.
- Duplicate SKU handling.
- Invalid product ID handling.

## 4. Project Folder Structure

```text
Inventory Management System/
│
├── config/
│   └── db.js
│
├── middleware/
│   ├── errorMiddleware.js
│   └── validateProduct.js
│
├── models/
│   └── Product.js
│
├── routes/
│   └── productRoutes.js
│
├── .env
├── .gitignore
├── package.json
├── package-lock.json
├── server.js
└── README.md
```

## 5. Installation and Setup

### Step 1: Clone or Download the Project

Download the project and open its folder in Visual Studio Code.

### Step 2: Install Dependencies

Run the following command in the terminal:

```bash
npm install
```

Required packages:

```bash
npm install express mongoose dotenv
```

### Step 3: Configure Environment Variables

Create a `.env` file in the root directory.

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/InventoryDB
```

### Step 4: Start MongoDB

Make sure MongoDB is installed and the MongoDB server is running locally.

### Step 5: Start the Application

```bash
node server.js
```

Expected terminal output:

```text
MongoDB Connected Successfully!
Server is running on port 5000
```

The application will run at:

```text
http://localhost:5000
```

## 6. Product Schema

The Product model contains the following fields:

| Field | Description |
|---|---|
| name | Product name |
| sku | Unique product identification code |
| category | Product category |
| price | Product price |
| quantity | Available stock quantity |
| reorderLevel | Minimum stock level |
| supplier | Supplier name |

The schema also uses Mongoose timestamps to maintain product creation and update dates.

## 7. API Endpoints

Base URL:

```text
http://localhost:5000/api/products
```

| Method | Endpoint | Description |
|---|---|---|
| POST | `/` | Create a product |
| GET | `/` | Get all products |
| GET | `/:id` | Get product by ID |
| PUT | `/:id` | Update product |
| DELETE | `/:id` | Delete product |
| PATCH | `/:id/stock` | Adjust product stock |
| PATCH | `/:id/restock` | Increase stock |
| PATCH | `/:id/sale` | Decrease stock |
| GET | `/low-stock` | Get low-stock products |
| GET | `/summary` | Get category-wise summary |

Additional report routes:

| Method | Endpoint | Description |
|---|---|---|
| GET | `/reports/low-stock` | Low-stock report |
| GET | `/reports/category-summary` | Category-wise summary |

## 8. API Request Examples

### A. Create Product

**POST** `/api/products`

```json
{
  "name": "Laptop",
  "sku": "LAP101",
  "category": "Electronics",
  "price": 55000,
  "quantity": 20,
  "reorderLevel": 5,
  "supplier": "Dell"
}
```

### B. Get All Products

**GET** `/api/products`

### C. Filtering, Sorting and Pagination

**GET** `/api/products?category=Electronics&sortBy=price&order=asc&page=1&limit=5`

### D. Get Single Product

**GET** `/api/products/PRODUCT_ID`

Replace `PRODUCT_ID` with an actual MongoDB product ID.

### E. Update Product

**PUT** `/api/products/PRODUCT_ID`

```json
{
  "name": "Dell Laptop Updated",
  "sku": "LAP101",
  "category": "Electronics",
  "price": 60000,
  "quantity": 25,
  "reorderLevel": 5,
  "supplier": "Dell India"
}
```

Use a unique SKU that is not already assigned to another product.

### F. Adjust Stock

**PATCH** `/api/products/PRODUCT_ID/stock`

```json
{
  "change": 10
}
```

A positive value increases stock, while a negative value decreases stock.

### G. Restock Product

**PATCH** `/api/products/PRODUCT_ID/restock`

```json
{
  "quantity": 10
}
```

### H. Record a Sale

**PATCH** `/api/products/PRODUCT_ID/sale`

```json
{
  "quantity": 5
}
```

### I. Low-Stock Report

**GET** `/api/products/low-stock`

Returns products whose available quantity is less than or equal to their reorder level.

### J. Category-wise Inventory Summary

**GET** `/api/products/summary`

Uses MongoDB aggregation to calculate category-wise inventory information.

### K. Delete Product

**DELETE** `/api/products/PRODUCT_ID`

Deletes a product using its MongoDB ID.

## 9. Database

Database Name:

```text
InventoryDB
```

Collection Name:

```text
products
```

MongoDB Compass can be used to view and manage the stored product documents.

## 10. Testing

All REST API endpoints can be tested using **Postman**.

The following operations are covered:

- Product creation and retrieval.
- Product updates and deletion.
- Filtering, sorting, and pagination.
- Stock adjustment and restocking.
- Low-stock report generation.
- Category-wise inventory aggregation.
- Input validation and error handling.

## 11. Learning Outcomes

Through this project, the following concepts were implemented:

- Mongoose schema design and field-level validation.
- RESTful API development using Express.js.
- CRUD operations with MongoDB.
- Query parameters and pagination.
- Filtering and sorting.
- MongoDB aggregation pipelines.
- Middleware implementation.
- Centralized error handling.
- Environment variable configuration using dotenv.

## 12. Conclusion

The Inventory and Data Management System provides a structured backend solution for managing product information and inventory operations. It demonstrates the practical implementation of Node.js, Express.js, MongoDB, and Mongoose concepts through RESTful APIs, validation, middleware, and aggregation.

**Project Status:** Developed as part of Web Development III – Assignment 3.