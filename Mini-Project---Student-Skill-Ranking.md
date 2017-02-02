##Models

###Student
* Student will be acting as an observer - somebody who ranks
* Student will be acting as a subject - somebody who will be ranked 

###Skill
* The criteria/agenda on which observer will be ranking the subject.

###Ranking
* Providing some ranking for skill for subject by observer. It contains subject, observer, skill & rank.

##Relationships
* ManyToOne relationship between Subject & Ranking  - One subject/student ranked by many observers/student.
* ManyToOne relationship between Observer & Ranking - One observer/student ranks many subject/student.
* ManyToOne relationship between Skill & Ranking    - Ranking will be done for many skills
 
##Mini Assignment
Make sure that before saving an entity, if object is not persisted before. 