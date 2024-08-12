# Data Tables

1. **Include jQuery:**
   - Add the following line inside the `<head>` section to include jQuery:
     ```html
     <script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
     ```

2. **Initialize DataTables:**
   - Include the DataTables CSS and JavaScript files. You've already done this in your code.
     ```html
     <link rel="stylesheet" href="https://cdn.datatables.net/1.13.7/css/jquery.dataTables.css" />
     <script src="https://cdn.datatables.net/1.13.7/js/jquery.dataTables.min.js"></script>
     ```
   - Replace your existing DataTable initialization script with the following:
     ```html
     <script>
         $(document).ready(function () {
             $('#myTable').DataTable();
         });
     </script>
     ```

3. **Remove Import Statement:**
   - Remove the following line from your script, as it's unnecessary:
     ```html
     <!-- Remove this line -->
     <!-- import DataTable from 'datatables.net-dt'; -->
     ```

4. **Final Script Section:**
   - Your final script section should look like this:
     ```html
     <!-- Bootstrap Bundle with Popper -->
     <script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
     <script src="https://cdn.datatables.net/1.13.7/js/jquery.dataTables.min.js"></script>
     <script>
         $(document).ready(function () {
             $('#myTable').DataTable();
         });
     </script>
     <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
     <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
     <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
     ```

Save this as a reference for future projects using DataTables. If you encounter any issues, you can refer back to this cheat sheet for guidance.