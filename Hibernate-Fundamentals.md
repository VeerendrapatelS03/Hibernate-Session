###Steps
* Create a POJO.
* Have an id field here.
* @Entity on the class - When hibernate sees the @Entity, it creates a corresponding database table for that class.
* Hibernate uses the field annotated with @Id as primary key.
* @GeneratedValues tells Hibernate/Database how to generate value value for the primary key.

###Using hibernate in application
* Create sessionFactory object.
* Get session out of it.

###SessionFactory
* Based on Factory Design Pattern. 
* Capable of generating objects.
* In this case capable of creating session objects.

###Sessions
* They have all the information required to access database.
* Placeholder for all the objects that will be mapped to database.
* On doing commit, all the objects will be mapped to database.