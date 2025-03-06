## SQL Queries

The following queries are included in this project:

* **Retrieve all customers who have placed an order in the last 30 days:**

    ```sql
    SELECT c.*
    FROM customers c
    JOIN orders o ON c.id = o.customer_id
    WHERE o.order_date >= DATE_SUB(CURDATE(), INTERVAL 30 DAY);
    ```

* **Get the total amount of all orders placed by each customer:**

    ```sql
    SELECT c.name, SUM(o.total_amount) AS total_order_amount
    FROM customers c
    LEFT JOIN orders o ON c.id = o.customer_id
    GROUP BY c.id, c.name;
    ```

* **Update the price of Product C to 45.00:**

    ```sql
    UPDATE products SET price = 45.00 WHERE name = 'Product C';
    ```

* **Add a new column discount to the products table:**

    ```sql
    ALTER TABLE products ADD COLUMN discount DECIMAL(5, 2);
    ```

* **Retrieve the top 3 products with the highest price:**

    ```sql
    SELECT * FROM products ORDER BY price DESC LIMIT 3;
    ```

* **Get the names of customers who have ordered Product A:**

    ```sql
    SELECT DISTINCT c.name
    FROM customers c
    JOIN orders o ON c.id = o.customer_id
    JOIN order_items oi ON o.id = oi.order_id
    JOIN products p ON oi.product_id = p.id
    WHERE p.name = 'Product A';
    ```

* **Join the orders and customers tables to retrieve the customer's name and order date for each order:**

    ```sql
    SELECT c.name, o.order_date
    FROM customers c
    JOIN orders o ON c.id = o.customer_id;
    ```

* **Retrieve the orders with a total amount greater than 150.00:**

    ```sql
    SELECT * FROM orders WHERE total_amount > 150.00;
    ```

* **Normalize the database by creating a separate table for order items and updating the orders table to reference the order_items table:**
    * The `order_items` table is created and populated.
    * The `orders` table is updated to calculate `total_amount` based on `order_items`.

* **Retrieve the average total of all orders:**

    ```sql
    SELECT AVG(total_amount) AS average_order_total
    FROM orders;
    ```
    ![alt image](https://github.com/abarna-RP/mysql-task/blob/main/output%20mysql.png)
