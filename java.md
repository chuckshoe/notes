# JAVA notes:
# TOPICS
  - [String, StringBuilder, StringBuffer](#string-stringbuilder-stringbuffer)
    - [String](#string)
    - [StringBuilder](#stringbuilder)
    - [StringBuffer](#stringbuffer)
    - [Difference](#difference)
  - [Interface & Abstract class](#interface-and-abstract-class)
    - [Interface](#interface)
    - [Abstract Class](#abstract-class)
    - [Interface vs Abstract class](#interface-vs-abstract-class)

## String StringBuilder StringBuffer
#### String
  - String is immutable ( once created can not be changed )object.
  - The object created as a String is stored in the Constant String Pool .
  - Every immutable object in Java is thread safe ,that implies String is also thread safe . String can not be used by two threads simultaneously.
  ```
  String demo = ” hello ” ; // The above object is stored in constant string pool and its value can not be modified.  

  demo=”Bye” ; //new ”Bye” string is created in constant pool and referenced by the demo variable

  // ”hello” string still exists in string constant pool and its value is not overrided but we lost reference to the ”hello”string
  ```

#### StringBuilder
  - StringBuilder is same as the StringBuffer , that is it stores the object in heap and it can also be modified .
  - The main difference between the StringBuffer and StringBuilder is that StringBuilder is also not thread safe. StringBuilder is fast as it is not thread safe .
  ```
  StringBuilder demo2= new StringBuilder(”Hello”); // The above object too is stored in the heap and its value can be modified  

  demo2=new StringBuilder(”Bye”); // Above statement is right as it modifies the value which is allowed in the StringBuilder
  ```

#### StringBuffer
  - StringBuffer is mutable means one can change the value of the object.
  - The object created through StringBuffer is stored in the heap .
  - StringBuffer has the same methods as the StringBuilder , but each method in StringBuffer is synchronized that is StringBuffer is thread safe.  
  Due to this it does not allow two threads to simultaneously access the same method . Each method can be accessed by one thread at a time.  
  But being thread safe has disadvantages too as the performance of the StringBuffer hits due to thread safe property. Thus StringBuilder is faster than the StringBuffer when calling the same methods of each class.StringBuffer value can be changed , it means it can be assigned to the new value.
  - String Buffer can be converted to the string by using toString() method.
  ```
  StringBuffer demo1 = new StringBuffer(”Hello”) ; // The above object stored in heap and its value can be changed

  demo1=new StringBuffer(”Bye”); // Above statement is right as it modifies the value which is allowed in the StringBuffer
  ```
#### Difference
  - Storage Area: String - Constant String Pool, StringBuilder - , StringBuffer -
  - Modifiable: String - No (immutable), StringBuilder - Yes( mutable, StringBuffer - Yes( mutable)
  - Thread Safe: String - No, StringBuilder - No, StringBuffer - Yes
  - Performance: String - Fast, StringBuilder - Fast, StringBuffer - Slow


## Interface and Abstract class
#### Interface  
  - A superclass defines common behavior for related subclasses. An interface can be used to define common behavior for classes (including unrelated classes).
  - Interface defines a sort of contract.
  - you can implement multiple interfaces
  - have to implement every method in the Interface
  - An interface is a class-like construct that contains only constants and abstract methods.
  - As with an abstract class, you cannot create an instance from an interface using the new operator.
  - Since all data fields are public static final and all methods are public abstract in an interface, Java allows these modifiers to be omitted. Therefore the following inter-face definitions are equivalent:
  ```
  public interface T {
    public static final int K = 1;
    public abstract void p();
  }
  ```
  Equivalent to
  ```
  public interface T {
    int K = 1;
    void p();
  }
  ```

#### Abstract class
  - a class can implement only one abstract class
  - The constructor in the abstract class is generatlly defined as protected, because it is used only by subclasses. When you create an instance of a concrete subclass, its superclass’s constructor is invoked to initialize data fields defined in the superclass.
  - `abstract method in abstract
class`: An abstract method cannot be contained in a nonabstract class. If a subclass of an abstract superclass does not implement all the abstract methods, the subclass must be defined as abstract. In other words, in a nonabstract subclass extended from an abstract class, all the abstract methods must be implemented. Also note that abstract methods are nonstatic.
  - `object cannot be created from
abstract class`: An abstract class cannot be instantiated using the new operator, but you can still define its constructors, which are invoked in the constructors of its subclasses.
  - `abstract class without abstract
method`: A class that contains abstract methods must be abstract. However, it is possible to define an abstract class that doesn’t contain any abstract methods. In this case, you cannot create instances of the class using the new operator. This class is used as a base class for defining subclasses.
  - `concrete method overridden
to be abstract`: A subclass can override a method from its superclass to define it as abstract. This is very unusual, but it is useful when the implementation of the method in the super-class becomes invalid in the subclass. In this case, the subclass must be defined as abstract.
  - `superclass of abstract class
may be concrete`: A subclass can be abstract even if its superclass is concrete. For example, the Object class is concrete, but its subclasses, such as GeometricObject , may be abstract.
  - `abstract class as type`: You cannot create an instance from an abstract class using the new operator, but an abstract class can be used as a data type. Therefore, the following statement, which creates an array whose elements are of the GeometricObject type, is correct.
  ```
  GeometricObject[] objects = new GeometricObject[10];
  ```
  You can then create an instance of GeometricObject and assign its reference to the array like this:
  ```
  objects[0] = new Circle();
  ```
  - `abstract method`: it is a placeholder function i.e. can't have a body. The subclass must either implement it or the method should be abstract in the subclass.
#### Interface vs Abstract class
  - Variables:
    - Abstract class: no restrictions
    - Interface: all variables must be public static final
  - Methods:
    - Abstract class: no restrictions
    - Interface: All methods must be public abstract instance methods
  - Constructors:
    - Abstract class: Constructors are invoked by subclasses through constructor chaining. An abstract class cannot be instantiated using the new operator.
    - Interface: No constructors. An interface cannot be instantiated using the new operator
  - An interface can inherit other interfaces using the extends keyword. Such an interface is called a subinterface.  
  An interface can extend other interfaces but not classes.  
  A class can implement multiple interfaces, but it can only extend one superclass.
  - All classes share a single root, the Object class, but there is no single root for interfaces.
  - ***NOTE:***  Like a class, an interface also defines a type. A variable of an interface type can reference any instance of the class that implements the interface. If a class implements an interface, the interface is like a superclass for the class. You can use an interface as a data type and cast a variable of an interface type to its subclass, and vice versa.
  - ***NOTE:*** Class names are nouns. Interface names may be adjectives or nouns.
  - ***DESIGN GUIDE:*** In general, a strong is-a
relationship that clearly describes a parent-child relationship should be modeled using classes.  
A weak is-a relationship, also known as an is-kind-of relationship, indicates that an object possesses a certain property. A weak is-a relationship can
be modeled using interfaces.
  - ***NOTE:*** Generally , interfaces preferred over abstract class. One reason being, we can implement multiple interfaces; so interfaces more flexible.
