In PHP, both `include` and `require` are used to include and integrate code from other files into the current script. However, there is a slight difference in how they behave:

1. **include**: 
   - The `include` statement includes and evaluates the specified file. If the file is not found or if there is an error during inclusion, `include` generates a warning but continues execution of the script.
   - In simpler terms, if the file cannot be included, for example, due to a typo in the filename, the script will continue to execute and only generate a warning.

   Example:
   ```php
   <?php
   include 'myfile.php';
   echo "This will be executed even if myfile.php is not found or has errors.";
   ?>
   ```

2. **require**:
   - The `require` statement also includes and evaluates the specified file, but if the file is not found or if there is an error during inclusion, `require` generates a fatal error and halts the execution of the script.
   - In other words, if the file cannot be included, the script will stop executing with a fatal error.

   Example:
   ```php
   <?php
   require 'myfile.php';
   echo "This will not be executed if myfile.php is not found or has errors.";
   ?>
   ```

So, the main difference lies in how they handle errors:

- `include` generates a warning and continues script execution.
- `require` generates a fatal error and halts script execution.

Generally, you would use `require` when the included file is crucial for the functioning of your script and any error in including it should stop the script execution. `include` is used when the included file is not critical, and you want the script to continue running even if the file is not found or has errors.