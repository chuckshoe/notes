# JAVA notes:
# TOPICS
  - [Interface & Abstract class](#interface-&-abstract-class)
    - [Interface](#interface)
    - [Abstract Class](#abstract-class)
    - [Interface vs Abstract class](#interface-vs-abstract-class)

## Interface & Abstract class
#### Interface  
  - A superclass defines common behavior for related subclasses. An interface can be used to define common behavior for classes (including unrelated classes).
  - Interface defines a sort of contract.
  - you can implement multiple interfaces
  - have to implement every method in the Interface

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
