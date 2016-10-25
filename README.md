# SQLiteParser
This Parser comes in handy when you want to write a sql statement easily and smarter.

#Porpouse

Make things easy when you need to write a sql statment for Android SQLite.

# Usage

Copy the [sql](\sql) folder to your Android project.

# Implementation


##### Working with columns.   

    Sql.query()
       .col("A")
       .col("B")
       .col("C", "NICK")
       .col("ALIAS","D", "NICK")
       .cols("E", "F", "G")
       .sum("H").count()
       .max("I")
       .table("YOUR_TABLE", "T")
       .build();

   > Output: SELECT A, B, C AS NICK, ALIAS.D AS NICK, E, F, G, SUM(H), COUNT(*), MAX(I) FROM  YOUR_TABLE T


##### More than one table.   

     Sql.query()
        .col("P", "NAME", "PRODUCT_NAME")
        .col("C", "NAME", "COLOR_NAME")
        .table("PRODUCT", "P")
        .table("COLOR", "C")
        .equal("P", "IDCOLOR", "C","ID")
        .build();

  > Output: SELECT P.NAME AS PRODUCT_NAME, C.NAME AS COLOR_NAME FROM PRODUCT P, COLOR C WHERE P.IDCOLOR = C.ID


##### Where clauses.   
    
     Sql.query()
        .table("TABLE")
        .notExists("1,2,3")
        .build();
  
  > Output: SELECT * FROM TABLE WHERE NOT EXISTS (1,2,3)
  
  
      Sql.query()
         .table("TABLE")
         .greater("THE_COLUMN" , 9)
         .and()
         .smallerEqual("THE_COLUMN", 40)
         .or()
         .equalTrim("TEST", " RAW ")
         .build();
       
   > Output: SELECT  *  FROM  TABLE WHERE THE_COLUMN > 9 AND THE_COLUMN <= 40 OR TRIM(TEST) = 'RAW'
       
##### Deleting.

     Sql.delete("TABLE").smallerEqual("COL", 0).build();     
     
   > Output: DELETE FROM TABLE WHERE COL <= 0
   
##### Inserting.
   
      Sql.insert("TABLE")
         .col("A", 1)
         .col("B", "TEST")
         .build();

> Output: INSERT INTO TABLE(A,B) VALUES(1,'TEST');
         
##### Create Statement

     Sql.create("TABLE")
                .pk("ID")
                .num("CODE")
                .num("TYPE")
                .flo("PRICE")
                .flo("QUANTITY")
                .build();
                
  > Output: CREATE TABLE TABLE (ID INTEGER PRIMARY KEY,CODE INTEGER,TYPE INTEGER,PRICE FLOAT,QUANTITY FLOAT);

         
##### You can bind your cursor, to take advantage of the conversions.

     Cursor cp = Sql.cursor(yourCursor);

        if (cp.binded()) 
            Product product = new Product(cp.num("ID")
                                        , cp.num("CODE")
                                        , cp.flo("STOCK")
                                        , cp.flo("")
                                        , cp.str("NAME"));
                                        
                                        
##### You can create a ContentValues from the Sql class.
       
	 Sql.content().add("NAME", "John")
		          .add("CITY", "New York")
        		  .add("STATE", "New Jersey");
        		  
