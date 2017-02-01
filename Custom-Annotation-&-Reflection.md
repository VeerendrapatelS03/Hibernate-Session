* Frameworks define annotation. This is done using @interface
* Application uses the defined annotation. Application use @YourDefinedAnnotation to tell framework to to deal with.
* Framework finds places where the annotation was used.And, it interprets accordingly. This is achieved using Reflexions.

##Annotations

##Types of Annotations
* Marker Annotation - No arguments in annotation
* Single-Value Annotation - Accepts Single arguments
* Multi-Value Annotation - Accepts multiple values as arguments

##Create a Basic Annotation
* Annotations are created by using @ sign, followed by the keyword interface, and followed by annotation name.
  `@interface MyAnnotation{ ...}`
* Members can be declared but looks like methods. We should not provide implementation for these members.
 
    @interface Bean{
      Sting name();
    }


    @Bean(name="abc")

* All annotations extends java.lang.annotation.Annotation interface. 
* Use 'default' to assign default value to member

##Retention Policy
* Annotation retention policy. The constants of this enumerated type describe the various policies for retaining annotations. They are used in conjunction with the Retention meta-annotation type to specify how long annotations are to be retained.
  1. CLASS - Annotations are to be recorded in the class file by the compiler but need not be retained by the VM at run time. Appear in decompiled class, but can't be inspected at run-time with reflections like getAnnotation()
  2. RUNTIME - Annotations are to be recorded in the class file by the compiler and retained by the VM at run time, so they may be read reflectively.
  3. SOURCE - Annotations are to be discarded by the compiler. Won't appear in decompiled class.

##Important Functions
###getAnnotations(AnnotationName.class)
Checks if the class/function have the annotation 'AnnotationName', if present returns an annotation object.
Use it on class to get class annotation & on method to get method annotation. Can work on .class & .getMethod

###getMethod("methodname")
Checks whether method is present in class & returns method object if it is.  
 
