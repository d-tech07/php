
### To Start new Project using PHP, we need to learn following steps

1. Step 1: Set Up the Development Environment
    Install XAMPP / WAMP / Laragon (Local Server)
    Download XAMPP:*** https://www.apachefriends.org ***  Download wamp64: *** https://sourceforge.net/projects/wampserver/ ***
    Install and start Apache and MySQL.

    When install you faced an error in wamp:
    Go to https://wampserver.aviatechno.net/ and install Microsoft VC packages VC2008, 2010, 2012, 2013, 2015-2022 zip files *** All VC Redistributable Packages (x86_x64) (32 & 64bits): https://wampserver.aviatechno.net/files/vcpackages/all_vc_redist_x86_x64.zip *** and extract file. Then after install one by one to all packages 

2. Set up Project Folder
    *** Go to xampp/htdocs/  ***
    OR 
    *** Go to wamp64/www/ ***
    Create a folder (e.g., mywebsite)

3. Open a Code Editor
    Recommended: VS Code, Sublime Text, or PHPStorm
    Install VS Code: https://code.visualstudio.com/

4. Go to your project folder *** mywebsite *** and open it in vs code 

5. Create following  File Structure as well 

    ```
    mywebsite/
    ├── css/
    │   └── style.css
    ├── js/
    │   └── min.js
    ├── img/
    ├── files/
    ├── config/
    │   └── db.php
    ├── inc/
    │   ├── header.php
    │   ├── navbar.php
    │   ├── sidebar.php
    │   └── footer.php
    ├── users/
    │   ├── create.php
    │   ├── index.php
    │   ├── show.php
    │   ├── edit.php
    │   └── delete.php
    ├── index.php         ← (Login Form)
    ├── signup.php
    ├── dashboard.php
    ```
    *** in the above structure, you need to repeat the same folder like users for further more features ***

    ### Description of Important Folders:

    * **`css/`**: Stylesheets
    * **`js/`**: JavaScript files
    * **`img/`**: Image assets
    * **`files/`**: Uploaded documents/files
    * **`config/`**: Configuration files (e.g., database connection)
    * **`inc/`**: required layout components (header, navbar, etc.)
    * **`users/`**: User module (CRUD operations)
    * **Root Files**: `index.php` (login), `signup.php`, and `dashboard.php`

5. Write database connection code in db.php
---

## **`config/db.php`**

    ```php
        <?php
        // Database configuration
        $host = "localhost";
        $username = "root";
        $password = "";
        $database = "mywebsite";  // Change to your database name

        // Create database connection
        $conn = mysqli_connect($host, $username, $password, $database);

        // Check connection
        if (!$conn) {
            die("Connection failed: " . mysqli_connect_error());
        }

        // Optional: echo "Connected successfully";
        ?>
    ```

        ---

        ##  **How to Use in Other Files**

        require the database connection at the top of any PHP file:

        ```php
            <?php
            require_once 'config/db.php';
            // Now you can use $conn for queries
            ?>
        ```
        ---

6. Here’s how to **create a database** named `mywebsite` for your PHP project using **phpMyAdmin** or **SQL query**.

    ---

    ## **Option 1: Create Database using phpMyAdmin (GUI)**
    1. Open your browser and go to:

    ```
    http://localhost/phpmyadmin
    ```
    2. Click on the **"New"** button in the left sidebar.
    3. In the **"Create database"** form:

    * **Database name**: `mywebsite`
    * **Collation**: `utf8mb4_general_ci` (recommended)
    4. Click **Create**.

    You now have a database named `mywebsite`.

    ---

    ## **Option 2: Create Database using SQL Query**
    You can also run this SQL command in the **SQL tab** of phpMyAdmin:

    ```sql
    CREATE DATABASE mywebsite CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
    ```

    ---

    ## **Option 3: Create Database using PHP**

    You can also create it programmatically: database/create-database.php

    ```php
        <?php
        $host = "localhost";
        $username = "root";
        $password = "";

        // Connect to MySQL server (no DB selected yet)
        $conn = mysqli_connect($host, $username, $password);

        if (!$conn) {
            die("Connection failed: " . mysqli_connect_error());
        }

        // Create database: choose any one
        $sql = "CREATE DATABASE mywebsite"; OR
        $sql = "CREATE DATABASE mywebsite CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci";


        if (mysqli_query($conn, $sql)) {
            echo "Database created successfully!";
        } else {
            echo "Error creating database: " . mysqli_error($conn);
        }

        mysqli_close($conn);
        ?>
    ```
    ### And run the file in your browser: localhost/myWebsite/database/create-database.php
    ---

