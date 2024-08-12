## Creating a MySQL Database using php

**Instructions:**

We need to create a function in the previous tutorial script which will run raw sql query on phpMyAdmin to create databases and stuff. So let's create a database using the following lines. 

```php
//Create a Database
$sql = "CREATE DATABASE dbHarry2";
mysqli_query($conn, $sqli);
```

Now if we refresh the phpMyAdmin page we will see the newly created dbHarry2 database. 

**Checking if the Database was created successfully or not:**

We can also get the result of the query using the following lines. Note that the reult will return True or False only.

```php
echo "The result is ";
echo var_dump($result);
echo"<br>";
```

or we can also use an "if else" statement to return the result. 

```php
// Check for the database creation success
if($result){
    echo "The db was created successfully!<br>";
}
else{
    echo "The db was not created successfully because of this error ---> ". mysqli_error($conn);
}
```
**Full Code**

```php
<?php
// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";

// Create a connection
$conn = mysqli_connect($servername, $username, $password);

// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}

// Create a db
$sql = "CREATE DATABASE dbHarry";
$result = mysqli_query($conn, $sql);

// Check for the database creation success
if($result){
    echo "The db was created successfully!<br>";
}
else{
    echo "The db was not created successfully because of this error ---> ". mysqli_error($conn);
}
  
?>
```

## Creating a Table in MySQL using php

**Creating a table**

