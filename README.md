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
    - encapsulation ecloses data and functionality (knows and does)
    - private member variable should have a underscore after the name e.g. length_
    - within a class there is a protection level for data and functionality: private and public.
        - public members can be accessed by client code (other classes and such)
        - private memebers cannot be accessed by client code i.e. only used within the class itself
    - with c++ the header file (.h) is the interface and is defined seperately from the implementation (.cpp file)
    - c++ header file - declares all member variables, declares all member functions
- Implementation v. header files 
- Public v. private elements of a class 
- Linking to external libraries to access helper routines 
- Namespaces