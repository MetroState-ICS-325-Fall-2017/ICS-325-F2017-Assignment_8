Assignment 8
============

Purpose
-------
To help you learn the basics of:
* MySQL (and MariaDB)
* MySQL Workbench
* Importing databases from SQL scripts
* Using PHP to query and report from a MySQL database

Collaboration
-------------
You can talk about the assignment with your peers in the class. You can work with 1 or 2 other people on the assignment, but make sure to mention who they are when you turn your code in.

Prerequisites
-------------
* You will need MySQL installed.  If you are not part of the database course, install XAMPP.  If you are part of the MySQL course, you can use the MySQL version you installed already.
* You will need to install MySQL Workbench for free from [mysql.com](https://www.mysql.com/products/workbench/)
  - Note: If you use Windows, you may need to install Visual C++ Redistributable for Visual Studio 2015 and/or Microsoft .NET Framework 4.5 Client Profile.  Both are listed on the download page for MySQL Workbench.  If MySQL Workbench doesn't work, then try installing Visual C++ Redistributable for Visual Studio 2015 first.  If it still doesn't work, then try installing Microsoft .NET Framework 4.5 Client Profile.
* You will need to import people.sql and mysqlsampledatabase.sql into your MySQL database using MySQL workbench.
* To run the book examples, you need to import book_examples/bookorama.sql into your MySQL database using MySQL workbench.
* You will need the PDO with MySQL support.  The PHP version that comes with XAMPP has this built-in.

### Instructions to set up the code to run
First you need to clone your git repository to your computer.  Open GitKraken and make sure you are logged into your github.com account.  Next go to `File->Clone Repo`.  Select the `GitHub.com` icon.  A list of your repositories in github.com should pop up.  Select your assignment 8 repo.  If you want, change `Where to clone to` by clicking browser and selecting a folder for your git repo to be cloned into.  Finally, hit the `Clone the repo!` button.  The repo should now clone to your computer.

For the assignment, you will write PHP in PHP CLI mode.  However, the book examples need to be run via a web server.  So, you need to set up PhpStorm.  We will be using the built-in PHP CGI server for this assignment.  To do so, first make sure you have the git repo open in PhpStorm by using the Open Directory menu item under File in PhpStorm (`File->Open Directory`).  Next go to `Run->Edit Configurations...` Click the green `+` to create a new configuration.  Select `PHP Built-in Web Server`.  Change the name to `MySQL Lab`.  Leave host as `localhost`.  Set the port to `8080`.  Set the `Document root` to your git repo directory by clicking the `...` button next to the field and using the file chooser to select it.  In the top right of the window there is a check box labled `Single instance only`, click on it to check it.  If there is a red ! icon near the bottom right of the window, click the `Fix` button and specify your PHP interpreter.  Once done, click `Ok` to exit the Edit Configurations window.  Next hit the green run button to start the PHP CGI web server.  **Note that before the following URLs will work**, you need to import the book_examples/bookorama.sql file into MySQL.  Here are the URLS you can try that are part of the book examples:
* [http://localhost:8080/book_examples/search.html](http://localhost:8080/book_examples/search.html) - perform a search using the mysqli driver.
* [http://localhost:8080/book_examples/search_pdo.html](http://localhost:8080/book_examples/search_pdo.html) - perform a search using PDO.
* [http://localhost:8080/book_examples/newbook.html](http://localhost:8080/book_examples/newbook.html) - insert a new record.

Assignment Set Up
-----------------
Make sure that MySQL is running.  If you have XAMPP, open the XAMPP control panel and click the `start` button next to MySQL.  If you are in the database course, MySQL may already be running in the background on your machine.

Open MySQL workbench.  If there is a button in the top left that says `Local instance 3306` click it and you will be logged into the MySQL server.

If not, click the `+` button next to `MySQL Connections`.  Name the connection `Local instance 3306`.  Hostname should be `127.0.0.1`.  Port should be `3306`.  Username should be `root`.  The password is blank if you use XAMPP.  If you installed MySQL for the database course, you may need to enter a password.  Hit okay and then open the connection by clicking on it.

Once you are in MySQL Workbench, go to `File->Run SQL Script...`  Select the `people.sql` script.  Hit the `Run` button.  If it asks for a password, you do not need one if you use XAMPP. Once it is done, in the bottom left side of the screen is a panel that says `SCHEMAS`.  Click the 2 headed arrow button next to it.  That will show you the schemas (databases) you have running.  Hit the refresh button (2 arrows in a circle) to see the examples database that was created by `people.sql`.  Click on the `+` next to examples to see the people table.  To run queries against a database, double click it.  The database name will turn bold.  Any queries you execute in you query window will run against the bolded database by default.

Now go to `File->Run SQL Script...` again, but this time select `mysqlsampledatabase.sql`.  Import it the same way.  Once you are done and refresh the schemas, you will see the classicmodels database.  Double click that database to select it.

Do the same for the `book_examples/bookorama.sql` file as well.  This will create the books database used in the book examples.

You should try out the example MySQL commands that go with the mysqlsampledatabase.sql file.  You should ensure that you run the ATLER table statement in the examples that changes the `priceEach` column in the `classicmodels.orderdetails` table to use decimals instead of floats.

Resources and Examples
----------------------
Chapters 9, 10, and 11 in the book goes over the basics of databases.

The sample database we will be using comes from the site [mysqltutorial.org](http://www.mysqltutorial.org/).  You will probably find it helpful to go through their examples on the following topics which make use of that sample database:
* [basics of the SELECT statement](http://www.mysqltutorial.org/mysql-select-statement-query-data.aspx) (read from the database)
* [basics of the WHERE clause](http://www.mysqltutorial.org/mysql-where/) (used with SELECT, INSERT, UPDATE)
* [basics of the ORDER BY clause](http://www.mysqltutorial.org/mysql-order-by/) (sorting SELECT results)
* [basics of the IN operator](http://www.mysqltutorial.org/sql-in.aspx) (part of WHERE clause)
* [basics of the AS keyword](http://www.mysqltutorial.org/mysql-alias/) (aliases for tables, select values, etc)
* [basics of the GROUP BY clause](http://www.mysqltutorial.org/mysql-group-by.aspx) (used with SELECT for calculating aggregates)
* [basics of the INNER JOIN clause](http://www.mysqltutorial.org/mysql-inner-join.aspx) (the default JOIN for MySQL):
* [basics of a sub-query](http://www.mysqltutorial.org/mysql-subquery/)
* [basics of aggregate functions](http://www.mysqltutorial.org/mysql-aggregate-functions.aspx)

Files in this Repo
------------------


* **people.sql** - Example schema and data used by example_sql_statements.sql.
* **php_pdo_mysql_example.php** - A simple example of how to use PHP, PDO, and MySQL.
* **book_examples/** - directory that contains the code examples from Chapter 9, 10, and 11 from the book.  You need to start the built-in PHP web server for these to work.
* **mysqlsampledatabase.sql** - Schema and data used by example_sql_statements.sql and the assignment 8 problems.
* **example_sql_statements.sql** - Example SQL statements using the example database from mysqlsampledatabase.sql.
* **assignment_8_problems.txt** - Contains instructions on how to complete the assignment and how it is graded.
* **assignment_8.php** - A script you need to modify to perform a SQL query and print the results to the terminal.  Referred to by assignment_8_problems.txt.
* **assignment_8_solution_output.txt** - Your completed assignment_8.php output should look like this


How to Turn in the Assignment
-----------------------------
You need to clone your private git repo for assignment 8.  Make changes assignment_8.php to complete problem 6.  For problems 1 though 5, edit the file assignment_8_problems.txt and follow the instructions given within that file for recording your answers.  Use a good text editor such as Notepad++ (on Windows) or PhpStorm when editing the text file.  Notepad (on Windows) may not work properly.

Once you are done, commit your modifications to your master branch and push them to GitHub.  Then go to D2L and turn in the assignment to let me know I can go look at your repo and grade you.  D2L requires you to upload a file, so upload a txt file with a link to your private git repo in it.
