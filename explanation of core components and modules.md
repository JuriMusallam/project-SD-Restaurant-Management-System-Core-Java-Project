## This document provides a detailed explanation of the core components and modules of the Restaurant Management System Java project, based on its file structure.

### 1. Controller.java
This file contains the main logic of the restaurant management system. Its responsibilities include:

- Managing user interactions (commands and inputs).
- Invoking methods from other classes like MenuItem, Order, and Employee to perform operations such as creating orders, managing employees, and handling payments.
- Acting as an intermediary between the database and the user interface (GUI or command-line).

Key Functions:

- Handling user actions (e.g., adding or removing menu items).
- Processing orders and interacting with the database.
- Responding to GUI interactions (if using `Controller_GUI.java`).

### 2. Controller_GUI.java
This file is responsible for handling the graphical user interface (GUI). It likely uses Java Swing or other GUI frameworks to create a user-friendly interface. Responsibilities include:

- Displaying the restaurant menu, orders, and employee data.
- Managing user inputs through buttons, text fields, and menus.
- Handling events like button clicks, item selections, and form submissions.

Key Components:

- Java Swing components (e.g., JFrame, JButton, JTextField, `JTable`).
- Event handling mechanisms to respond to user actions (e.g., ActionListener for button clicks).

### 3. Database.java
This module handles all database interactions, such as:

- Connecting to a database (possibly using JDBC for relational databases).
- Managing CRUD (Create, Read, Update, Delete) operations for entities like Employee, MenuItem, and Order.
- Querying and updating data in the restaurant’s database tables.
- Ensuring safe transaction handling (committing and rolling back transactions when necessary).

Key Functions:

- connect(): Opens a connection to the database.
- close(): Closes the connection.
- executeQuery(): Runs SELECT statements.
- executeUpdate(): Runs INSERT, UPDATE, and DELETE statements.

### 4. DatabaseException.java
This file defines custom exceptions for database operations, allowing the system to handle errors gracefully when interacting with the database.

Key Responsibilities:

- Handling exceptions (e.g., failed connections, query issues).
- Logging error messages and optionally rolling back transactions to avoid data corruption.

### 5. Employee.java
This class represents an employee in the restaurant, containing:

- Attributes like id, name, position, salary, and workingHours.
- Methods for getting and setting employee details (e.g., getName(), `setSalary()`).
- Functionality specific to different employee roles (e.g., waiter, chef, cashier).

Key Functions:

- Methods to add, remove, or update employee details.
- Role-specific methods for defining actions employees can perform.

### 6. Manager.java
This class focuses on managerial roles and may extend or work with Employee.java. Responsibilities include:

- Viewing all orders and employees.
- Adding or modifying menu items.
- Generating reports on sales, inventory, or employee performance.

Key Functions:

- Methods to hire or fire employees.
- Adjusting menu prices and promotions.
- Tracking inventory levels and ordering stock.

### 7. MenuItem.java
This class represents a menu item in the restaurant system, containing attributes such as:

- name: The name of the item (e.g., “Burger”).
- price: The cost of the item.
- category: The type of item (e.g., drinks, mains, desserts).
- availability: A flag indicating whether the item is currently available.

Key Methods:

- Methods to add, remove, or update menu items.
- Displaying available items to customers.
- Managing item availability based on stock or sales.

### 8. Order.java
This class represents an order placed by a customer, containing attributes like:

- orderId: Unique ID for the order.
- items: A list of MenuItem objects associated with the order.
- totalPrice: The total cost of the order.
- status: Order status (e.g., “Pending”, “Served”, “Paid”).

Key Functions:

- Adding or removing items from the order.
- Calculating the total price based on menu items and quantities.
- Updating the order status (e.g., marking it as completed when paid).

### 9. OrderDetail.java
This class contains details of each item in an order, tracking:

- item: The specific MenuItem ordered.
- quantity: How many of that item were ordered.
- price: The price of that item (possibly including discounts).

Key Functions:

- Managing individual components of an order.
- Providing an itemized breakdown for receipts or invoices.

## Likely Workflow of the System

1. User Interaction: The user (e.g., a cashier or waiter) interacts with the system through the GUI managed by Controller_GUI.java.
2. Controller Logic: User actions trigger methods in Controller.java, performing operations like adding an order or updating employee details.
3. Database Access: Controller.java interacts with Database.java to persist data to the restaurant’s database.
4. Data Handling: Objects like MenuItem, Order, Employee, and Manager represent different entities, with their methods handling data manipulation and business logic.
5. Error Handling: If database issues arise, custom exceptions in DatabaseException.java ensure graceful error handling, logging issues or notifying the user.
