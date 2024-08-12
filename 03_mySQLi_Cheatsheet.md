Certainly! Here's the extended MySQLi functions cheat sheet, including `mysqli_affected_rows` and related functions:

**MySQLi Functions Cheat Sheet in PHP**

---

**Connecting to MySQL Database:**

1. **`mysqli_connect` - Open a new connection to the MySQL server:**
   ```php
   $conn = mysqli_connect($servername, $username, $password, $dbname);
   ```

2. **`mysqli_close` - Close the MySQL connection:**
   ```php
   mysqli_close($conn);
   ```

---

**Executing Queries:**

3. **`mysqli_query` - Perform queries against the database:**
   ```php
   $result = mysqli_query($conn, $sql);
   ```

4. **`mysqli_multi_query` - Perform multiple queries:**
   ```php
   mysqli_multi_query($conn, $sql);
   ```

5. **`mysqli_real_escape_string` - Escape special characters in a string for use in an SQL statement:**
   ```php
   $escaped_str = mysqli_real_escape_string($conn, $unescaped_str);
   ```

---

**Fetching Data:**

6. **`mysqli_fetch_assoc` - Fetch a result row as an associative array:**
   ```php
   $row = mysqli_fetch_assoc($result);
   ```

7. **`mysqli_fetch_array` - Fetch a result row as an associative, numeric array, or both:**
   ```php
   $row = mysqli_fetch_array($result, MYSQLI_ASSOC);
   ```

8. **`mysqli_fetch_row` - Fetch a result row as an enumerated array:**
   ```php
   $row = mysqli_fetch_row($result);
   ```

---

**Error Handling:**

9. **`mysqli_error` - Return a string description of the last error:**
   ```php
   $error = mysqli_error($conn);
   ```

10. **`mysqli_errno` - Return the error code for the most recent function call:**
    ```php
    $error_code = mysqli_errno($conn);
    ```

---

**Prepared Statements:**

11. **`mysqli_prepare` - Prepare an SQL statement for execution:**
    ```php
    $stmt = mysqli_prepare($conn, $sql);
    ```

12. **`mysqli_stmt_bind_param` - Binds variables to a prepared statement as parameters:**
    ```php
    mysqli_stmt_bind_param($stmt, "s", $param1);
    ```

13. **`mysqli_stmt_execute` - Executes a prepared Query:**
    ```php
    mysqli_stmt_execute($stmt);
    ```

14. **`mysqli_stmt_get_result` - Transfers a result set from a prepared statement:**
    ```php
    $result = mysqli_stmt_get_result($stmt);
    ```

---

**Transactions:**

15. **`mysqli_begin_transaction` - Start a new transaction:**
    ```php
    mysqli_begin_transaction($conn);
    ```

16. **`mysqli_commit` - Commit the current transaction:**
    ```php
    mysqli_commit($conn);
    ```

17. **`mysqli_rollback` - Roll back the current transaction:**
    ```php
    mysqli_rollback($conn);
    ```

---

**Affected Rows:**

18. **`mysqli_affected_rows` - Get the number of affected rows in a previous MySQL operation:**
    ```php
    $aff = mysqli_affected_rows($conn);
    ```

---

**Miscellaneous:**

19. **`mysqli_insert_id` - Get the ID generated in the last query:**
    ```php
    $last_id = mysqli_insert_id($conn);
    ```

20. **`mysqli_num_rows` - Get the number of rows in a result set:**
    ```php
    $num_rows = mysqli_num_rows($result);
    ```

---

**Remember to handle errors and ensure the security of your queries, especially when using user input.**

**Note for Future Reference:**
- Make sure to handle errors using `mysqli_error` and `mysqli_errno`.
- When dealing with user input, use prepared statements to prevent SQL injection.
- Always close the database connection using `mysqli_close` when done.

--- 

This cheat sheet covers essential MySQLi functions for database interaction in PHP. For more detailed information, refer to the official PHP documentation: [MySQLi Functions](https://www.php.net/manual/en/book.mysqli.php).