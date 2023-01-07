### Classes and objects 
- When object is being accessed by a pointer, member functions can be accessed using the `->` (arrow) operator

```c++
c->getVolume();
(*c).getVolume(); # identical
```
### Constructors
- The term default constructor it defines a constructor that takes in no arguments. if any single custom constructor is defined, the automatic default constructor is not defined automatically
- We define a custom default constructor by creating:
    1. A member function with the same name of the class
    2. A function takes zero parameters.
    3. The function does not have a return type. (not even void)
    ```c++
    //in Cube.h header file
    namespace uiuc {
        class Cube {
            public: 
                Cube(); // Custom default constructor

                double getVolume();
                void setLength(double length);
            private:
                double length_;
        };
    }

    //in Cube.cpp define implementation
    namespace uiuc {
        Cube::Cube() {
            length_ = 1;
        }
    }
    ```
- constructor can be overladed (eg. with and without parameters) Eg. with param constructor initialization: uiuc::Cube c(2); //init cube object of length 2
- Compile time error if object initialized with a signature that doesn't match to any class constructor. E.g. if there's a one parameter constructor only and you try to initialize a class object without parameters, a compile time error will be thrown

### Copy constructor
- The function needs to be a class constructor, so it needs to follow all the rules for a class constructor, and it must have exactly one argument, and that argument must be a constant reference to the same type as the class itself.
    - i.e. argument: const Class & obj
- A copy constructor is called when an object is passed as an argument to another function (because it has to be copied into the function's stack frame)
- Also, when a function returns an object, it has to be copied back to main, so a copy constructor is invoked

### Copy assignment operator
- if objects are already created (using default constructor or otherwise), and then there's an assignment statement with these created objects, copy ctor won't be invoked (as there's no construction involved)
- A copy assignment operator defines a behavior of using the assignment operator or the equals sign in code, which is different from a copy constructor because it doesn't construct anything - just assigns a value to an existing object
- Rules
    - Public member function of the class
    - Function name operator=
    - It has to have a return value of the reference of the class type.
    - has exactly one argument - which is const reference of the class type
    ```c++
    Cube & Cube:: operator=(const Cube & obj)
    ```

### Reference variable
- a reference variable never stores any memory itself.
- 0 bytes of memory; it's an alias to memory; use &; when ref var created, it must be aliased as soon as created. if not, compiler error
- if we use & in function signature, it will create an alias and not another copy of the object in the function stack frame; 3 ways: by value, by reference, by pointer

### Destructor
- There's exactly one way to define it and the only way to define it, is the name of the class itself preceded by a tilde with absolutely no arguments.
```c++
Cube::~Cube(); //Class destructor
```

### Templates
- We initialize a vector by saying std::vector and we give it the templated type inside of these alligator braces
- ```std::vector<T> v; ```where T is the desired type of each element of the vector; thsi is a dynamically initialized vector array (of variable size) accessor is [] square brackets; push_back() for pushing to back of the array; .size() to return size of the array;
- ```template <typename T>``` comes before class or function (without semicolon); T can be used as placeholder for any type (custom or inbuilt)
```c++
template <typename T>
class List{
    //...
    private:
        T data_;
};
```
### Inheritance
- Base class constructor gets called first and then derived class initialized
- for constructor of derived class: derived classs constructor(x,y) : base class constructor (x) {//definition}; after colon part is called `initializer list`
```c++
namespace uiuc {
    Cube::Cube(double width, uiuc::HSLAPixel color) : Shape(width) {
        color_ = color;
    }
}
```
- don't have access to private members of the base class in the derived class
    - can call accessor methods: e.g. getWidth() 
- can use the `initializer list` syntax defined above for multiple things - can help clean up code
```c++
//default width 1 for the constructor - uses the 1 parameter constructor for initialization
Shape::Shape() : Shape(1) {
    //Nothing
}
// initialize private member variables using initializer list
Shape::Shape(double width) : width_(width) {
    //Nothing
}

```