7. Create table ( database/database.php)
    ```php
        <?php
        // step 1
        $host = "localhost";
        $username = "root";
        $password = "";
        $database = "mywebsite";

        // Connect to MySQL
        $conn = mysqli_connect($host, $username, $password, $database);

        // Check connection
        if (!$conn) {
            die("Connection failed: " . mysqli_connect_error());
        }
        //....

        // step 2
        // Drop table if exists
        $dropTable = "DROP TABLE IF EXISTS users";
        if (mysqli_query($conn, $dropTable)) {
            echo "Old users table dropped successfully.<br>";
        } else {
            die("Error dropping table: " . mysqli_error($conn));
        }
        //....

        // step 3
        // Create new users table
        $createTable = "CREATE TABLE users (
            id INT AUTO_INCREMENT PRIMARY KEY,
            name VARCHAR(100) NOT NULL,
            email VARCHAR(100) NOT NULL UNIQUE,
            password VARCHAR(255) NOT NULL,
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        )";
        if (mysqli_query($conn, $createTable)) {
            echo "New users table created successfully.<br>";
        } else {
            die("Error creating table: " . mysqli_error($conn));
        }
        //....

        // Close connection
        mysqli_close($conn);
        ?>
    ```
    ### And run the file in your browser: localhost/myWebsite/database/database.php
    ### to create more tables, repeat the step 3 block of code

8. Create all Pages
    Create Login form in index.php
    Create dashboard in dashboard.php
    Create signup page in singup.php
    Create INC pages 
    Create users pages 

### Login page 
    <!-- index.php (Login Form) -->
```php
    <?php
    session_start();
    require_once "config/db.php";

    if ($_SERVER['REQUEST_METHOD'] == 'POST') {
        $email = $_POST['email'];
        $password = $_POST['password'];

        $sql = "SELECT * FROM users WHERE email = '$email' AND password = MD5('$password')";
        $result = mysqli_query($conn, $sql);

        if (mysqli_num_rows($result) == 1) {
            $_SESSION['user'] = mysqli_fetch_assoc($result);
            header("Location: dashboard.php");
            exit();
        } else {
            $error = "Invalid email or password.";
        }
    }
    ?>
```

```php
    <?php require "inc/header.php"; ?>
    <div class="container mt-5">
        <h2>Login</h2>
        <?php if (isset($error)) echo "<div class='alert alert-danger'>$error</div>"; ?>
        <form method="POST">
            <div class="mb-3">
                <label>Email</label>
                <input type="email" name="email" class="form-control" required>
            </div>
            <div class="mb-3">
                <label>Password</label>
                <input type="password" name="password" class="form-control" required>
            </div>
            <button type="submit" class="btn btn-primary">Login</button>
            <a href="signup.php" class="btn btn-link">Sign up</a>
        </form>
    </div>
    <?php require "inc/footer.php"; ?>
```

### Dashboard
```php
    <!-- dashboard.php -->
    <?php
    session_start();
    if (!isset($_SESSION['user'])) {
        header("Location: index.php");
        exit();
    }
    require "inc/header.php";
    require "inc/navbar.php";
    require "inc/sidebar.php";
    ?>
    <div class="container mt-4">
        <h2>Welcome, <?php echo $_SESSION['user']['name']; ?>!</h2>
        <p>This is your dashboard.</p>
    </div>
    <?php require "inc/footer.php"; ?>
```

### Signup page
```php
    <!-- signup.php -->
    <?php
    require_once "config/db.php";
    if ($_SERVER['REQUEST_METHOD'] == 'POST') {
        $name = $_POST['name'];
        $email = $_POST['email'];
        $password = md5($_POST['password']);

        $sql = "INSERT INTO users (name, email, password) VALUES ('$name', '$email', '$password')";
        if (mysqli_query($conn, $sql)) {
            header("Location: index.php");
        } else {
            $error = "Signup failed.";
        }
    }
    ?>

    <?php require "inc/header.php"; ?>
    <div class="container mt-5">
        <h2>Signup</h2>
        <?php if (isset($error)) echo "<div class='alert alert-danger'>$error</div>"; ?>
        <form method="POST">
            <div class="mb-3">
                <label>Name</label>
                <input type="text" name="name" class="form-control" required>
            </div>
            <div class="mb-3">
                <label>Email</label>
                <input type="email" name="email" class="form-control" required>
            </div>
            <div class="mb-3">
                <label>Password</label>
                <input type="password" name="password" class="form-control" required>
            </div>
            <button type="submit" class="btn btn-success">Sign Up</button>
        </form>
    </div>
    <?php require "inc/footer.php"; ?>
```

### inc/
```php
    <!-- inc/header.php -->
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>My PHP Website</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    </head>
    <body>
```

```php
    <!-- inc/navbar.php -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">MyWebsite</a>
        <div class="collapse navbar-collapse">
        <ul class="navbar-nav ms-auto">
            <li class="nav-item">
            <a class="nav-link" href="dashboard.php">Dashboard</a>
            </li>
            <li class="nav-item">
            <a class="nav-link" href="logout.php">Logout</a>
            </li>
        </ul>
        </div>
    </div>
    </nav>
```

