###HQL - Hibernate Query Language
* Object oriented language
* Similar to SQL
* HQL works on persistent objects & properties rather than tables
* This mechanism makes database query portable.
* Takes advantage of Hibernate's SQL generation.
* Makes use of hibernate's caching infrastructure. 

###FROM Clause
* Load complete persistent objects into memory
* from Student
* from my.Student - If you need fully qualified class name in HQL

    String hql = "FROM stdinfo";
    Query q = session.createQuery(hql);
			
    List<Student> res = q.list();
    for (Student s: res){
	System.out.println(s);
    }


###AS Clause
* Assign aliases to the classes in HQL queries
* AS keyword is optional FROM Student S

###SELECT Clause
* Provides more control over result set
* "SELECT S.name FROM Student S", name is a property of Student

###WHERE Clause
* Narrow down specific objects from storage
* "FROM Student S WHERE S.age = 20"

###ORDER BY Clause
* Sort HQL queries - ASC/DESC

###GROUP BY Clause
* This lets hibernate pull information & group it based on a value of an attribute.
* This is used more for aggregate value
* "SELECT SUM(S.marks), S.name FROM Student S GROUP BY S.name"
  
###UPDATE Clause
* Provides an option to update a specific entry.

###DELETE Clause
* Delete one or more objects

###INSERT Clause
* HQL supports INSERT INTO clause only where records can be inserted from one object to another.
* "INSERT INTO Student(name,marks) SELECT name,marks FROM OLD_STUDENT" 
 
###Aggregate Methods
* avg - average of property values
* count - property count
* max, min, sum 

##Pagination using Query
###setFirstResult
###setMaxResults

###JOIN
* HQL supports inner joins, left outer join, right outer join & full join.
* Have Student class & Address Class. Address is member of Student class
* "SELECT S.name, A.CITY from Student S INNER JOIN S.address A" 