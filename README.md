# SQLiteParser
This Parser comes in handy when you want to write a sql statement easily and smarter.

#Porpouse

Make things easy when you need to write a sql statment for Android SQLite.

# Usage

Copy the [sql](\sql) folder to your Android project.

# Implementation


##### Working with columns.   

   >SELECT A, B, C AS NICK, ALIAS.D AS NICK, E, F, G, SUM(H), COUNT(*), MAX(I) FROM  YOUR_TABLE T

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

##### More than one table.   

   >SELECT P.NAME AS PRODUCT_NAME, 
   >       C.NAME AS COLOR_NAME 
   >  FROM PRODUCT P, 
   >       COLOR C 
   > WHERE P.IDCOLOR = C.ID

     Sql.query()
        .col("P", "NAME", "PRODUCT_NAME")
        .col("C", "NAME", "COLOR_NAME")
        .table("PRODUCT", "P")
        .table("COLOR", "C")
        .equal("P", "IDCOLOR", "C","ID")
        .build();
   
