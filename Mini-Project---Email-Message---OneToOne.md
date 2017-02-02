##Models

###Email
* This is in OneToOne relationship with Message 
* @OneToOne(mappedBy = "email") - A column is created in Message Table which points to email.

###Message
* This is in OneToOne relationship with Email

