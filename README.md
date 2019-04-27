### scala-tutorial
## Scala- basics

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
   -  Everything in scalas is exception except  try , catch and finally
   val excption = throw new NullPointerException()
   -  def getInt(withExceptions:Boolean):Int = 
   {
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
## Packaging and Imports
- Package is not an expression.
- Pacages members are accessible by their simple name.
- packages object is created to declare constant out side all the classes and accessible to all classes.There can be only one package object per packages.
 package object <package_name> {
  def sayHello():Unit = println("hello")
  val SPEED_PER_KM : Int = 50
- import all classes in pacakge: import com.test._ (Underscore is used to import all classes)
- You can import a set of class using import com.test.{test1, test2, test3 => hello3 // test 3 refer with hello3 classs. Use if have class name conflict }
- if both classess in import same then comiple take first import as class. Use fullyqualified class other wise
- import by other name import java.sql.{Date => sqlDate}
 } 
 - default imports are automatically imported package. java.lang -string, object, exception. Scala package - Int,Nothing,Function , scala.predef - println, ???
