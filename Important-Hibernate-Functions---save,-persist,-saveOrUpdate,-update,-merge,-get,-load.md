###save
* Used to save entity in database
* Issue: If we use this without transaction & we have cascading between entities, then only primary key gets save unless we flush the session.
* We should not use save outside transaction boundaries.
* save() method returns generated id immediately, this is possible because primary object is saved as soon as save method is invoked
* If there are other objects mapped to the primary object, they gets saved at the time of committing transaction.
* For the objects in persistent state, save updates the data through update query. This happens when tx.commit() is done.
* save() load entity object to persistent context.

###persist
* Similar to save() & adds entity object to persistent context.
* Persist itself takes care of cascaded objects
* Persist doesn't return anything, persist object is used to get generated identifier.

###saveOrUpdate
* This results into insert or update queries based on data. If the data is present in the database, update will be executed.
* We can use saveOrUpdate without transaction, but issue will mapped objects.
* adds entity objects to persistent cotext & track any further changes. Any further changes can be persisted using persist.

###update
* Should be used only when you know that you are updating the entity information.
* Update doesn't return anything.

###Merge
* Used to update existing values.
* This method creates a copy from the passed entity object & return it.
* This means the returned object is different from passed object.
* Return object can be tracked for further changes but passed object cannot.

 
    Employee emp = (Employee) session.load(Employee.class, 1L);
     emp.age = 66;
     Transaction tx = session.beginTransaction();
     Employee emp1 = session.merge(emp);
     emp1 is tracked for changes
     emp is not tracked for changes
     emp1.age = 100
     emp.age = 50
     tx.commit()


###session.load(Student.class,1L)
1. This always return a proxy object.
2. Proxy Object - hibernate will always prepare some fake object with a id (1L) in memory without hitting db.
3. It won't populate other member information like name & salary.
4. The other information will be populated only when we try to retrieve the other properties.
5. If row is null, it returns ObjectNotFoundException

###session.get(Student.class,1L)
1. It hits database immediately & returns the original object.
2. If row is null, it returns null 

###Performance
1. Load will do little better but if object is not found, it throws exception.

###When to use
Use get to check if entity is existing in db & load only when you are sure that entity is existing & entity non-existing is not an option.
 
  
