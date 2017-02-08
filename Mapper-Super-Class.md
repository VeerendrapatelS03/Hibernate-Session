###Class Structure

 Name           Type              Fields        Transient
  
 SuperBook      (Base Class)      location   

 BookSuperClass (Base Class)      id, name

 ComputerBook   (Entity Class)    language       address

###Notes
* @MappedSuperclass, Annotate each base class with this.
* Only the @Entity class needs to be mentioned in hibernate.cfg.xml.
* The contents of the base class is available in derived this & is automatically mapped into database. 

###@MappedSuperclass
* Annotate each base class of persisted entity with this.
* All non-transient field from base classes will be mapped to database

###@Transient
* Any class member that is annotated with this will not be hibernated/persisted into database.

###Mapping configuration in hibernate.cfg
* Mention just the derived class here