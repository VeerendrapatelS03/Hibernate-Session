###Application Details
* Employee & Meetings. Each employee can attend many meetings. Each meeting can be attended my many employees.
* This is implemented by Set of meeting in in Employee class & Set of employee in Meeting class.
* We will user Hibernate to map classes having collection.
* This is a natural ManyToMany relationship between Employee & Meeting.

###Steps to Hibernate such relationship
* @Column - Default column name is field name, another way to assign it is this.
* @Cascade - Related tables, entry read/write/update rollback if not complete
* @ManyToMany - Annotating collection (Set in this case with) with this.
* @JoinTable - Create a third mapping table OR intermediate table for connecting other two tables.
* @JoinColumn - The new columns of the intermediate table.  

###Cascade Options
* EVICT
* SAVE
* UPDATE
* ALL - Rollback if all the related tables is not updated. 