# E-Commerce Inventory Management System

## Project Description

The **E-Commerce Inventory Management System** is a database project developed using MySQL to manage products, categories, suppliers, customers, orders, and stock movements.

The project helps track product availability, manage inventory levels, process order items, identify low-stock products, and generate sales reports. It uses SQL features such as stored procedures, triggers, views, indexes, and constraints to manage inventory operations efficiently.

## Technologies Used

- **Database:** MySQL 8.0+
- **Language:** SQL
- **Tool:** MySQL Workbench

## Features

- Manage product and category information.
- Store supplier and customer details.
- Track product prices and available stock.
- Manage customer orders and order items.
- Automatically update stock after adding order items.
- Record stock movements and sales.
- Identify low-stock and out-of-stock products.
- Search products by name.
- Add stock using stored procedures.
- Generate order summaries and sales reports.
- Use database constraints to maintain data integrity.

## Database Structure

The project contains seven main tables:

| Table | Description |
|---|---|
| `categories` | Stores product categories. |
| `suppliers` | Stores supplier details. |
| `products` | Stores product information, prices, and stock quantities. |
| `customers` | Stores customer information. |
| `orders` | Stores customer order details and status. |
| `order_items` | Stores products included in each order. |
| `stock_movements` | Records stock additions, sales, returns, and adjustments. |

## Database Objects

### Stored Procedures
- `add_stock` – Adds stock to an existing product.
- `place_order_item` – Adds a product to an order after checking availability.
- `search_products` – Searches active products by name.

### Triggers
- `trg_order_item_after_insert` – Updates stock quantity and order total when an order item is inserted.
- `trg_order_item_after_delete` – Restores stock and adjusts the order total when an order item is deleted.

### Views
- `product_inventory` – Displays product details and stock status.
- `low_stock_products` – Displays products at or below their reorder level.
- `order_summary` – Displays order details with customer information.
- `sales_by_product` – Summarizes units sold and sales amounts by product.

### Indexes and Constraints
- Primary and foreign keys.
- Unique constraints for product SKUs and customer emails.
- Check constraints for prices, quantities, and stock levels.
- Indexes to improve search and reporting performance.

## Repository Structure

```text
E-Commerce-Inventory-System/
├── ecommerce_inventory.sql
└── README.md
```

## Installation and Setup

### Step 1: Install MySQL

Install MySQL Server 8.0 or a compatible version and MySQL Workbench.

### Step 2: Download the Repository

Clone the GitHub repository:

```bash
git clone <your-github-repository-url>
```

Alternatively, download the repository as a ZIP file.

### Step 3: Open the SQL File

Open `ecommerce_inventory.sql` in MySQL Workbench.

### Step 4: Execute the SQL Script

Run the complete script to create the database, tables, sample records, triggers, stored procedures, views, and indexes.

The script creates or reuses the `ecommerce_inventory` database and drops and recreates its project tables and related database objects.

**Important:** Back up any existing project data before running the script because the existing tables and their data may be deleted.

## Example SQL Queries

### 1. Display Product Inventory

```sql
USE ecommerce_inventory;

SELECT * FROM product_inventory;
```

### 2. Display Low-Stock Products

```sql
SELECT * FROM low_stock_products;
```

### 3. Display Order Summary

```sql
SELECT *
FROM order_summary
ORDER BY order_date DESC;
```

### 4. Display Sales by Product

```sql
SELECT *
FROM sales_by_product
ORDER BY total_sales DESC;
```

### 5. Calculate Total Inventory Value

```sql
SELECT SUM(unit_price * stock_quantity) AS inventory_value
FROM products;
```

### 6. Search for Products

```sql
CALL search_products('Java');
```

### 7. Add Stock to a Product

```sql
CALL add_stock(1, 10, 'Restock from supplier');
```

This adds 10 units to the product with ID 1 and records the stock movement.

### 8. Add a Product to an Order

```sql
CALL place_order_item(3, 1, 1);
```

This adds one unit of product ID 1 to order ID 3 if the product is active, sufficient stock is available, and the order is not cancelled.

## Learning Outcomes

- Understanding relational database design.
- Creating tables and relationships using SQL.
- Using joins, aggregate functions, and views.
- Implementing stored procedures and triggers.
- Tracking inventory and stock movements.
- Managing order details and calculating sales.
- Applying constraints and indexes.
- Writing queries for inventory reports and business analysis.

## Future Enhancements

- Develop a web interface for administrators and customers.
- Add user authentication and role-based access.
- Generate downloadable inventory and sales reports.
- Add supplier purchase-order management.
- Implement order cancellation and refund workflows.
- Add automatic low-stock notifications.
- Create dashboards for sales and inventory analysis.

## Conclusion

The E-Commerce Inventory Management System demonstrates how MySQL can be used to manage inventory, customer orders, suppliers, and sales records. It provides a foundation for developing a complete inventory management application with a frontend and backend.

## Author Details
- **Name:** KURUBA CHANDRAMOULI 
- **Domain:** SQL
- **Internship ID:** CITS9354
