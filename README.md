# SQL-Internship-Task-8
  The Objetive of this Task focusing on the creation and implementation of Stored Procedures and Functions to achieve modular and reusable SQL code.  <br>
  
# 📝 Deliverables
The files below contain the SQL scripts for the required deliverables <br>

# 🛠️ 𝗧𝗼𝗼𝗹𝘀 𝗨𝘀𝗲𝗱 
  * Database :  E-Commerce Database.
  * Environment: [ MySQL Workbench ].
  * The database structure includes four tables. <br>
    A. Customers (Customer_Id, Full_Name, Contact, Email, Address) <br>
    B. Products (Product_Id, Product_Name, Category, Price, Stock_quantity) <br>
    C. Orders (Order_Id, Customer_Id, Product_Id, Order_Date, Amount, Payment_Type) <br>
    D. Payments (Payment_Id, Order_Id, Payment_Status, Payment_Date) <br>

# 𝕊𝕋𝕆ℝ𝔼 ℙℝ𝕆ℂ𝔼𝔻𝕌ℝ𝔼. 
  A stored procedure in MySQL is a set of SQL statements that are saved in the database and can be reused whenever required.   <br>
  Stored procedures are a powerful way to perform repetitive or complex operations in a database.<br>
  Once created, they can be executed with a single call and can take parameters to customize their behavior.<br>

  * 𝐊𝐄𝐘 𝐅𝐄𝐀𝐓𝐔𝐑𝐄𝐒.<br>
    - ʀᴇᴜꜱᴀʙʟᴇ ᴄᴏᴅᴇ :   Write the logic once and use it multiple times.<br>
    - ꜱᴇᴄᴜʀɪᴛʏ : Access can be granted or revoked for executing the procedure,hiding the underlying SQL code. <br>
    - ʀᴇᴅᴜᴄᴇᴅ ɴᴇᴛᴡᴏʀᴋ ᴛʀᴀꜰꜰɪᴄ : As the logic runs on the server, less data needs to be sent over the network.<br>
    
  * 𝐏𝐚𝐫𝐚𝐦𝐞𝐭𝐞𝐫𝐬 𝐢𝐧 𝐒𝐭𝐨𝐫𝐞𝐝 𝐏𝐫𝐨𝐜𝐞𝐝𝐮𝐫𝐞𝐬 - <br>
    - 𝐼𝒩 : Input parameter (default type, passes a value to the procedure).  <br>
    - 𝒪𝒰𝒯  : Output parameter (returns a value to the caller). <br>
    - 𝐼𝒩𝒪𝒰𝒯 : Acts as both an input and an output parameter. <br>

  * 𝐄𝐗𝐏𝐋𝐀𝐍𝐀𝐓𝐈𝐎𝐍 <br>
    - ​🇩​​🇪​​🇱​​🇮​​🇲​​🇮​​🇹​​🇪​​🇷​ // <br>
    Changes the delimiter to allow multi-line statements in the stored 
    procedure.<br> 
     In MySQL, the DELIMITER is a command used to change the default 
    statement delimiter from a semicolon (;) to another symbol or set of 
    characters. <br>
     By default, MySQL interprets a semicolon as the end of an SQL 
    statement. <br> 
     However, when defining stored procedures, triggers, or functions, the SQL 
    block often contains multiple semicolons.  <br>
     To avoid confusion and allow these blocks to be written correctly, the 
    DELIMITER command temporarily changes the delimiter. <br>

  * 𝐒𝐘𝐍𝐓𝐀𝐗 <br>
    ```sql
    DELIMITER // 
    CREATE PROCEDURE procedure_name (Parameters) 
    BEGIN 
          -- SQL statements 
    END // 
    DELIMITER ; 
    ```
    -- Call to Prodcedure <br>
    ```sql
    CALL procedure_name(parameter1, parameter2, ...) ;
     ```
     ---
  
    -- Ex. Create procedures Without parameter <br>
     ```sql
      DELIMITER //
      CREATE PROCEDURE GetData_Customer()
      BEGIN
      SELECT * FROM Customers ;
      END ;
      DELIMITEER ;
     ```
     -- Call to Procedures & Display to Customer Data <br>
     ```sql
     CALL GetData_Customer() ;
     ```
     ---

     -- Ex. Create Procedures with `IN` Parameter. <br>
     ```sql
      DELIMITER //
      CREATE PROCEDURE GetpaidStatus(IN Pay_Status VARCHAR(10))
      BEGIN
          SELECT * FROM Payments WHERE Payment_Status = Pay_Status;
      END //
      DELIMITER ;
     ```
  
    -- Call To Procedures Show all paid Payment Status. <br>
    ```sql
    CALL GetpaidStatus('Paid') ;
    ```
    ---
  
    -- Ex. Create procedures With parameter And Use of `CASE` statment . <br>
    ```sql
    DELIMITER //
    CREATE PROCEDURE  CheckTaxs(IN Prices DECIMAL(10,2))
    BEGIN
    SELECT Price,
    CASE 
    WHEN 100000 >= prices THEN '28%'
    WHEN 50000 >= Prices THEN '24%'
    WHEN 25000 >= Prices THEN '18%'
    WHEN 25000 < Prices THEN '17%'
    END AS Taxs
    END ; 
    DELIMITER ;
    ```
    -- Call to procedure then Dispaly Tax <br>
    ```sql
    CALL CheckTaxs(120000) ;
    ```
     ---
    -- Ex. Create procedures With `OUT` parameter <br>
    ```sql
     DELIMITER //
     CREATE PROCEDURE CountproductCategory(OUT n)
     BEGIN 
     SELECT COUNT(*) FROM Orders;
     END ;
     DELIMITER ;
    ```
    -- 
    ```sql
     CALL CountproductCategory() ;
    ```
    ---
    -- Ex. Create procedures With `INOUT` parameter 
    ```sql
    DELIMITER // 
    CREATE PROCEDURE Addition(INOUT C INT,IN B INT) 
    BEGIN 
    SET C=C+B; 
    END // 
    DELIMITER ; 
    ```
    -- Call to Addition Function <br>
     ```sql
     CALL Addition(10);
     ```
  


    












  
