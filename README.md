### scala-tutorial
## Scala- basics
 - Value , variable and Type
   -  val x: Int = 42 //  val is immutable variable similar to final and can not be modified or reassigned.
   -  var x:Int = 32  // var is mutable and can be re-assigned.
   -  Type of val are optional and can be infered by compiler. compiler can detect automatically.
   -  semicolon(;) is optional and end of expression. It should be discourage in scala.
   -  Int, char, Boolean, String, Long,Short, Float,Double. Long should have suffix'L' and 'f' at end of float value.
   -  var is side effect as assign expresssion will get evaulated.
   -  Functioanl programming prefer val over var. Same for scala.
 - Expressions
   -  expression are evaulated to value. var x = 1+2 , var y += 3
   -  {>>>} is right shift operator with zero padding.
   -  Instruction is something you will tell to computer to do . Imperative programming like java, python use heavily.
   -  expression compute to a value. everything in scala is expression. Look at if and else as it return value so it is expression in scala however but not in java.
      var conditionvalue = if(condition) 3 else 5
   -  NEVER USE WHILE LOOP in SCALA iNSTEAD USR RECURSION.WHILE LOOP USED iN IMPERATIVE PROGRAMMING LIKE JAVA. NEVER EVER USE LOOP.
   -  Unit is equivale to void and it means nothing.
   -  code blocks are special kind of expression. val codeBlock = {}. value of code block is last expression. all variables visibilty inside block only.
   -  Instructions are excuted and expressions are evaluated.
  - Function
    -  def aFunction(a:String, b:String):String = a+ "" + b ; or {a+ "" +b}
    - Functional is also expression.
    - parameterless function can also be call without paranthesis.  var srt :String = "test".toString.
    - When you need loop use recursive function. This is important in functional programming. Recursive function always return type. You can user 'Unit' return type if nothing.
    - code block can also have auxillary function def aFunction(a:Int):Int= {def auxFunction(a:Int):Int =a auxFunction(a) }.Aux function can be use to define return type of parent function.
   - Type Inference
     -  What the compiler knows. compiler does able to figure out type.
     -  Compile is also able to figure type of function and variable but not in recursive function.
   - Stack and Tail Recursion
     -  def factorial(n:Int):Int = if (n <= 1) n else n *factorail(n-1)
     -  Recurisve function use call stack in scala or stack frame for execution
     -  if you call with big number then it will throw stack over flow error, we have to write differently
     -   def factorial(n:Int):Int = {def factHelper(x:Int, accumulator:Int):Int = if(n==1) n else factHelper(x-1,x*accumulator)
     facthelper(n,1)}
     - So this problem is solved using auxillary function and accumulator
     - above use tail recursion. Tail recursion is last expression in function.
     - you can use @tailrecursion annotatoin above method to see if wrote correctly
   - Call BY Name or Value
     -  def calledByValue(x:Long):Unit = {println(x)}
     -  def calledByName( x: =>Long):Unit = {println(x)}
     - println(calledByValue(Sytem.nanotime())// Inside function can be evaluated and value passed.
     - println(calledByName(Sytem.nanotime())// Inside function does not  evaluated instead function passed.
     - you can see difference if you print 2 times every function. value function will return same value each time but name does not
   - Default or Named Arguments.
     -  def add(a:Int, b: Int = 1<<1 is default value>>) : a+d ; // you can call add(5).
     -  Default value should be in last arguments otherwise compile will not recognise else call with names add(a=5, b= 1).
     
## Object oriented programming in scala
   - Basic.
     -  class Person  // person:Person = new Peson().
     -  class Person(name:String, age:Int) // This is consructor.
     - name and age are class parameters and not member variable so you can not access use "." like person.age
     -  if need member variable declare inside else use val. class Person(name:String, val age:Int)
     -  if you have parameter with same name then use this.name to access class parameter name.
     - overloading is method with same name but different signature( default parameter or different return type but not return type only)
     - constructor is declared using def this(name:String) = this(name,0)
     - constructor can only call other constructor and nothing else.  def this(): this("nishant")
     - This problem can be solved through passing default value in class parameter so no need of auxillary this constructor.
  - Syntatic Sugar Method notation.
     -  a.add(b) can also be called as println(a add b) and this is called infix style and work with single parameter. This is natural language way calling method.
     -  you can use + , * or any other mathmetical operator as method name . you can use a.+(b) or printl(a + b). All operator are method in scala.
     - prefix notation is all about unary operator. var x = -1 is equivalent var x = 1.unary_-. unary_ prefix works with only + ,-, !,~
     - post prefix notation a.toString equivalent a toString . Post prefix work only for method without parameter.
     - apply method can be declared in class and you can call using classname() and this is equivalent to classname.apply()
   - Scala Objects.
     -  scala object are different concepts. class does not have class level functionality.
     -  object Person{val EYES=2} . object does not recieve parameters.
     -  scala object are singleton and it is own type so equal always return true.
     - you can write object and class with same name and this is called companion.  obect person = {} and class person = {}
       var nishant = person // this is singleton instance of object but var vaidya = new Person() is instance of class. class instances are not equal as they are different instances.
     - companion can access each other private members.
      - Scala application are object with main method . and can be write using extends App.
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
