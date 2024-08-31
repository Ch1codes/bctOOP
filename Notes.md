Constant member functions are declared by placing const after the parameter list and before function body. 
a non constant function cannot be called by constant object because it can change the object's value or data member value.
In rare cases, constant functions need to change the value of internally used unobservable data member. to the user the function appears as if there is no change value of the object but some detail the user cannot directly observe is updated. this is called logical constantness.
cpp provides const_cast operator which is used in the constant function to remove the constantness and update those types of members. Mutable is alternative to this. 
a mutable data member is always modifiable even with constant member function or constant object.
if a function declared as a friend is in another scope, the scope should also be mentioned. the mentioned friend function can be in another namespace or a member of a class. 
friend void A::add();
Operator function that accepts a built in type as its first operand cannot be a member function.
the difference between copy consturctor and assignment operator is copy consturctor initializes the initialized memory during object creation whereas the assignment operator assigns copies to to the already created object.
In C++, access specifiers are keywords that set the accessibility of classes and their members (attributes and methods). They control how the members of a class can be accessed from outside the class
If we override a function name in derived class which is in overloaded form in base class than non of the functions of the base class are accessible after overriding without using the base class name.
When the pointer to objects are involved in calling function the selection of the function is done at the runtime because the address information is only known at runtime. this is runtime polymorphism. 
the runtime polymorphism in cpp is possible because the base class pointer can hold the address of its own class as well as the address of its derived class.
abstract classes can be used as framework upon which new classes can be built to provide new functionality.
a version of a template for a specific template argument is called specialization.
when explicitly specifying the template type argument, the template version is called even when the overloaded function with that type of argument exists. 
class template differ from function templates in the way they are instantiated. calling the function using specific argument type creates a function but to instantiate a class, we must pass the template arguments during object declaration. 
we can specify the value in the template specification almost similar to normal function parameter but the value must be known at compiler time
even if we are not supplying the template argument, we must use the empty angle brackets without the type to show it is a class template. 
while declaring specialization, general template must be declared before any specialization.
The catch blocks are to be organized in such a way that specific exceptions are handled by the earlier catch blocks and the general case that is base class exception is to be placed at last. 