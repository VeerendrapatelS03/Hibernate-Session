##Hibernate Configuration can be done using two approaches
1. XML Based configuration
2. Annotation Based Configuration

##Configuration Details

###hibernate.dialect
Dialect that Hibernate should use to talk to database. For e.g. 'org.hibernate.dialect.MySQLDialect'. 

###hibernate.connection.driver_class
The driver required by jdbc layer of hibernate to talk to database. For e.g. 'com.mysql.jdbc.Driver'.

###hibernate.connection.url
Which database to connect.

###hibernate.connection.username
Valid username in database for collection.

###hibernate.connection.password
Password required to connect

###hbm2ddl.auto
update - will create table if not present.
create - will create table no matter what.

###mapping class
Here we mention the classes that we want to map to database.


