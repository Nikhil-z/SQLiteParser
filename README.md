# SQLiteParser
This Parser comes in handy when you want to write a sql statement easily and smarter.

#Porpouse

Make things easy when you need to write a sql statment for Android SQLite.

# Usage

Copy the [sql](\sql) folder to your Android project.

# Implementation


##### Working with columns.   

   >SELECT A, B, C AS NICK, ALIAS.D AS NICK, E, F, G FROM YOUR_TABLE T

    Sql.query()
       .col("A")
       .col("B")
       .col("C", "NICK")
       .col("ALIAS","D", "NICK")
       .cols("E", "F", "G")
       .table("YOUR_TABLE", "T")
       .build();

   >SELECT  *  FROM  YOU_TABLE WHERE TEXT_COLUMN = 'YOUR_VALUE' AND INT_COLUMN = 1

     Sql.query()
        .table("YOU_TABLE")
        .equalStr("TEXT_COLUMN", "YOUR_VALUE")
        .and()
        .equal("INT_COLUMN", 1)
        .build();
   