```php
    <!-- inc/sidebar.php -->
    <div class="bg-light p-3" style="width: 200px; float: left; height: 100vh;">
    <h5>Sidebar</h5>
    <ul class="nav flex-column">
        <li class="nav-item"><a class="nav-link" href="users/index.php">Manage Users</a></li>
    </ul>
    </div>
    <div style="margin-left: 210px;">
```
```php
    <!-- inc/footer.php -->
    </div> <!-- Close sidebar content wrapper -->
    <footer class="bg-dark text-white text-center p-3 mt-4">
    &copy; <?php echo date("Y"); ?> MyWebsite. All rights reserved.
    </footer>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    </body>
    </html>
```
### Users pages: users/
    <!-- users/index.php -->
### users/index.php
```php
    <?php
    require_once "../config/db.php";
    require "../inc/header.php";
    require "../inc/navbar.php";
    require "../inc/sidebar.php";

    $result = mysqli_query($conn, "SELECT * FROM users");
    ?>
    <div class="container mt-4">
        <h2>All Users</h2>
        <a href="create.php" class="btn btn-primary mb-3">Add New User</a>
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <?php while($row = mysqli_fetch_assoc($result)) { ?>
                <tr>
                    <td><?= $row['id'] ?></td>
                    <td><?= $row['name'] ?></td>
                    <td><?= $row['email'] ?></td>
                    <td>
                        <a href="show.php?id=<?= $row['id'] ?>" class="btn btn-info btn-sm">View</a>
                        <a href="edit.php?id=<?= $row['id'] ?>" class="btn btn-warning btn-sm">Edit</a>
                        <a href="delete.php?id=<?= $row['id'] ?>" class="btn btn-danger btn-sm" onclick="return confirm('Are you sure?')">Delete</a>
                    </td>
                </tr>
                <?php } ?>
            </tbody>
        </table>
    </div>
    <?php require "../inc/footer.php"; ?>
```

### users/create.php
```php
    <!-- users/create.php -->
    <?php
    require_once "../config/db.php";
    if ($_SERVER['REQUEST_METHOD'] == 'POST') {
        $name = $_POST['name'];
        $email = $_POST['email'];
        $password = md5($_POST['password']);

        $sql = "INSERT INTO users (name, email, password) VALUES ('$name', '$email', '$password')";
        mysqli_query($conn, $sql);
        header("Location: index.php");
    }
    require "../inc/header.php";
    require "../inc/navbar.php";
    require "../inc/sidebar.php";
    ?>
    <div class="container mt-4">
        <h2>Add New User</h2>
        <form method="POST">
            <div class="mb-3">
                <label>Name</label>
                <input type="text" name="name" class="form-control" required>
            </div>
            <div class="mb-3">
                <label>Email</label>
                <input type="email" name="email" class="form-control" required>
            </div>
            <div class="mb-3">
                <label>Password</label>
                <input type="password" name="password" class="form-control" required>
            </div>
            <button type="submit" class="btn btn-success">Create</button>
        </form>
    </div>
    <?php require "../inc/footer.php"; ?>
```

### users/show.php
```php
    <!-- users/show.php -->
    <?php
    require_once "../config/db.php";
    require "../inc/header.php";
    require "../inc/navbar.php";
    require "../inc/sidebar.php";

    $id = $_GET['id'];
    $result = mysqli_query($conn, "SELECT * FROM users WHERE id = $id");
    $user = mysqli_fetch_assoc($result);
    ?>
    <div class="container mt-4">
        <h2>User Details</h2>
        <p><strong>Name:</strong> <?= $user['name'] ?></p>
        <p><strong>Email:</strong> <?= $user['email'] ?></p>
        <a href="index.php" class="btn btn-secondary">Back</a>
    </div>
    <?php require "../inc/footer.php"; ?>
```

### users/index.php
```php
    <!-- users/edit.php -->
    <?php
    require_once "../config/db.php";
    require "../inc/header.php";
    require "../inc/navbar.php";
    require "../inc/sidebar.php";
    $id = $_GET['id'];

    if ($_SERVER['REQUEST_METHOD'] == 'POST') {
        $name = $_POST['name'];
        $email = $_POST['email'];

        $sql = "UPDATE users SET name = '$name', email = '$email' WHERE id = $id";
        mysqli_query($conn, $sql);
        header("Location: index.php");
    }

    $result = mysqli_query($conn, "SELECT * FROM users WHERE id = $id");
    $user = mysqli_fetch_assoc($result);
    ?>
    <div class="container mt-4">
        <h2>Edit User</h2>
        <form method="POST">
            <div class="mb-3">
                <label>Name</label>
                <input type="text" name="name" class="form-control" value="<?= $user['name'] ?>" required>
            </div>
            <div class="mb-3">
                <label>Email</label>
                <input type="email" name="email" class="form-control" value="<?= $user['email'] ?>" required>
            </div>
            <button type="submit" class="btn btn-primary">Update</button>
        </form>
    </div>
    <?php require "../inc/footer.php"; ?>
```

### users/index.php
```php
    <!-- users/delete.php -->
    <?php
    require_once "../config/db.php";
    $id = $_GET['id'];

    $sql = "DELETE FROM users WHERE id = $id";
    mysqli_query($conn, $sql);

    header("Location: index.php");
    exit();
    ?>
```