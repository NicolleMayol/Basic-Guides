QUICK SQL GUIDE: (From your loving wife):

SQL is the programming language for RELATIONAL databases. You've heard me multiple times talk about how there are two types of databases: Relational and non-relational (also called no-sql). Relational databases are the most traditional types of DB's. They are (as their name suggests), databases that contain multiple relations between different tables. This relations are defined in their cardinality, as you can have tables that have 1-1 relationships, 1-to-many, or many-to-many relationships. I won't explain this further because you already know that.

Databases, no matter the type, are just a way to store and handle data, which is the core of basically every software application out there. As such, being that this data is stored in the database, we need a way to query the data. That´s where SQL (Standard Query Language) comes in. SQL is the tool we programmers use to retrieve, insert and modify data inside the database.

SQL is quite simple. It is basically like just writing in English. As any other language, there a few things to keep in mind. It's important to understand what you´re doing beforehand because once you execute a query in your database, there is no going back. You can delete your entire database with just one line of code and any database motor will allow you to do so. So, it's important to be cautious and having backups when working with important data.

A few of the things you have to keep in mind: Database fields have data types, and SQL is very strict about it. Also, inside those data types, you can choose the length of the data. For example, if you need to store AGES, you would choose a NUMBER type with a length of 150 (because it´s very unlikely that someone will be over 150 years old, right?). But for names, you would use a VARCHAR type with a longer length, because names can be very long sometimes. This is important down the road, because it allows for the database to be more efficient and scalable.

These are a few of the most relevant statements used in SQL:

 * SELECT: This is the way to tell the database that you want to retrieve data. When you use a SELECT statement, you must tell the database two main things: How many registries you need (e.g. you want all *, or you want 1, or 2, or the top 1000, whatever you want) and where you want to retrieve that data from (e.g. the table where the data you want is stored). You can also add conditions that you want the data to comply with, like if it were a filter.

 This is the basic structure:
        SELECT column1, column 2, ... FROM table WHERE condition

    - Here are a few examples:
        - You want to get *all* the records from the table USERS, where the field NAME is 'MANUELA':
                SELECT * FROM USERS WHERE NAME = 'MANUELA';

        - You want to get the top 10 records from the table where the field AGE is over 25
                SELECT TOP(10) FROM USERS WHERE AGE > 25;

        - You want to get all the records from the table STUDENTS where the field APPROVED is NOT True:
                SELECT * FROM STUDENTS WHERE approved NOT TRUE;

    See how easy? It's almost like writing in literal English.

 * INSERT: This is how you can write NEW information into the database. I make emphasis on the new part, because if you're trying to rewrite a registry that already has data in it, there is another statement for that (UPDATE). When you use the INSERT statement, you need to make sure you're filling up all of the fields that table requires. You can leave empty fields, but only if they´re not marked as required. This is important, because if you don't do so, the query will fail. The way the INSERT queries are written is very simple: you have to specify the table where you want to insert, then the fields you want to insert into, and then the data.
 
 Here is a basic structure:     
         INSERT INTO table_name (column1, column2) VALUES (value1, value2);

    - Here is an example:
        - You want to insert one record into the table users.The field you want to insert into are the first_name, the last_name and email.
              INSERT INTO users (first_name, last_name, email)
              VALUES ('Manuela', 'Larrea', 'manuela.larrea@example.com');
  
        - You can also insert multiple records into the table. 
                INSERT INTO users (first_name, last_name, email)
                VALUES 
                ('Jane', 'Smith', 'jane.smith@example.com'),
                ('James', 'Brown', 'james.brown@example.com'),
                ('Sarah', 'Johnson', 'sarah.johnson@example.com');
        
* UPDATE: Okay, now the scenario is that you want to modify existing records in a database.You tell the database which table you're changing, what columns you're updating, and with what values. You can also specify conditions to narrow down the updates. If you don't specify conditions, you will update EVERY record on the table, however, if you use the conditions, you will only update the records that match the conditions.

Here is the basic structure:
        UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;

      - Here are a few examples:
        - Updating a single field: Change the email of the user with id
                UPDATE users SET email = 'new.email@example.com' WHERE user_id = 101;

        - Updating multiple fields: UPDATE the price and stock quantity of all the products that have the Electronics category
                UPDATE products SET price = 29.99, stock_quantity = 100 WHERE category = 'Electronics';

        - You can also update fields from a subquery:
                UPDATE orders SET status = 'Shipped' WHERE order_id IN (
                        SELECT order_id FROM order_items WHERE product_id = 101);
        This updates the status of orders that contain a specific product (with product_id 101) to 'Shipped'. 


* DELETE: The DELETE statement is employed to remove records from a table. You indicate the table from which you want to delete, and you can set conditions to target specific records for deletion. This statement is very delicate, because as I said before, you can easily delete the entire database with one line.

Basic structure:
        DELETE FROM table_name WHERE condition;

Here are a few examples:
        - Deleting the user with user_id 100, from the table users.
                DELETE FROM users WHERE user_id = 100;
        
        - Deleting records with a limit: Imagine you only want to delete 5 records that meet the condition:
                DELETE FROM employees
                WHERE termination_date IS NOT NULL
                LIMIT 5;



                