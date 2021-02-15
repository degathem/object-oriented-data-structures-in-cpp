# object_oriented_data_structures_in_cpp
### Notes and code for Coursera course [https://www.coursera.org/learn/cs-fundamentals-1]
- C++ language syntax 
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
- Writing, compiling and debugging code 
- Interactive development environment (IDE)
    - I am choosing to use vs code on Ubuntu Linux
- C++ classes 
    - C++ Classes ecapsulate data and associated functionality (properties and methods) into an object
    - encapsulation encloses data and functionality (knows and does)
    
    -
    


- Implementation v. header files 
    - with c++ the header file (.h) is the interface and is defined seperately from the implementation (.cpp file)
    - c++ header file - declares all member variables, declares all member functions. The names of what our class knows and does, but not how it does them
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
- Public v. private elements of a class
    - within a class there is a protection level for data and functionality: private and public.
        - public members can be accessed by client code (other classes and such)
        - private memebers cannot be accessed by client code i.e. only used within the class itself
    - private member variable should have a underscore after the name e.g. length_ (as per google's style guide data class members [https://google.github.io/styleguide/cppguide.html#Variable_Names])
- Linking to external libraries to access helper routines 
    - c++ has a set of common tools and functionality
    - include them with include directive, call them in code by wrting name of namespace std and double colon :: i.e. std::cout
    - all functionality used from the standard library will be part of std namespace
    - iostream library common functionality for inputting and outputting data, to files and the console
- Namespaces
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