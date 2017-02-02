##Introduction
Not only one key, but group of keys together working as primary key. This is known as compounded primary key.

###Terms expected to be known
* Serializable - Marker Interface. A class implementing this is capable of converting object into bitstream. This is required since primary key comparison will be done in database.


###There are 3 ways to achieve it
* Annotating members of primary key with @Id
* Create a separate class with Primary Key Elements & use @EmbeddedId
* Using Embeddable class

###1st Approach
* Annotating each member with @Id
* Mentioning the Id class with @IdClass
* Id Class should always be serializable 
* Constructor, setter-getter, equals & hashcode implemented.
* Mostly converting existing stuff into compounded primary key

###2nd Approach
* Annotating the primary key with @EmbeddedId
* Primary class should be serializable
* Constructor, setter-getter, equals & hashcode implemented.
* Absolutely nothing needs to be mentioned in Key Class. 
* Mostly primary class definition library is not editable

###3rd Approach
* Annotate the Primary Key class with @Id
* Primary Key Class should be @Embeddable & Serializable 
* Constructor, setter-getter, equals & hashcode implemented.

Notes:
* Embedded Class should be serializable 
* Should have implemented constructors, setter-getters, hashcode & equals
