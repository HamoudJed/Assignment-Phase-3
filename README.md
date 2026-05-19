# Assignment 3 - PHP Product Management System

## 📋 Project Overview
This is a complete PHP CRUD (Create, Read, Update, Delete) application for managing products. The application uses SQLite database and includes a REST API endpoint.

## ✨ Features
- ✅ View all products in a table format
- ✅ Add new products with name and price
- ✅ Edit existing product details
- ✅ Delete products with confirmation
- ✅ JSON API endpoint for retrieving all products

## 🛠️ Technologies Used
- **PHP** - Server-side scripting
- **SQLite** - Embedded database
- **PDO** - Database abstraction layer
- **Bootstrap 5** - Frontend styling
- **HTML5** - Structure

## 📁 Project Structure
```
assignment3/
│
├── index.php           # Main page - displays all products
├── create.php          # Add new product form
├── edit.php            # Edit existing product form
├── delete.php          # Delete product handler
├── api.php             # JSON API endpoint
├── db.php              # Database connection configuration
├── sample_products.db  # SQLite database file
└── README.md           # This file
```

## 🚀 Installation & Setup

### Prerequisites
- PHP 7.4 or higher
- A local server (XAMPP, WAMP, MAMP) or PHP built-in server

### Steps to Run

1. **Download/Clone the project**
   ```bash
   git clone <your-github-repo-url>
   cd assignment3
   ```

2. **Run with PHP built-in server**
   ```bash
   php -S localhost:8000
   ```

3. **Or use XAMPP/WAMP**
   - Place the project folder in `htdocs` (XAMPP) or `www` (WAMP)
   - Access via: `http://localhost/assignment3/`

4. **Open in browser**
   ```
   http://localhost:8000/index.php
   ```

## 📝 Completed TODO Tasks

### 1. index.php (Line 24)
**Task:** Display actual product price  
**Solution:** Replaced `'DISPLAY PRICE HERE'` with `\${$row['price']}`

### 2. create.php (Line 7)
**Task:** Handle form submission and insert new product  
**Solution:** 
```php
$name = $_POST['name'];
$price = $_POST['price'];

$stmt = $pdo->prepare("INSERT INTO products (name, price) VALUES (:name, :price)");
$stmt->bindParam(':name', $name, PDO::PARAM_STR);
$stmt->bindParam(':price', $price);
$stmt->execute();
```

### 3. edit.php (Line 14)
**Task:** Handle form submission and update product  
**Solution:**
```php
$name = $_POST['name'];
$price = $_POST['price'];

$stmt = $pdo->prepare("UPDATE products SET name = :name, price = :price WHERE id = :id");
$stmt->bindParam(':name', $name, PDO::PARAM_STR);
$stmt->bindParam(':price', $price);
$stmt->bindParam(':id', $id, PDO::PARAM_INT);
$stmt->execute();
```

### 4. delete.php (Line 6)
**Task:** Handle product deletion  
**Solution:**
```php
$id = $_GET['id'];

$stmt = $pdo->prepare("DELETE FROM products WHERE id = :id");
$stmt->bindParam(':id', $id, PDO::PARAM_INT);
$stmt->execute();
```

### 5. api.php (Line 9)
**Task:** Fetch all products and return as JSON  
**Solution:**
```php
$stmt = $pdo->query("SELECT * FROM products");
$products = $stmt->fetchAll(PDO::FETCH_ASSOC);

echo json_encode([
    'status' => 'success',
    'data' => $products
]);
```

## 🌐 API Endpoint

### Get All Products
**URL:** `http://localhost:8000/api.php`  
**Method:** GET  
**Response Format:**
```json
{
    "status": "success",
    "data": [
        {
            "id": 1,
            "name": "Product Name",
            "price": 10.99
        }
    ]
}
```

## 🧪 Testing Instructions

1. **Test View Products**
   - Open `index.php`
   - Verify all products display with correct prices

2. **Test Create Product**
   - Click "Add Product" button
   - Fill in name and price
   - Verify product appears in the list

3. **Test Edit Product**
   - Click "Edit" button on any product
   - Modify details
   - Verify changes are saved

4. **Test Delete Product**
   - Click "Delete" button
   - Confirm deletion
   - Verify product is removed

5. **Test API**
   - Access `api.php` in browser
   - Verify JSON response format

## 🔒 Security Features
- ✅ Prepared statements (PDO) to prevent SQL injection
- ✅ Parameter binding for database queries
- ✅ HTML special characters escaping
- ✅ Confirmation dialog before deletion

## 📚 Database Schema

### Products Table
| Column | Type    | Description        |
|--------|---------|-------------------|
| id     | INTEGER | Primary Key (Auto) |
| name   | TEXT    | Product name      |
| price  | REAL    | Product price     |

## 👨‍💻 Author
**Student ID:** [Your ID]  
**Course:** CPIT-405 (Internet Applications)  
**Semester:** Spring 2026  
**University:** King Abdulaziz University

## 📄 License
This project is created for educational purposes as part of the CPIT-405 course assignment.

## 🙏 Acknowledgments
- King Abdulaziz University - Faculty of Computing & Information Technology
- Bootstrap for UI components
- PHP Documentation

---
**Note:** Make sure to include this GitHub repository link in your portfolio website's "My Works" page.
