# object_oriented_data_structures_in_cpp
## Notes and code for Coursera course 
[https://www.coursera.org/learn/cs-fundamentals-1]
## Week 1
### C++ language syntax 
- c++ is a strongly typed language, every variable has a type, name, value and mem location
- c++ has 2 variable types, primatives and user defined
- primatives: int, char, bool, float, double (usually will use these instead of float), void (denotes absence of value)
- user defined types - common std values: std::string, std::vector, std::unsignedint
- c++ programs must contain a starting point

```c++
int main() {
    return 0
}
```

### Writing, compiling and debugging code 
- Interactive development environment (IDE)
    - I am choosing to use vs code on Ubuntu Linux
- C++ classes 
    - C++ Classes ecapsulate data and associated functionality (properties and methods) into an object
    - encapsulation encloses data and functionality (knows and does)    

### Implementation v. header files 
- with c++ the header file (.h) is the interface and is defined seperately from the implementation (.cppfile)
- c++ header file - declares all member variables, declares all member functions. The names of what ourclass knows and does, but not how it does them
- Header file is akin to an api
- the top of a header file has #pragma once, instructs compiler to compiled once

### Header file (.h file)

``` c++
// All header (.h) files start with "#pragma once":
#pragma once

// A class is defined with the `class` keyword, the name
// of the class, curly braces, and a required semicolon
// at the end:
class Cube {
  public:  // Public members:
    double getVolume();
    double getSurfaceArea();
    void setLength(double length);

  private: // Private members:
    double length_;
};

}
```
### cpp file

``` c++
#include <iostream>
#include "Cube.h"

int main() {
  Cube c;

  c.setLength(3.48);
  double volume = c.getVolume();
  std::cout << "Volume: " << volume << std::endl;

  return 0;
}
```
### Public v. private elements of a class
- within a class there is a protection level for data and functionality: private and public.
- public members can be accessed by client code (other classes and such)
- private memebers cannot be accessed by client code i.e. only used within the class itself
- private member variable should have a underscore after the name e.g. length_ (as per google's style guide data class members [https://google.github.io/styleguide/cppguide.html#Variable_Names])
### Linking to external libraries to access helper routines 
- c++ has a set of common tools and functionality
- include them with include directive, call them in code by wrting name of namespace std and double colon :: i.e. std::cout
- all functionality used from the standard library will be part of std namespace
- iostream library common functionality for inputting and outputting data, to files and the console
### Namespaces
- namespacess allow us to avoid name conflicts for commonly used names
- if a feature from a namesspace is used often is can be imported to global space with using
- minimize use of using except for common functions
- use double colon to use the namespace outside the namespace declaration, the 

```c++
#include <iostream>

using std::cout;
using std::endl;

int main() {
  cout << "Hello, world!" << endl;
  return 0;
}

```
## Week 2
### Local (stack) memory 
- in c++ we have control over memory and lifecycle of every variable
- variables live in *stack memory* by default
- every variable has 4 things: name, type, value, memory address
- the memory address can be returned by using the & operator
```c++
int num = 42;
int num_address = &num;
```
- stack memory is associated with the current function and the mem lifecycle is tied to that function, the stack memory is released with the function ends (return)
- stack memory always starts from high addresses and grows down
- 
### Pointers and dereferencing 
- Pointers are a powerful ability in c++, allows developer to save memory by pointing to stack memory and not make a bunch of copies of a variable in memory
- pointer is a variable that **stores** the memory address of the data, not actual data
- pointers are a level of indiretion from the data
- a pointer is defined by adding an * before the type of the variable
``` cpp
int * p = &num
```
- pointers can be dereferenced - indirection can be removed to see actual value of the variable this is done by putting * before variable
- don't need to know content of the pointer (mem location) but actually the value
``` cpp
int num = 7;
int * p = &num;
int value_in_num = *p;
*p = 42;
```


### Allocated (heap) memory
- we can use memory that is independant of a lifecycle of a function, i.e. it lasts longer than the lifecycle of a function - this is heap memory
- the only way to create heap memory in c++ is with the **new** operator
- the **new** operator reeturns a ponter to the memory storing the data - not an insatnce of the data itself
    1. allocate memory ofnt he heap for the data structure
    2. initialize the data structure
    3. return a pointer to the start of the data structure
- the heap memory is only ever reclaimed by the system by using the **delete** operator
- heap memory starts low and goes up - this is in contrast to stack memory which starts high and goes lower
- we also need to deallocate the stack memory by using **nullptr** which refers to the 0x0 stack memory location. 
    - Represents a pointer to nowhere
    - address 0x0 is reserved by the system and never used 
    - calls to delete 0x0 are ignored
- Arrow operator **->** allow access the contents of a class when object is stored via a pointer