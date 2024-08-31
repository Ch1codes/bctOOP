#### Constructors
An implicit no-argument constructor is built into the program automatically by the compiler and it's this constructor that created the objects even though we didn't define it in the class, this no argument constructor is called default constructor. If this weren't created automatically by the constructor you wouldn't be able to create objects of a class for which no constructor was defined. 
```cpp
distance():meter(0), inches(0.0){}
//initialization of data members in the default constructor so that we can be sure of the values the data members may be given. 
```

Every call to a member function is associated with a particular object (unless
it’s a static function; we’ll get to that later). Using the member names alone (feet and
inches), the function has direct access to all the members, whether private or public, of that
object. It also has indirect access, using the object name and the member name, connected with the dot operator (dist1.inches or dist2.feet) to other objects of the same class that are
passed as arguments.

#### Default copy constructor
A no-argument constructor can initialize data members to constant values and a multi argument constructor can initialize data members to value passed as arguments. 
An object can also be initialized with another object of same type for which a special constructor is not needed as one is already built on all classes called default copy constructor which takes a single argument(object of the same class)
We can use default copy constructor through two ways:
```cpp
className obj2(obj1);
className obj3=obj1;
```

#### Structure and Classes\
The formal difference between class and struct is that in a class the members are private by default, while in a structure they are public by default. 
You can define a structure using the keyword private too but structures are favored to group only data while classes to group both data and functions. 

#### Classes, Objects and Memory
Each object has its own separate data items but all the objects of a given class use the same member functions. The member functions are created and placed in the memory only once when they are defined in the class definition since the functions for each object are identical. Despite being shared by all the objects of the class, there is no conflict because only one function is executed at a time. 
Data is placed in memory when each object is defined, so there is a separate set of data for each object. 

#### Static Class Data
If a data item in a class is declared as static, only one such item is created for the entire class, no matter how many objects there are. A static data item is useful when all objects of the same class must share a common item of information. Its lifetime is in the entire program continuing to exist even if there are no objects of the class. 
Static member data requires two separate statements: one for variable's declaration in the class definition but static member data variable is actually defined outside the class in the same way as a global variable. This two part approach is used so that the static member data doesn't violate the idea that a class definition is only a blueprint and does not set aside any memory. Putting the definition of static member data outside the class also serves to emphasize that the memory space for such data is allocated only once, before the program starts to execute and that one static member variable is accessed by the entire class. 

#### const and Classes
A const member function guarantees that it will never modify any of its class's member data. 
```cpp
returnType functionName() const{
definition;
}
```
If there is a separate function declaration, const must be used in both declaration and definition.
Member function that do nothing but acquire data from an object are obvious candidates for being made const. 
Making the argument const while passing it to a function by reference, the function cannot modify it. 
When an object is declared as const, you can't modify it. It follows that you can use only const member functions with it, because they're the only ones that guarantee not to modify it. 
