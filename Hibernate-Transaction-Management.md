###Introduction
A transaction represents a unit of work. It may consist of multiple smaller steps. If one step fails, the whole transaction fails. And, rollback happens to revert already done changes. 
 - Atomicity -Individual or Irreducible series of transaction. If any of it doesn't happen. Everything rollsback
 - Consistancy - Data must be updated based on constraints. 
 - Isolation - Changes in one transaction visibility to others
 - Durability - Transactions that has happened should be permanent

The methods of transaction interface are as follows 
* begin() - starts new transaction
* commit() - ends the work
* rollback() - forces this transaction to rollback
* setTimeout() - it sets transaction timeout for any transaction 
* isAlive() - checks if the transaction is alive
* wasCommitted() - checks if a transaction is committed successfully 
* wasRollback() - checks if a transaction is rollbacked successfully

###Important terms
* transient - A new instance of a persistent class which is not associated with a Session & has no representation of databse
* persistent - An instance with database representation
* detached - Once the Hibernate session is closed, the object become detached.