We will create a new function called $database for creating the table in the specified database. Now we will create another function called $sql and we will write the specified sql query to make a table(Note we don't need to add the database name in the query as we have already added it on $database function). Now to check if the table was created successfully or not we need to use an "if-else" statement and the code should look like this. 

```php
// Create a table in the db (Here Table Name is phptrip )
$sql = "CREATE TABLE `phptrip` 
( 
            `sno` INT(6) NOT NULL AUTO_INCREMENT , 
            `name` VARCHAR(12) NOT NULL , 
            `dest` VARCHAR(6) NOT NULL , 
            PRIMARY KEY (`sno`)
)";

$result = mysqli_query($conn, $sql);


// Check for the table creation success
if($result){
    echo "The table was created successfully!<br>";
}
else{
    echo "The table was not created successfully because of this error ---> ". mysqli_error($conn);
}
```
**Full Code**

```php
<?php
// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";
$database = "dbharry";

// Create a connection
$conn = mysqli_connect($servername, $username, $password, $database);
// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}

// Create a table in the db
$sql = "CREATE TABLE `phptrip` ( `sno` INT(6) NOT NULL AUTO_INCREMENT , `name` VARCHAR(12) NOT NULL , `dest` VARCHAR(6) NOT NULL , PRIMARY KEY (`sno`))";
$result = mysqli_query($conn, $sql);

// Check for the table creation success
if($result){
    echo "The table was created successfully!<br>";
}
else{
    echo "The table was not created successfully because of this error ---> ". mysqli_error($conn);
}
  
?>
```

## Insert Data Into MySQL Using MySQLi using php

**Inserting Data**

Let's open our favourite code editor VSCode and start coding. We are going to connec to the database using the following code. 

```php
// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";
$database = "dbharry";

Now we will try to establish a connection to the database using a simple if-else method.

// Create a connection
$conn = mysqli_connect($servername, $username, $password, $database);
// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}
```

Now we need to run the sql query. We can copy sql query from the console as described in the video or we can write our own sql query. We just need to create a function to run the sql query. We can also add variables that can be inserted to the table using this method. We just need to create a variable function and then we need to use those variable function on the sql query in order to run. Then we can also use the if-else condition to check if the data was intserted or not. Like this :

```php
// Variables to be inserted into the table
$name = "Vikrant";
$destination = "Russia";

// Sql query to be executed
$sql = "INSERT INTO `phptrip` (`name`, `dest`) VALUES ('$name', '$destination')";
$result = mysqli_query($conn, $sql);

// Add a new trip to the Trip table in the database
if($result){
    echo "The record has been inserted successfully successfully!<br>";
}
else{
    echo "The record was not inserted successfully because of this error ---> ". mysqli_error($conn);
}
```


**Full Code**
```php
<?php

// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";
$database = "dbharry";

// Create a connection
$conn = mysqli_connect($servername, $username, $password, $database);
// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}

// Variables to be inserted into the table
$name = "Vikrant";
$destination = "Russia";

// Sql query to be executed
$sql = "INSERT INTO `phptrip` (`name`, `dest`) VALUES ('$name', '$destination')";
$result = mysqli_query($conn, $sql);

// Add a new trip to the Trip table in the database
if($result){
    echo "The record has been inserted successfully successfully!<br>";
}
else{
    echo "The record was not inserted successfully because of this error ---> ". mysqli_error($conn);
}
?>
```

## Selecting and Displaying Data From MySQL Using MySQLi

**Connecting to the database and running SQL query**
So let's start writing our script by connecting to the SQL database. As we have established a connection with the database, we will run the required SQL query to select a table in a database. The SQL query for selecting is 

```php
$sql = "SELECT * FROM `phptrip`";
$result = mysqli_query($conn, $sql);
```

Now to find the number of records returned from the table, we will write this code. 
```php
// Find the number of records returned
$num = mysqli_num_rows($result);
echo $num;
echo " records found in the DataBase<br>";
```

Now we can display the rows that are returned by SQL query using mysqli_fetch_assoc($result). It will return an array that will show the first record. Now to see the second record, we need to use mysqli_fetch_assoc($result) again. Because mysqli_fetch_assoc() returns an associative array representing the next record, we can now use this method to return the records. For that, we need to copy-paste the mysqli_fetch_assoc($result) several times until it returns a NULL value. But this is not the optimal way to do it. We can use "while-loop" and get a similar result in a short length of code. If we use this code, it will show all the values until it returns a NULL value. We can also beautify the result to our needs.

```php
 // We can fetch in a better way using the while loop
    while($row = mysqli_fetch_assoc($result)){
        // echo var_dump($row);
        echo $row['sno'] .  ". Hello ". $row['name'] ." Welcome to ". $row['dest'];
        echo "<br>";
    }
```
**Full Code**
```php
<?php
// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";
$database = "dbharry";

// Create a connection
$conn = mysqli_connect($servername, $username, $password, $database);
// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}

$sql = "SELECT * FROM `phptrip`";
$result = mysqli_query($conn, $sql);

// Find the number of records returned
$num = mysqli_num_rows($result);
echo $num;
echo " records found in the DataBase<br>";
// Display the rows returned by the sql query
if($num> 0){
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";
    // $row = mysqli_fetch_assoc($result);
    // echo var_dump($row);
    // echo "<br>";

    // We can fetch in a better way using the while loop
    while($row = mysqli_fetch_assoc($result)){
        // echo var_dump($row);
        echo $row['sno'] .  ". Hello ". $row['name'] ." Welcome to ". $row['dest'];
        echo "<br>";
    }


}
?>
```

## Updating Records in PHP & Where Clause
**Connecting to the database and running SQL query**
So let's start writing our script by connecting to the SQL database. We have learned earlier how to do that, so I will not be explaining that here again. For explanation, watch tutorial no 24. As we have established a connection with the database, we will run the required SQL query to select a database table. For this tutorial, I will be using a table called 'phptrip,’ and inside that table, I will update the 'dest.’ Let's fetch and display the data from dest by using where clause method.
```php
$sql = "SELECT * FROM `phptrip` WHERE `dest`='Bihar'";
$result = mysqli_query($conn, $sql);

// Usage of WHERE Clause to fetch data from the database
$num = mysqli_num_rows($result);
echo $num . " records found in the DataBase<br>";
$no=1;
if($num> 0){  
    while($row = mysqli_fetch_assoc($result)){ 
        echo $no .  ". Hello ". $row['name'] ." Welcome to ". $row['dest'];
        echo "<br>";
        $no = $no +1;
    }
}
```

Now as our data has been fetched, we need to update the dest. For updating the dest the SQL query is :
```php
$sql = "UPDATE `phptrip` SET `name` = 'FromBihar' WHERE `dest` = 'Bihar'";
```
So now we can put this code inside a where clause  to update the data and show us the result.

```php// Usage of WHERE Clause to Update Data
$sql = "UPDATE `phptrip` SET `name` = 'FromBihar' WHERE `dest` = 'Bihar'";
$result = mysqli_query($conn, $sql);
echo var_dump($result);
$aff = mysqli_affected_rows($conn);
echo "<br>Number of affected rows: $aff <br>";
if($result){
    echo "We updated the record successfully";
}
else{
    echo "We could not update the record successfully";
}
```
**Full Code**
```php<?php
// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";
$database = "dbharry";

// Create a connection
$conn = mysqli_connect($servername, $username, $password, $database);

// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}


$sql = "SELECT * FROM `phptrip` WHERE `dest`='Bihar'";
$result = mysqli_query($conn, $sql);

// Usage of WHERE Clause to fetch data from the database
$num = mysqli_num_rows($result);
echo $num . " records found in the DataBase<br>";
$no=1;
if($num> 0){  
    while($row = mysqli_fetch_assoc($result)){ 
        echo $no .  ". Hello ". $row['name'] ." Welcome to ". $row['dest'];
        echo "<br>";
        $no = $no +1;
    }
}

// Usage of WHERE Clause to Update Data
$sql = "UPDATE `phptrip` SET `name` = 'FromBihar' WHERE `dest` = 'Bihar'";
$result = mysqli_query($conn, $sql);
echo var_dump($result);
$aff = mysqli_affected_rows($conn);
echo "<br>Number of affected rows: $aff <br>";
if($result){
    echo "We updated the record successfully";
}
else{
    echo "We could not update the record successfully";
}
?>
```

## Deleting Records in PHP & Limit Clause


**Connecting to the database and running SQL query**

So let's start writing our script by connecting to the SQL database. We have learned earlier how to do that, so I will not be explaining that here again. The SQL query for deleting is :
```php
$sql = "DELETE FROM `phptrip` WHERE `dest` = 'Russia' ";
```

You can see that 'phptrip' is our table name, and we are deleting the records that have Russia as dest. If you have multiple records with the same dest, then all of them will be deleted. To check how many rows were affected, we need to use the following code: 
```php
$aff = mysqli_affected_rows($conn);
echo "<br>Number of affected rows: $aff <br>";
```
If you want to limit the amount of records that are being deleted, you should use LIMIT ## (## is the number of records you want to delete). For example, if you want to delete 13 records that have Russia as dest, then use the following code:
```php
$sql = "DELETE FROM `phptrip` WHERE `dest` = 'Russia' LIMIT 13";
```
Now to display if our records have been deleted or not, we can use a simple if-else command with $result like this:
```php
if($result){
    echo "Delete successfully";
}
else{
    $err = mysqli_error($conn);
    echo "Not Delete successfully due to this error --> $err";
}
```
**Full Code**
```php
<?php
// Connecting to the Database
$servername = "localhost";
$username = "root";
$password = "";
$database = "dbharry";

// Create a connection
$conn = mysqli_connect($servername, $username, $password, $database);

// Die if connection was not successful
if (!$conn){
    die("Sorry we failed to connect: ". mysqli_connect_error());
}
else{
    echo "Connection was successful<br>";
}


$sql = "DELETE FROM `phptrip` WHERE `dest` = 'Russia' LIMIT 13";
$result = mysqli_query($conn, $sql);
$aff = mysqli_affected_rows($conn);
echo "<br>Number of affected rows: $aff <br>";

if($result){
    echo "Delete successfully";
}
else{
    $err = mysqli_error($conn);
    echo "Not Delete successfully due to this error --> $err";
}

?>
```