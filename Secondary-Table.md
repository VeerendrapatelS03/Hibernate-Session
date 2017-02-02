##Introduction
* The database might have huge number of columns.
* Now, not always you need all the columns. 
* The frequently needed items will be few.
* We can break down data into multiple parts.
* The frequently accessed data can be in fast access memory & less frequently accessed data in cheaper memory.
* To achieve this, hibernate provides a mechanism to break-down a class into multiple tables. This concept is known as secondary table. 


###@SecondaryTable(name = "customer_details")

* Class will be mapped to table in database. 
* Number of columns can be large. 
* Not always you want all piece of information. Performance.
* Some columns are frequently accessed relative to others. 
* So, we may want some piece of information in fast table compared to others. 

Using secondary table concept we can split class into multiple tables    