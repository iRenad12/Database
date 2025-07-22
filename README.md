# 📋 Renad - Simple PHP Form with MySQL

This project is a basic web application that allows users to input their **name** and **age** through an HTML form. Once submitted, the data is sent to a PHP script and saved into a MySQL database.

---

## 🌟 Features

- Simple HTML form to collect user data.
- PHP backend to process and store data.
- Data is inserted into a MySQL database table.
- Confirmation message after successful insertion.

---

## 🧰 Technologies Used

- HTML
- PHP (using MySQLi)
- MySQL
- XAMPP/MAMP (for local development)

---

## 🗂️ Project Files

```
renad/
├── index.html     # HTML form to collect name and age
├── x.php          # PHP script to handle form submission and insert data
└── README.md      # This documentation file
```

---

## 🗃️ Database Setup

You need to create a MySQL database and table before running the project.

### 🔧 SQL Commands:

```sql
CREATE DATABASE renad;

USE renad;

CREATE TABLE renadt (
  id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  age INT
);
```

---

## 🚀 How to Run the Project

1. Download and install **XAMPP** or **MAMP**.
2. Start **Apache** and **MySQL** from the control panel.
3. Open **phpMyAdmin** and run the SQL commands above to create the database and table.
4. Place the project folder `renad/` inside the `htdocs` directory (usually found in `C:\xampp\htdocs\`).
5. Open your browser and go to:
   ```
   http://localhost/renad/index.html
   ```
6. Fill in your name and age, then click "Submit".
7. You should see a success message and the data saved in your database.

---

## 💻 Code Summary

### `index.html`

```html
<form action="x.php" method="get">
  <label for="name">name:</label><br>
  <input type="text" id="name" name="name"><br>

  <label for="age">age:</label><br>
  <input type="text" id="age" name="age"><br><br>

  <input type="submit" value="Submit">
</form>
```

### `x.php`

```php
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "renad";

$name = $_GET["name"];
$age = $_GET["age"];

echo $name . "<br>";
echo $age . "<br>";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);
}

$sql = "INSERT INTO renadt (name, age) VALUES ('$name', '$age')";

if ($conn->query($sql) === TRUE) {
  echo "New record created successfully";
} else {
  echo "Error: " . $sql . "<br>" . $conn->error;
}

$conn->close();
?>
```

---

## ⚠️ Troubleshooting

- ❌ **Incorrect integer value: '' for column `renad`.`renadt`.`id`**
  
  ✅ Make sure the `id` column is defined as `AUTO_INCREMENT`.

- ❌ **Connection failed**
  
  ✅ Ensure your MySQL server is running and the database credentials are correct.

---

## 📄 License

This project is open-source and free to use for educational purposes.
