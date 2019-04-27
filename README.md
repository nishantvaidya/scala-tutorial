# scala-tutorial

## Case Classes

  case class Person( name :String, age:Int)
  
  - Case classes are perfect for ligh weight data hold oboject.
  - Class parameter promoted to field.
       var nishant = new Person("nishnat", 22)
  - sensible to tostring method.
   - nishant.toString()
    - nishant will automatically delicate to toStirng method() // syntatic sugar,
    - equal and hashcode automatically implement out of the box.
        nishant1 == nishant2 will return always true.
       - Case class has handy copy method.
           var nishant3 = nishant2.copy(age=22)
        - case class have companion object.
            var nishant4 = nishant 3
         - case class can instantiated without new keyword and use apply method internally.
            var person = Person("Nishant",33)
          - case classes are serializable. it is very usefull in distributed system.
          - case classes have extractor pattern. it can be used for pattern matching.
          - case Object have same property similar to case classes except they do not have companion object.
  ## Exceptions :
   -  Everything in scalas is exception except  try , catch and finally.
      val excption = throw new NullPointerException()
   -  
      def getInt(withExceptions:Boolean):Int = {
       if(withExceptions) = throw new Exception("exception") else 42 
       try{
        val value = getInt(true);
       } catch{
        case  e : RunTimeException =>  println("exception")
      }finally {
      
      // optional and does not influence return type. it is side effect.
      println("finally")
      }
      
   - Define your own exception
     calss myException extends Exception // can have variable ,method etc.
     val exception = new myException
     throw new exception
