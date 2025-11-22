# Travel-Management-System

php + MySQL based travel management system with Bootstrap.

## Quick setup (Windows, using XAMPP)

1. Install XAMPP (or WAMP / Laragon) with Apache + PHP + MySQL and start Apache & MySQL.

2. Copy project to web root:
   - Move the folder `SQL-Tourism-Project-main` into XAMPP's htdocs folder:
     C:\xampp\htdocs\SQL-Tourism-Project-main

3. Import the database:
   - Using phpMyAdmin:
     - Open http://localhost/phpmyadmin
     - Create a database named `travel`
     - Select the `travel` database → Import → choose `travel.sql` (file in project root) → Go
   - Or using CLI:
     - Open cmd and run:
       mysql -u root -p
       (enter password if any)
       use travel;
       source "C:\path\to\travel.sql";
       exit

4. Configure DB credentials (if needed):
   - Default code expects MySQL user `root` with no password.
   - If you changed credentials, edit:
     c:\Users\PC\Downloads\SQL-Tourism-Project-main\SQL-Tourism-Project-main\function.php
     Update mysqli_connect(...) credentials to match your MySQL user/password.

5. Ensure image folders exist and contain images:
   - Admin pack images: Admin/packimages
   - Subcategory images: Admin/subcatimages
   - General images: images/
   If images are missing, placeholders will appear.

6. Open the site in browser:
   - http://localhost/SQL-Tourism-Project-main/index.php

7. Admin login:
   - Open: http://localhost/SQL-Tourism-Project-main/admin/loginform.php
   - Default user (from travel.sql): username `mahmud`, password `1234`

## Notes & troubleshooting
- PHP version: project is written for older PHP (5.x–7.x). Use PHP 7.4+ if possible. If you see deprecated warnings, enable error display for debugging or suppress in php.ini.
- If you get DB connection errors, confirm MySQL is running and credentials in function.php are correct.
- If pages show blank or partial HTML, check for PHP errors in Apache error log (C:\xampp\apache\logs\error.log).
- Some files include inline HTML wrappers (e.g., function.php). That is OK for simple use, but a cleaner separation of PHP-only files is recommended.
- If images are not displayed, confirm image filenames listed in the database match files under Admin/packimages and Admin/subcatimages.
- After importing SQL, if primary keys or AUTO_INCREMENT are missing, re-check the import result in phpMyAdmin.

## Useful commands (Windows)
- Start XAMPP Control Panel and start Apache & MySQL.
- Import via CLI:
  mysql -u root -p travel < "C:\Users\PC\Downloads\SQL-Tourism-Project-main\SQL-Tourism-Project-main\travel.sql"

## Recommended improvements (optional)
- Move DB connection logic to a pure-PHP file without HTML.
- Validate and sanitize user inputs to avoid SQL injection (use prepared statements).
- Verify/normalize column names and casing used by PHP vs SQL dump (some files expect numeric indexes).
