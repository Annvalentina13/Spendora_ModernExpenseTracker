# ✨ Smart Expense Tracker: Modern Desktop Finance App

**(Java Swing | FlatLaf | MySQL | JFreeChart)**

A secure, responsive, and visually appealing personal finance tracking application built with **Java Swing**. This project demonstrates best practices in modern desktop development by integrating real-time budget monitoring, powerful data visualization, asynchronous processing, and advanced UI fixes.

## 🌟 Key Features

* **Secure Authentication:** User accounts managed with **SHA-256 password hashing**.
* **Asynchronous Performance:** Uses **`SwingWorker`** to offload all database operations to background threads, ensuring the UI remains **responsive and non-blocking**.
* **Real-Time Budget Tracking:** Users set monthly limits. The app provides instant visual feedback using a custom **color-coded renderer** (Green/Orange/Red) to indicate budget status.
* **Data Visualization:** Integrates **JFreeChart** to display financial health with Pie Charts (spending distribution) and Bar Charts (category comparison).
* **Modern UI & Theming:** Utilizes **FlatLaf** for a contemporary look, featuring rounded components and a **Dark/Light theme toggle**.
* **Professional Reporting:** Export complete expense history to **CSV** and structured **PDF** reports (using iTextPDF).

## 🛠️ Technology Stack

| Category | Technology | Purpose |
| :--- | :--- | :--- |
| **Frontend/UI** | **Java Swing, FlatLaf** | Core desktop framework and modern Look and Feel. |
| **Backend Logic** | **Java, `SwingWorker`** | Business logic, calculations, and performance. |
| **Database** | **MySQL (via JDBC)** | Secure and persistent data storage. |
| **Visualization** | **JFreeChart** | Generating dynamic charts. |

---

## 📐 Technical Achievements

This project specifically focused on solving complex architectural and rendering problems:

1.  **Fixed UI Rendering Glitches:** Resolved issues like **JTable transparency artifacts** and **navigation button ghosting** by implementing custom cell renderers and opaque styling.
2.  **Efficient Data Management:** Implemented budget control using the **SQL `ON DUPLICATE KEY UPDATE`** clause for efficient creation and modification.
3.  **Tiered Architecture:** Maintained clear separation between the Presentation, Application, and Data tiers using JDBC and `SwingWorker`.

---

## 🚀 Setup and Run

### Prerequisites
* Java Development Kit (JDK) 11+
* MySQL Server running

### 1. Database Setup
1.  Create a new database named: `expense_tracker_modern_db`
2.  Run the following SQL script to create the necessary tables:

```sql
-- SQL to create the required tables

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password_hash VARCHAR(64) NOT NULL
);

CREATE TABLE expenses (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    amount DOUBLE NOT NULL,
    category VARCHAR(100),
    note VARCHAR(255),
    expense_date DATE NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE budgets (
    user_id INT,
    category VARCHAR(100),
    limit_amount DOUBLE NOT NULL,
    PRIMARY KEY (user_id, category),
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```
### 2. Configure Credentials
* Open the ModernExpenseTracker.java file.
* Update the connectToDatabase() method with your local MySQL credentials:

```
// In ModernExpenseTracker.java
String pass = "YOUR_MYSQL_PASSWORD"; // ⚠️ IMPORTANT: Replace this value!
```

### 3. Build and Run
* Ensure all necessary external JAR files (MySQL Connector, FlatLaf, JFreeChart, iTextPDF) are included in your project's classpath.
* Compile and run the ModernExpenseTracker.java class.
* Use the Register function to create a new user account and begin tracking.
---

### 🤝 Contribution
Developed by Annie Valentina A.

