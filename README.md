# 📚 Bookstore SQL Project

## 📌 Project Overview
This project involves designing and analyzing a **Bookstore Database** using **PostgreSQL**. The goal is to manage book inventory, customer data, and order transactions efficiently. Key objectives include:
- Understanding customer purchase behavior
- Identifying best-selling books
- Analyzing revenue and sales trends

## 🗄 Database Schema
The project consists of **three tables**:

1. **Customers** (Stores customer details)
   - `customer_id` (Primary Key)
   - `name`
   - `email`
   - `phone`
   - `address`

2. **Books** (Stores book information)
   - `book_id` (Primary Key)
   - `title`
   - `author`
   - `genre`
   - `price`
   - `stock_quantity`

3. **Orders** (Stores order transactions)
   - `order_id` (Primary Key)
   - `customer_id` (Foreign Key → Customers)
   - `book_id` (Foreign Key → Books)
   - `order_date`
   - `quantity`
   - `total_price`

## 🛠 SQL Queries & Analysis
The project includes key SQL queries such as:

- 📌 **Retrieve all books in the "Fiction" genre**:
  ```sql
  SELECT * FROM Books WHERE genre = 'Fiction';
  ```

- 📌 **Find books published after the year 1950**:
  ```sql
  SELECT * FROM Books WHERE EXTRACT(YEAR FROM order_date) > 1950;
  ```

- 📌 **List all customers from Canada**:
  ```sql
  SELECT * FROM Customers WHERE address LIKE '%Canada%';
  ```

- 📌 **Show orders placed in November 2023**:
  ```sql
  SELECT * FROM Orders WHERE order_date BETWEEN '2023-11-01' AND '2023-11-30';
  ```

- 📌 **Retrieve the total stock of books available**:
  ```sql
  SELECT SUM(stock_quantity) AS total_stock FROM Books;
  ```

- 📌 **Find the details of the most expensive book**:
  ```sql
  SELECT * FROM Books ORDER BY price DESC LIMIT 1;
  ```

- 📌 **Show all customers who ordered more than 1 quantity of a book**:
  ```sql
  SELECT customer_id, COUNT(*) AS order_count FROM Orders GROUP BY customer_id HAVING COUNT(*) > 1;
  ```

- 📌 **Retrieve all orders where the total amount exceeds $20**:
  ```sql
  SELECT * FROM Orders WHERE total_price > 20;
  ```

- 📌 **Find the book with the lowest stock**:
  ```sql
  SELECT * FROM Books ORDER BY stock_quantity ASC LIMIT 1;
  ```

- 📌 **Calculate the total revenue generated from all orders**:
  ```sql
  SELECT SUM(total_price) AS total_revenue FROM Orders;
  ```

- 📌 **Retrieve the total number of books sold for each genre**:
  ```sql
  SELECT genre, SUM(quantity) AS total_sold FROM Orders JOIN Books ON Orders.book_id = Books.book_id GROUP BY genre;
  ```

- 📌 **Find the average price of books in the "Fantasy" genre**:
  ```sql
  SELECT AVG(price) AS avg_price FROM Books WHERE genre = 'Fantasy';
  ```

- 📌 **List customers who have placed at least 2 orders**:
  ```sql
  SELECT customer_id, COUNT(order_id) AS total_orders FROM Orders GROUP BY customer_id HAVING COUNT(order_id) >= 2;
  ```

- 📌 **Show the top 3 most expensive books of 'Fantasy' Genre**:
  ```sql
  SELECT * FROM Books WHERE genre = 'Fantasy' ORDER BY price DESC LIMIT 3;
  ```

- 📌 **Retrieve the total quantity of books sold by each author**:
  ```sql
  SELECT author, SUM(quantity) AS total_sold FROM Books JOIN Orders ON Books.book_id = Orders.book_id GROUP BY author;
  ```

- 📌 **List the cities where customers who spent over $30 are located**:
  ```sql
  SELECT DISTINCT address FROM Customers JOIN Orders ON Customers.customer_id = Orders.customer_id WHERE total_price > 30;
  ```

- 📌 **Find the customer who spent the most on orders**:
  ```sql
  SELECT customer_id, SUM(total_price) AS total_spent FROM Orders GROUP BY customer_id ORDER BY total_spent DESC LIMIT 1;
  ```

- 📌 **Calculate the stock remaining after fulfilling all orders**:
  ```sql
  SELECT title, stock_quantity - COALESCE(SUM(quantity), 0) AS remaining_stock FROM Books LEFT JOIN Orders ON Books.book_id = Orders.book_id GROUP BY title, stock_quantity;
  ```

## 📊 Insights & Findings
- **Fiction and Fantasy books** are the most popular genres.
- **Customers from Canada** contribute significantly to bookstore sales.
- The **most expensive book** costs **$120**, and the cheapest is **$15**.
- **Total revenue generated** from all orders is **$8,450**.
- **Customers who place multiple orders** are more likely to buy high-priced books.
- **Low stock warning**: Some books have less than **3 copies** available.
- **Authors with the highest sales** are primarily from the Fantasy and Self-Help genres.
- Customers who spent **over $30** are concentrated in specific cities.
- **Stock levels need optimization** based on customer demand trends.


## ✨ Connect with Me
📩 Email: bariv219@gmail.com  
💼 LinkedIn: http://linkedin.com/in/vaibhav-bari-915bb5202

