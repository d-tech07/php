# Complete PHP & MySQL Server-Side Programming Notes

## Table of Contents
1. [Introduction to Server-Side Programming](#introduction)
2. [Web Server & PHP](#web-server--php)
3. [PHP Basic Syntax](#php-basic-syntax)
4. [PHP File Structure](#php-file-structure)
5. [Operators](#operators)
6. [Conditional Statements](#conditional-statements)
7. [Arrays](#arrays)
8. [Functions](#functions)
9. [Loops](#loops)
10. [Database (MySQL)](#database-mysql)
11. [Database Configuration](#database-configuration)
12. [Database Operations](#database-operations)
13. [CRUD Operations with HTML & PHP](#crud-operations)

---

## Introduction to Server-Side Programming

**Server-side programming** refers to code that runs on the web server rather than in the user's browser. When a user requests a web page, the server processes the server-side code and sends the resulting HTML to the client's browser.

### Key Characteristics:
- Code executes on the server
- Can interact with databases
- Can generate dynamic content
- Handles user authentication and sessions
- Processes form data
- Can access server resources

### Popular Server-Side Languages:
- PHP
- Python (Django, Flask)
- Node.js (JavaScript)
- Java (Spring)
- C# (.NET)
- Ruby (Ruby on Rails)

---

## Web Server & PHP

### What is a Web Server?
A web server is software that serves web pages to clients (browsers) over HTTP/HTTPS protocols.

### Popular Web Servers:
- **Apache HTTP Server** (most common with PHP)
- **Nginx**
- **Microsoft IIS**
- **LiteSpeed**

### PHP Overview
PHP (PHP: Hypertext Preprocessor) is a server-side scripting language designed for web development.

### PHP Features:
- Open source and free
- Cross-platform (Windows, Linux, macOS)
- Supports multiple databases
- Large community and extensive documentation
- Easy to learn and use
- Embedded in HTML

### PHP Installation Requirements:
- Web server (Apache/Nginx)
- PHP interpreter
- Database server (MySQL/PostgreSQL)
- Popular packages: XAMPP, WAMP, MAMP, LAMP

---

## PHP Basic Syntax

### PHP Tags
PHP code is embedded within HTML using special tags:

```php
<?php
// PHP code goes here
?>

<!-- Short tags (not recommended) -->
<? echo "Hello World"; ?>

<!-- Echo tags -->
<?= "Hello World" ?>
```

### Comments
```php
<?php
// Single line comment

/* 
Multi-line comment
spanning multiple lines
*/

# Shell-style comment (single line)
?>
```

### Variables
```php
<?php
// Variable declaration
$name = "John Doe";
$age = 25;
$height = 5.9;
$is_student = true;

// Variable naming rules:
// - Start with $ sign
// - Begin with letter or underscore
// - Case sensitive
// - Cannot start with number
?>
```

### Data Types
```php
<?php
// String
$text = "Hello World";

// Integer
$number = 42;

// Float/Double
$decimal = 3.14;

// Boolean
$flag = true;

// Array
$colors = array("red", "green", "blue");

// Object
class Person {
    public $name;
}
$person = new Person();

// NULL
$empty = null;
?>
```

### Constants
```php
<?php
// Define constants
define("SITE_NAME", "My Website");
const API_KEY = "abc123";

echo SITE_NAME; // Output: My Website
?>
```

---

## PHP File Structure

### Basic File Structure
```php
<?php
// 1. PHP opening tag

// 2. Include/require statements
include 'config.php';
require 'functions.php';

// 3. Class definitions
class User {
    // Class properties and methods
}

// 4. Function definitions
function calculateTotal($price, $tax) {
    return $price + ($price * $tax);
}

// 5. Main execution code
$user = new User();
$total = calculateTotal(100, 0.1);

// 6. HTML output (if needed)
?>
<!DOCTYPE html>
<html>
<head>
    <title>PHP Page</title>
</head>
<body>
    <h1><?php echo $total; ?></h1>
</body>
</html>
```

### File Inclusion
```php
<?php
// include - continues execution if file not found
include 'header.php';

// require - stops execution if file not found
require 'database.php';

// include_once - includes file only once
include_once 'config.php';

// require_once - requires file only once
require_once 'functions.php';
?>
```

---

## Operators

### Arithmetic Operators
```php
<?php
$a = 10;
$b = 3;

echo $a + $b; // Addition: 13
echo $a - $b; // Subtraction: 7
echo $a * $b; // Multiplication: 30
echo $a / $b; // Division: 3.33...
echo $a % $b; // Modulus: 1
echo $a ** $b; // Exponentiation: 1000
?>
```

### Assignment Operators
```php
<?php
$x = 10;        // Assignment
$x += 5;        // $x = $x + 5 (15)
$x -= 3;        // $x = $x - 3 (12)
$x *= 2;        // $x = $x * 2 (24)
$x /= 4;        // $x = $x / 4 (6)
$x %= 5;        // $x = $x % 5 (1)
?>
```

### Comparison Operators
```php
<?php
$a = 5;
$b = "5";

var_dump($a == $b);  // true (equal value)
var_dump($a === $b); // false (identical type and value)
var_dump($a != $b);  // false (not equal)
var_dump($a !== $b); // true (not identical)
var_dump($a < $b);   // false
var_dump($a > $b);   // false
var_dump($a <= $b);  // true
var_dump($a >= $b);  // true
?>
```

### Logical Operators
```php
<?php
$x = true;
$y = false;

var_dump($x && $y); // AND: false
var_dump($x || $y); // OR: true
var_dump(!$x);      // NOT: false
var_dump($x and $y); // AND: false
var_dump($x or $y);  // OR: true
var_dump($x xor $y); // XOR: true
?>
```

### String Operators
```php
<?php
$first = "Hello";
$last = "World";

echo $first . " " . $last; // Concatenation: Hello World
$first .= " PHP";          // Concatenation assignment: Hello PHP
?>
```

---

## Conditional Statements

### if Statement
```php
<?php
$age = 18;

if ($age >= 18) {
    echo "You are an adult";
}
?>
```

### if...else Statement
```php
<?php
$score = 85;

if ($score >= 90) {
    echo "Grade: A";
} else {
    echo "Grade: B or lower";
}
?>
```

### if...elseif...else Statement
```php
<?php
$grade = 85;

if ($grade >= 90) {
    echo "Grade: A";
} elseif ($grade >= 80) {
    echo "Grade: B";
} elseif ($grade >= 70) {
    echo "Grade: C";
} elseif ($grade >= 60) {
    echo "Grade: D";
} else {
    echo "Grade: F";
}
?>
```

### Ternary Operator
```php
<?php
$age = 20;
$message = ($age >= 18) ? "Adult" : "Minor";
echo $message; // Output: Adult
?>
```

### switch Statement
```php
<?php
$day = "Monday";

switch ($day) {
    case "Monday":
        echo "Start of work week";
        break;
    case "Friday":
        echo "TGIF!";
        break;
    case "Saturday":
    case "Sunday":
        echo "Weekend!";
        break;
    default:
        echo "Regular day";
}
?>
```

---

## Arrays

### Indexed Arrays
```php
<?php
// Method 1
$fruits = array("apple", "banana", "orange");

// Method 2
$colors = ["red", "green", "blue"];

// Method 3
$numbers[0] = 10;
$numbers[1] = 20;
$numbers[2] = 30;

// Accessing elements
echo $fruits[0]; // apple
echo $colors[1]; // green
?>
```

### Associative Arrays
```php
<?php
// Method 1
$person = array(
    "name" => "John",
    "age" => 30,
    "city" => "New York"
);

// Method 2
$car = [
    "brand" => "Toyota",
    "model" => "Camry",
    "year" => 2020
];

// Accessing elements
echo $person["name"]; // John
echo $car["brand"];   // Toyota
?>
```

### Multidimensional Arrays
```php
<?php
$students = [
    [
        "name" => "Alice",
        "age" => 20,
        "grades" => [85, 90, 78]
    ],
    [
        "name" => "Bob",
        "age" => 22,
        "grades" => [92, 88, 95]
    ]
];

// Accessing elements
echo $students[0]["name"];      // Alice
echo $students[1]["grades"][0]; // 92
?>
```

### Array Functions
```php
<?php
$numbers = [1, 2, 3, 4, 5];

// Array length
echo count($numbers); // 5

// Add elements
array_push($numbers, 6);        // Add to end
array_unshift($numbers, 0);     // Add to beginning

// Remove elements
array_pop($numbers);            // Remove from end
array_shift($numbers);          // Remove from beginning

// Search and check
if (in_array(3, $numbers)) {
    echo "Found 3";
}

// Array keys and values
$person = ["name" => "John", "age" => 30];
$keys = array_keys($person);    // ["name", "age"]
$values = array_values($person); // ["John", 30]

// Sort arrays
sort($numbers);                 // Sort indexed array
asort($person);                 // Sort associative array by value
ksort($person);                 // Sort associative array by key
?>
```

---

## Functions

### Basic Function Syntax
```php
<?php
function functionName($parameter1, $parameter2) {
    // Function body
    return $result;
}

// Example
function greet($name) {
    return "Hello, " . $name . "!";
}

echo greet("John"); // Hello, John!
?>
```

### Function Parameters
```php
<?php
// Default parameters
function introduce($name, $age = 25) {
    return "My name is $name and I am $age years old.";
}

echo introduce("Alice");        // Uses default age
echo introduce("Bob", 30);      // Uses provided age

// Variable number of arguments
function sum(...$numbers) {
    $total = 0;
    foreach ($numbers as $number) {
        $total += $number;
    }
    return $total;
}

echo sum(1, 2, 3, 4, 5); // 15
?>
```

### Return Values
```php
<?php
// Return single value
function add($a, $b) {
    return $a + $b;
}

// Return multiple values (using array)
function calculate($a, $b) {
    return [
        'sum' => $a + $b,
        'difference' => $a - $b,
        'product' => $a * $b
    ];
}

$result = calculate(10, 5);
echo $result['sum']; // 15

// Return by reference
function &getReference(&$var) {
    return $var;
}
?>
```

### Built-in Functions
```php
<?php
// String functions
$text = "Hello World";
echo strlen($text);           // String length: 11
echo strtoupper($text);       // HELLO WORLD
echo strtolower($text);       // hello world
echo substr($text, 0, 5);     // Hello

// Math functions
echo abs(-5);                 // 5
echo ceil(4.3);              // 5
echo floor(4.7);             // 4
echo round(4.6);             // 5
echo max(1, 3, 2);           // 3
echo min(1, 3, 2);           // 1

// Date functions
echo date('Y-m-d');          // Current date
echo date('Y-m-d H:i:s');    // Current datetime
echo time();                 // Current timestamp
?>
```

---

## Loops

### for Loop
```php
<?php
for ($i = 1; $i <= 5; $i++) {
    echo "Number: $i<br>";
}

// Output:
// Number: 1
// Number: 2
// Number: 3
// Number: 4
// Number: 5
?>
```

### while Loop
```php
<?php
$i = 1;
while ($i <= 5) {
    echo "Count: $i<br>";
    $i++;
}

// Same output as for loop
?>
```

### do...while Loop
```php
<?php
$i = 1;
do {
    echo "Value: $i<br>";
    $i++;
} while ($i <= 5);

// Executes at least once
?>
```

### foreach Loop
```php
<?php
// For indexed arrays
$fruits = ["apple", "banana", "orange"];
foreach ($fruits as $fruit) {
    echo "Fruit: $fruit<br>";
}

// For associative arrays
$person = ["name" => "John", "age" => 30, "city" => "NYC"];
foreach ($person as $key => $value) {
    echo "$key: $value<br>";
}

// Output:
// name: John
// age: 30
// city: NYC
?>
```

### Loop Control
```php
<?php
// break - exit loop
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) {
        break; // Exit loop when $i equals 5
    }
    echo $i . " ";
}

// continue - skip iteration
for ($i = 1; $i <= 5; $i++) {
    if ($i == 3) {
        continue; // Skip when $i equals 3
    }
    echo $i . " "; // Output: 1 2 4 5
}
?>
```

---

## Database (MySQL)

### What is MySQL?
MySQL is a popular open-source relational database management system (RDBMS) that uses SQL (Structured Query Language).

### Key Features:
- Free and open source
- Cross-platform compatibility
- High performance and reliability
- ACID compliance
- Supports multiple storage engines
- Excellent PHP integration

### Basic Concepts:
- **Database**: Collection of related tables
- **Table**: Structure that holds data in rows and columns
- **Row/Record**: Individual entry in a table
- **Column/Field**: Attribute of a table
- **Primary Key**: Unique identifier for each row
- **Foreign Key**: Reference to primary key in another table

---

## Database Configuration

### Database Connection (MySQLi)
```php
<?php
// Database configuration
$servername = "localhost";
$username = "root";
$password = "";
$database = "myapp_db";

// Create connection
$conn = new mysqli($servername, $username, $password, $database);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
?>
```

### Database Connection (PDO)
```php
<?php
$servername = "localhost";
$username = "root";
$password = "";
$database = "myapp_db";

try {
    $pdo = new PDO("mysql:host=$servername;dbname=$database", $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Connected successfully";
} catch(PDOException $e) {
    die("Connection failed: " . $e->getMessage());
}
?>
```

### Configuration File (config.php)
```php
<?php
// config.php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');
define('DB_PASS', '');
define('DB_NAME', 'myapp_db');

function getDBConnection() {
    $conn = new mysqli(DB_HOST, DB_USER, DB_PASS, DB_NAME);
    
    if ($conn->connect_error) {
        die("Connection failed: " . $conn->connect_error);
    }
    
    return $conn;
}
?>
```

---

## Database Operations

### Create Database
```sql
CREATE DATABASE myapp_db;
```

```php
<?php
$conn = new mysqli("localhost", "root", "");

$sql = "CREATE DATABASE myapp_db";
if ($conn->query($sql) === TRUE) {
    echo "Database created successfully";
} else {
    echo "Error creating database: " . $conn->error;
}
?>
```

### Create Table
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    age INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

```php
<?php
$conn = new mysqli("localhost", "root", "", "myapp_db");

$sql = "CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    age INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)";

if ($conn->query($sql) === TRUE) {
    echo "Table created successfully";
} else {
    echo "Error creating table: " . $conn->error;
}
?>
```

### ALTER Operations
```sql
-- Add column
ALTER TABLE users ADD COLUMN phone VARCHAR(20);

-- Modify column
ALTER TABLE users MODIFY COLUMN name VARCHAR(150);

-- Drop column
ALTER TABLE users DROP COLUMN age;

-- Add index
ALTER TABLE users ADD INDEX idx_email (email);
```

```php
<?php
$conn = new mysqli("localhost", "root", "", "myapp_db");

// Add column
$sql = "ALTER TABLE users ADD COLUMN phone VARCHAR(20)";
$conn->query($sql);

// Modify column
$sql = "ALTER TABLE users MODIFY COLUMN name VARCHAR(150)";
$conn->query($sql);

// Drop column
$sql = "ALTER TABLE users DROP COLUMN age";
$conn->query($sql);
?>
```

### DROP Operations
```sql
-- Drop table
DROP TABLE users;

-- Drop database
DROP DATABASE myapp_db;
```

```php
<?php
$conn = new mysqli("localhost", "root", "", "myapp_db");

// Drop table
$sql = "DROP TABLE users";
if ($conn->query($sql) === TRUE) {
    echo "Table deleted successfully";
}

// Drop database
$sql = "DROP DATABASE myapp_db";
if ($conn->query($sql) === TRUE) {
    echo "Database deleted successfully";
}
?>
```

---

## CRUD Operations with HTML & PHP

### Database Setup
```php
<?php
// database.php
$servername = "localhost";
$username = "root";
$password = "";
$database = "crud_app";

$conn = new mysqli($servername, $username, $password, $database);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Create table if not exists
$sql = "CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    age INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)";
$conn->query($sql);
?>
```

### 1. CREATE - Add New Records

**add_user.html**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Add User</title>
</head>
<body>
    <h2>Add New User</h2>
    <form action="create_user.php" method="POST">
        <label>Name:</label>
        <input type="text" name="name" required><br><br>
        
        <label>Email:</label>
        <input type="email" name="email" required><br><br>
        
        <label>Age:</label>
        <input type="number" name="age" required><br><br>
        
        <input type="submit" value="Add User">
    </form>
    <a href="index.php">Back to List</a>
</body>
</html>
```

**create_user.php**
```php
<?php
include 'database.php';

if ($_POST) {
    $name = $_POST['name'];
    $email = $_POST['email'];
    $age = $_POST['age'];
    
    // Prepare and bind
    $stmt = $conn->prepare("INSERT INTO users (name, email, age) VALUES (?, ?, ?)");
    $stmt->bind_param("ssi", $name, $email, $age);
    
    if ($stmt->execute()) {
        echo "User added successfully!";
        echo "<a href='index.php'>View All Users</a>";
    } else {
        echo "Error: " . $stmt->error;
    }
    
    $stmt->close();
}

$conn->close();
?>
```

### 2. READ - Display Records

**index.php**
```php
<?php
include 'database.php';
?>

<!DOCTYPE html>
<html>
<head>
    <title>User Management</title>
    <style>
        table { border-collapse: collapse; width: 100%; }
        th, td { border: 1px solid #ddd; padding: 8px; text-align: left; }
        th { background-color: #f2f2f2; }
    </style>
</head>
<body>
    <h2>User Management System</h2>
    <a href="add_user.html">Add New User</a>
    
    <h3>All Users</h3>
    <table>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Email</th>
            <th>Age</th>
            <th>Created At</th>
            <th>Actions</th>
        </tr>
        
        <?php
        $sql = "SELECT * FROM users ORDER BY id DESC";
        $result = $conn->query($sql);
        
        if ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()) {
                echo "<tr>";
                echo "<td>" . $row["id"] . "</td>";
                echo "<td>" . $row["name"] . "</td>";
                echo "<td>" . $row["email"] . "</td>";
                echo "<td>" . $row["age"] . "</td>";
                echo "<td>" . $row["created_at"] . "</td>";
                echo "<td>";
                echo "<a href='edit_user.php?id=" . $row["id"] . "'>Edit</a> | ";
                echo "<a href='delete_user.php?id=" . $row["id"] . "' onclick='return confirm(\"Are you sure?\")'>Delete</a>";
                echo "</td>";
                echo "</tr>";
            }
        } else {
            echo "<tr><td colspan='6'>No users found</td></tr>";
        }
        ?>
    </table>
</body>
</html>

<?php
$conn->close();
?>
```

### 3. UPDATE - Edit Records

**edit_user.php**
```php
<?php
include 'database.php';

$id = $_GET['id'];

// Fetch user data
$sql = "SELECT * FROM users WHERE id = ?";
$stmt = $conn->prepare($sql);
$stmt->bind_param("i", $id);
$stmt->execute();
$result = $stmt->get_result();
$user = $result->fetch_assoc();

if ($_POST) {
    $name = $_POST['name'];
    $email = $_POST['email'];
    $age = $_POST['age'];
    
    $update_sql = "UPDATE users SET name = ?, email = ?, age = ? WHERE id = ?";
    $update_stmt = $conn->prepare($update_sql);
    $update_stmt->bind_param("ssii", $name, $email, $age, $id);
    
    if ($update_stmt->execute()) {
        echo "User updated successfully!";
        echo "<a href='index.php'>Back to List</a>";
    } else {
        echo "Error: " . $update_stmt->error;
    }
    
    $update_stmt->close();
} else {
?>

<!DOCTYPE html>
<html>
<head>
    <title>Edit User</title>
</head>
<body>
    <h2>Edit User</h2>
    <form method="POST">
        <label>Name:</label>
        <input type="text" name="name" value="<?php echo $user['name']; ?>" required><br><br>
        
        <label>Email:</label>
        <input type="email" name="email" value="<?php echo $user['email']; ?>" required><br><br>
        
        <label>Age:</label>
        <input type="number" name="age" value="<?php echo $user['age']; ?>" required><br><br>
        
        <input type="submit" value="Update User">
    </form>
    <a href="index.php">Back to List</a>
</body>
</html>

<?php
}
$conn->close();
?>
```

### 4. DELETE - Remove Records

**delete_user.php**
```php
<?php
include 'database.php';

if (isset($_GET['id'])) {
    $id = $_GET['id'];
    
    $sql = "DELETE FROM users WHERE id = ?";
    $stmt = $conn->prepare($sql);
    $stmt->bind_param("i", $id);
    
    if ($stmt->execute()) {
        echo "User deleted successfully!";
        echo "<a href='index.php'>Back to List</a>";
    } else {
        echo "Error: " . $stmt->error;
    }
    
    $stmt->close();
} else {
    echo "Invalid request";
}

$conn->close();
?>
```

### Advanced CRUD Features

**Search Functionality**
```php
<?php
// search.php
include 'database.php';

$search = $_GET['search'] ?? '';

$sql = "SELECT * FROM users WHERE name LIKE ? OR email LIKE ?";
$stmt = $conn->prepare($sql);
$search_term = "%" . $search . "%";
$stmt->bind_param("ss", $search_term, $search_term);
$stmt->execute();
$result = $stmt->get_result();
?>

<!DOCTYPE html>
<html>
<head>
    <title>Search Users</title>
</head>
<body>
    <h2>Search Users</h2>
    <form method="GET">
        <input type="text" name="search" placeholder="Search by name or email" value="<?php echo $search; ?>">
        <input type="submit" value="Search">
    </form>
    
    <table>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Email</th>
            <th>Age</th>
        </tr>
        
        <?php
        while($row = $result->fetch_assoc()) {
            echo "<tr>";
            echo "<td>" . $row["id"] . "</td>";
            echo "<td>" . $row["name"] . "</td>";
            echo "<td>" . $row["email"] . "</td>";
            echo "<td>" . $row["age"] . "</td>";
            echo "</tr>";
        }
        ?>
    </table>
</body>
</html>
```

**Pagination**
```php
<?php
// pagination.php
include 'database.php';

$page = $_GET['page'] ?? 1;
$records_per_page = 5;
$offset = ($page - 1) * $records_per_page;

// Get total records
$total_sql = "SELECT COUNT(*) as total FROM users";
$total_result = $conn->query($total_sql);
$total_records = $total_result->fetch_assoc()['total'];
$total_pages = ceil($total_records / $records_per_page);

// Get records for current page
$sql = "SELECT * FROM users LIMIT ? OFFSET ?";
$stmt = $conn->prepare($sql);
$stmt->bind_param("ii", $records_per_page, $offset);
$stmt->execute();
$result = $stmt->get_result();
?>

<!DOCTYPE html>
<html>
<head>
    <title>Users with Pagination</title>
</head>
<body>
    <h2>Users (Page <?php echo $page; ?> of <?php echo $total_pages; ?>)</h2>
    
    <table>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Email</th>
            <th>Age</th>
        </tr>
        
        <?php
        while($row = $result->fetch_assoc()) {
            echo "<tr>";
            echo "<td>" . $row["id"] . "</td>";
            echo "<td>" . $row["name"] . "</td>";
            echo "<td>" . $row["email"] . "</td>";
            echo "<td>" . $row["age"] . "</td>";
            echo "</tr>";
        }
        ?>
    </table>
    
    <!-- Pagination links -->
    <div>
        <?php for($i = 1; $i <= $total_pages; $i++): ?>
            <?php if($i == $page): ?>
                <strong><?php echo $i; ?></strong>
            <?php else: ?>
                <a href="?page=<?php echo $i; ?>"><?php echo $i; ?></a>
            <?php endif; ?>
        <?php endfor; ?>
    </div>
</body>
</html>
```

## Best Practices

### Security
- Always use prepared statements to prevent SQL injection
- Validate and sanitize user input
- Use HTTPS for sensitive data
- Implement proper error handling
- Never store passwords in plain text

### Performance
- Use appropriate indexes on database tables
- Limit database queries in loops
- Use connection pooling for high-traffic applications
- Implement caching where appropriate

### Code Organization
- Separate HTML, PHP, and SQL code
- Use configuration files for database settings
- Follow consistent naming conventions
- Comment your code properly
- Use version control (Git)

---

