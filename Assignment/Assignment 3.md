## **Assignment No : 03**

## **Assignment Name : Study and Implementation of Operator Overloading, Inheritance, and Virtual Functions in C++**

## **Submission Date : October 15, 2024**

---

## **Theory :**
<div align="justify">
In object-oriented programming (OOP), concepts like operator overloading, inheritance, and virtual functions are essential for creating flexible, reusable, and efficient code. Operator overloading allows user-defined types to use standard operators intuitively. Inheritance promotes code reuse by enabling derived classes to extend base class functionality. Virtual functions enable run-time polymorphism, allowing programs to select the appropriate function implementation dynamically.

* **Operator Overloading:** Operator overloading is a feature in C++ that allows existing operators to be redefined and used with user-defined data types. This enables the operators to work in a more intuitive way, similar to how they work with built-in types. For example, the + operator can be overloaded to add two objects of a custom class. By overloading operators, developers can write cleaner and more readable code, making complex operations look simpler. However, it is important to use operator overloading carefully to ensure that the overloaded operators behave in a consistent and predictable manner.

* **Inheritance:** Inheritance is a fundamental concept in object-oriented programming that allows a class (known as a derived class) to acquire the properties and behaviors of another class (called a base class). It promotes code reusability by enabling derived classes to use, extend, or modify functionalities defined in the base class. Inheritance supports the hierarchical classification of classes and facilitates the implementation of polymorphic behavior. There are different types of inheritance, including single, multiple, and multilevel inheritance, each serving various design purposes.

* **Virtual Functions:** Virtual functions are member functions in a base class that can be overridden in derived classes. By declaring a function as virtual, C++ allows the function to exhibit polymorphic behavior, enabling run-time polymorphism. When a base class reference or object points to a derived class object, the specific implementation of the virtual function in the derived class is executed. This feature is critical for designing flexible and extensible systems, as it allows different classes to provide their own versions of the same function, ensuring that the correct function is called at runtime based on the actual type of the object.
</div>

## **Operator Overloading**
## **Question 1 :** 
Overload the >> and << shift operator relative to the coord class so that the following types of operations are allowed: 
```cpp
ob << integer
ob >> integer
```
Make sure your operations shift the x and y values by the amount specified.

### **Answer  :**
```cpp
#include <iostream>
using namespace std;

class coord {
private:
    int x; 
    int y; 

public:
    coord(int value1, int value2) {
        x = value1;
        y = value2;
    }

    coord operator<<(int shift) {
        coord result(x - shift, y - shift); 
        return result;
    }

    coord operator>>(int shift) {
        coord result(x + shift, y + shift);
        return result;
    }

    void display() {
        cout << "X : " << x << ", Y : " << y << endl;
    }
};

int main() {
    coord ob(10, 15); 
    ob = ob << 2; 
    ob.display();

    ob = ob >> 3; 
    ob.display(); 

    return 0;
}
```

## **Output :**
<p align="center">
<img width="472" height="170" alt="Screenshot 2024-10-15 at 10 05 05 PM" src="https://github.com/user-attachments/assets/8748737e-e132-40a6-8218-3c0b17bd2776">
</p>

### **Discussion :**
<div align="justify">
In this program, the << and >> operators are overloaded to shift the x and y values of the coord object by a specified integer. The << operator decreases both values, while the >> operator increases them. This makes it easy to adjust the coordinates using simple shift operations.
</div>


## **Question 2 :** 
Given the class 
```cpp
class three_d
{
  int x, y, z;
public :
three_d (int i, int j, int k) {
       x = i; y = j; z = k;
       }
three_d () {
       x=0; y=0; z=0;
       }
void get (int &i, int &j, int &k) {
       i = x; j = y; k = z;
       }
};
```
overload the +, -, ++, and – operators for this class. (For the increment and decrement operators, overload only the prefix form.)

### **Answer  :**
```cpp
#include <iostream>
using namespace std;

class three_d {
private:
    int x, y, z; 

public:
    three_d(int i, int j, int k) {
        x = i;
        y = j;
        z = k;
    }

    three_d() {
        x = 0;
        y = 0;
        z = 0;
    }

    void get(int &i, int &j, int &k) {
        i = x;
        j = y;
        k = z;
    }

    three_d operator+(three_d obj) {
        three_d result(x + obj.x, y + obj.y, z + obj.z);
        return result;
    }

    three_d operator-(three_d obj) {
        three_d result(x - obj.x, y - obj.y, z - obj.z);
        return result;
    }

    three_d operator++() {
        ++x;
        ++y;
        ++z;
        return *this;
    }

    three_d operator--() {
        --x;
        --y;
        --z;
        return *this;
    }

    void display() {
        cout << "X: " << x << ", Y: " << y << ", Z: " << z << endl;
    }
};

int main() {
    three_d obj1(3, 4, 5);
    three_d obj2(1, 2, 3);

    three_d obj3 = obj1 + obj2; 
    cout << "After Addition: ";
    obj3.display();

    three_d obj4 = obj1 - obj2; 
    cout << "After Subtraction: ";
    obj4.display();

    ++obj1;
    cout << "After Increment: ";
    obj1.display();

    --obj2; 
    cout << "After Decrement: ";
    obj2.display();

    return 0;
}
```

## **Output :**
<p align="center">
<img width="472" height="200" alt="Screenshot 2024-10-15 at 10 09 25 PM" src="https://github.com/user-attachments/assets/d9f78bec-1d00-4307-b816-247c163f5a0a">
</p> 

### **Discussion :**
<div align="justify">
In this program, the + and - operators are overloaded to allow adding and subtracting three_d objects, which adjusts the x, y, and z values accordingly. The prefix ++ and -- operators are also overloaded to increment or decrement each coordinate value by 1. This makes it easier to perform arithmetic and adjustment operations directly on three_d objects.
</div>


## **Question 3 :** 
Rewrite your answer to Question 2 so that it uses reference parameters instead of value parameters to the operator functions. (Hint: You will need to use friend functions for the increment and decrement operators.)

### **Answer  :**
```cpp
#include <iostream>
using namespace std;

class three_d {
private:
    int x, y, z; 

public:
    three_d(int i, int j, int k) {
        x = i;
        y = j;
        z = k;
    }

    three_d() {
        x = 0;
        y = 0;
        z = 0;
    }

    void get(int &i, int &j, int &k) {
        i = x;
        j = y;
        k = z;
    }

    three_d operator+(three_d &obj) {
        three_d result(x + obj.x, y + obj.y, z + obj.z);
        return result;
    }

    three_d operator-(three_d &obj) {
        three_d result(x - obj.x, y - obj.y, z - obj.z);
        return result;
    }

    friend three_d operator++(three_d &obj) {
        obj.x++;
        obj.y++;
        obj.z++;
        return obj;
    }

    friend three_d operator--(three_d &obj) {
        obj.x--;
        obj.y--;
        obj.z--;
        return obj;
    }

    void display() {
        cout << "X: " << x << ", Y: " << y << ", Z: " << z << endl;
    }
};

int main() {
    three_d obj1(3, 4, 5);
    three_d obj2(1, 2, 3);

    three_d obj3 = obj1 + obj2; 
    cout << "After Addition: ";
    obj3.display();

    three_d obj4 = obj1 - obj2; 
    cout << "After Subtraction: ";
    obj4.display();

    ++obj1;
    cout << "After Increment: ";
    obj1.display();

    --obj2; 
    cout << "After Decrement: ";
    obj2.display();

    return 0;
}
```

## **Output :**
<p align="center">
<img width="472" height="200" alt="Screenshot 2024-10-15 at 10 09 25 PM" src="https://github.com/user-attachments/assets/02c094c2-a101-487c-bac5-4d8b3cc2c37e">
</p> 

### **Discussion :**
<div align="justify">
In this revised program, the + and - operators are overloaded using reference parameters, allowing for more efficient access to three_d objects without making unnecessary copies. The prefix increment (++) and decrement (--) operators are implemented as friend functions, which enables direct access to the private members of the three_d class. This approach maintains the functionality while enhancing performance by avoiding the overhead of object copying during operations.
</div>


## **Question 4 :** 
How do friend operator functions differ from member operator functions?

### **Answer  :**
<div align="justify">
Member operator functions implicitly use the calling object as the left-hand operand, requiring only one argument for binary operators (none for unary). This allows intuitive chaining like obj1 + obj2 + obj3. In contrast, friend operator functions need two arguments for binary operators since neither operand is implied, and one for unary operators. This design provides flexibility to handle various operand types, such as allowing an integer to be added to an object (int + obj), which member functions cannot directly accommodate. Ultimately, the choice between the two depends on the desired operator behavior and the types of operands involved.
</div>

## **Question 5 :** 
Explain why you might need to overload the assignment operator.

### **Answer  :**
<div align="justify">
Overloading the assignment operator is important for better memory management. The default assignment operator makes a simple copy of the object, which can cause issues if both objects try to access the same resource. By overloading the operator, I can ensure that each object has its own copy of the resource. This way, I can avoid problems like memory leaks and ensure that the program runs smoothly without unexpected behavior.
</div>

## **Question 6 :** 
Can operator=() be a friend function?

### **Answer  :**
<div align="justify">
The assignment operator operator=() cannot be a friend function; it must be a member function because it directly modifies the left-hand object calling it. This ensures proper access to the object's state and allows for appropriate resource management. Implementing operator=() as a friend function would not be appropriate, as it wouldn't operate on the object being assigned to.
</div>


## **Inheritance**
## **Question 1 :** 
<div align="justify">
Create a generic base class called building that stores the number of floors a building has, the number of rooms, and its total square footage. Create derived class called house that inherits building and also stores the number of bedrooms and the number of bathrooms. Next, create a derived class called office that inherits building and also stores the number of fire extinguishers and the number of telephones. Note: Your solution may differ from the answer given in the back of this book. However, if it is functionally the same, count it as correct.
</div> 

### **Answer  :**
```cpp
#include <iostream>
using namespace std;

class Building {
private:
    int floors;           
    int rooms;            
    double squareFootage; 

public:
    Building(int f, int r, double s) { 
        floors = f;
        rooms = r;
        squareFootage = s; 
    }

    void displayBuildingInfo() {
        cout << "Building Info:" << endl;
        cout << "Floors: " << floors << endl;
        cout << "Rooms: " << rooms << endl;
        cout << "Total Square Footage: " << squareFootage << endl;
    }
};

class House : public Building {
private:
    int bedrooms;    
    int bathrooms;  

public:
    House(int f, int r, double s, int bdr, int bth): Building(f, r, s){
        bedrooms = bdr;
        bathrooms = bth;   
    }

    void displayHouseInfo() {
        displayBuildingInfo(); 
        cout << "House Info:" << endl;
        cout << "Bedrooms: " << bedrooms << endl;
        cout << "Bathrooms: " << bathrooms << endl;
    }
};

class Office : public Building {
private:
    int fireExtinguishers; 
    int telephones;        

public:
    Office(int f, int r, double s, int fe, int tel) : Building(f,r, s){
        fireExtinguishers = fe;
        telephones = tel; 
    }

    void displayOfficeInfo() {
        displayBuildingInfo(); 
        cout << "Office Info:" << endl;
        cout << "Fire Extinguishers: " << fireExtinguishers << endl;
        cout << "Telephones: " << telephones << endl;
    }
};

int main() {
    House myHouse(2, 5, 2000.0, 3, 2);
    cout << "House Details:" << endl;
    myHouse.displayHouseInfo();
    cout << endl;

    Office myOffice(5, 10, 5000.0, 4, 20);
    cout << "Office Details:" << endl;
    myOffice.displayOfficeInfo();

    return 0;
}
```

## **Output :**
<p align="center">
<img width="472" height="450" alt="Screenshot 2024-10-15 at 10 26 37 PM" src="https://github.com/user-attachments/assets/3a363c02-4bdb-4406-8402-af2859e66c17">
</p>

### **Discussion :**
<div align="justify">
This implementation defines a base class Building, which includes common attributes such as floors, rooms, and square footage. The derived classes House and Office add specific features: House tracks bedrooms and bathrooms, while Office includes fire extinguishers and telephones. This structure promotes organized code and easy extensibility, allowing for the creation of new building types by inheriting from Building. The use of constructors ensures proper initialization of all attributes, resulting in clearer and more maintainable code.
</div>


## **Question 2 :** 
When a base class is inherited as public by the derived class, what happens to its public members? What happens to its private members? If the base is inherited as private by the derived class, what happens to its public and private members?

### **Answer  :**
<div align="justify">
    
When a base class is inherited by a derived class, the accessibility of its members depends on the type of inheritance (public, protected, or private).
* **Base Class is Inherited as Public by the Derived Class**<br>
**Public Members:** The base class's public members remain public in the derived class and can be accessed by any code that has access to the derived class.<br>
**Private Members:** The base class's private members remain inaccessible in the derived class and cannot be accessed directly, as they are not visible to the derived class.
* **Base Class is Inherited as Private by the Derived Class**<br>
**Public Members:** The base class's public members become private in the derived class and can only be accessed by the derived class, not by any external code.<br>
**Private Members:** The base class's private members remain inaccessible in the derived class and cannot be accessed directly, similar to public inheritance.<br>

</div>

## **Question 3 :** 
Explain what protected means. (Be sure to explain what it means both when referring to members of a class and when it is used as an inheritance access specifier.)

### **Answer  :**
<div align="justify">

The protected keyword in C++ serves two purposes: controlling member access within a class and defining how base class members are treated during inheritance.
* **Referring to members of a class:**
When a class member is marked as protected, it can be accessed within the class itself and by any class that inherits from it. This means that protected members are not accessible from outside the class or by unrelated classes, but they are available to all derived classes, allowing them to use and modify these members.<br>
* **Using as an inheritance access specifier:**
When a derived class inherits a base class using the protected specifier, the public and protected members of the base class become protected in the derived class. This means they can be accessed within the derived class and further derived classes but are not accessible outside. The private members of the base class, however, remain completely inaccessible and cannot be used by the derived class.

</div>

## **Question 4 :** 
When one class inherits another, when are the classes’ constructors called? When are their destructors called?

### **Answer  :**
<div align="justify">

When one class inherits another, the order of constructor and destructor calls follows a specific sequence:

* **Constructors:**
When a derived class inherits one or more base classes, the constructors of the base classes are called first, in the order they are listed in the inheritance declaration. After all the base class constructors have been executed, the constructor of the derived class is called. This ensures that the base part of the object is properly initialized before the derived part. <br>
* **Destructors:**
The order is reversed for destructors. When an object is destroyed, the derived class’s destructor is called first, followed by the destructors of the base classes, in reverse order of their construction. This ensures that any resources specific to the derived class are released before those of the base class.

</div>

## **Question 5 :** 
Given this skeleton, fill in the details as indicated in the comments:

```cpp
# include <iostream >
using namespace std;

class planet {
protected :
        double distance ; // miles from the sun
        int revolve ; // in days
public :
planet ( double d, int r) {
        distance = d; revolve = r;
        }
};
class earth : public planet {
        double circumference ; // circumference of orbit
public :
/*
Create earth ( double d, int r). Have it pass the
distance and days of revolution back to planet .
Have it compute the circumference of the orbit . ( Hint : circumference = 2r *3.1416.)
*/
/*
Create a function called show () that displays the
information .
*/
};

int main () {
earth ob (93000000 , 365) ;
ob. show ();
return 0;
}
```

### **Answer  :**
```cpp
#include <iostream>
using namespace std;

class planet {
protected:
    double distance; 
    int revolve;    

public:
    planet(double d, int r) {
        distance = d;
        revolve = r;
    }
};

class earth : public planet {
private:
    double circumference; 

public:
    earth(double d, int r) : planet(d, r) {
        circumference = 2 * d * 3.1416; 
    }

    void show() {
        cout << "Distance from the Sun: " << distance << " miles" << endl;
        cout << "Days to complete one revolution: " << revolve << " days" << endl;
        cout << "Circumference of the orbit: " << circumference << " miles" << endl;
    }
};

int main() {
    earth ob(93000000, 365);
    ob.show();
    return 0;
}
```

## **Output :**
<p align="center">
<img width="472" height="200" alt="Screenshot 2024-10-15 at 10 37 50 PM" src="https://github.com/user-attachments/assets/f8b5b162-89df-4dfc-9884-9ca540ffb99c">
</p>

### **Discussion :**
<div align="justify">
This implementation defines a base class planet with protected attributes for distance from the sun and the number of days it takes to revolve. The derived class earth inherits from planet and includes an additional attribute for the circumference of the orbit. The constructor of earth initializes the base class using an initializer list and calculates the circumference using the formula, circumference = 2 × distance × 3.1416. The show function displays the planet's details, providing a clear overview of its properties. This structure allows for easy extension to other celestial bodies while maintaining encapsulation.
</div>


## **Question 6 :** 
Fix the following program:

```cpp
/*
A variation on the vehicle hierarchy . But
this program contains an error . Fix it. Hind :
try compiling it as is and observe the error
messages .
*/
# include <iostream >
using namespace std;
// A base class for various types of vehicles .
class vehicle {
        int num_wheels ;
        int range ;
public :
        vehicle (int w, int r) {
        num_wheels = w;
        range = r;
        }
void showv () {
cout << " Wheels : " << num_wheels << ’\n’;
cout << " Range : " << range << ’\n’;
    }
};
enum motor { gas , electric , diesel };
class motorized : public vehicle {
        enum motor mtr ;
public :
motorized ( enum motor m, int w, int r) : vehicle (w, r) {
        mtr = m;
        }
void showm () {
cout << " Motor : ";
    switch (mtr ) {
case gas : cout << "Gas \n";
    break ;
case electric : cout << " Electric \n";
    break ;
case diesel : cout << " Diesel \n";
    break ;
        }
    }
};
class road_use : public vehicle {
    int passengers ;
public :
    road_use (int p, int w, int r) : vehicle (w, r) {
        passengers = p; }
void showr () {
cout << " Passengers : " << passengers << ’\n’;
     }
};
enum steering { power , rack_pinion , manual };
class car : public motorized , public road_use {
    enum steering strng ;
public :
    car ( enum steering s, enum motor m, int w, int r, int p) :
    road_use (p, w, r), motorized (m, w, r), vehicle (w, r) {
        strng = s;
         }
void show () {
showv ();
showr ();
showm ();
cout << " Steering : ";
    switch ( strng ) {
case power : cout << " Power \n";
    break ;
case rack_pinion : cout << " Rack and Pinion \n";
    break ;
case manual : cout << " Manual \n";
    break ;
        }
    }
};
int main () {
car c(power , gas , 4 , 500 , 5); c. show ();
return 0;
}
```

### **Answer  :**
```cpp
#include <iostream>
using namespace std;

class vehicle {
    int num_wheels;
    int range;
public:
    vehicle(int w, int r) {
        num_wheels = w;
        range = r;
    }
    void showv() {
        cout << "Wheels: " << num_wheels << endl;
        cout << "Range: " << range << endl;
    }
};

enum motor { gas, electric, diesel };

class motorized : virtual public vehicle {
    enum motor mtr;
public:
    motorized(enum motor m, int w, int r) : vehicle(w, r) {
        mtr = m;
    }
    void showm() {
        cout << "Motor: ";
        switch (mtr) {
            case gas: 
                cout << "Gas" << endl; 
                break;
            case electric: 
                cout << "Electric" << endl; 
                break;
            case diesel: 
                cout << "Diesel" << endl; 
                break;
        }
    }
};

class road_use : virtual public vehicle {
    int passengers;
public:
    road_use(int p, int w, int r) : vehicle(w, r) {
        passengers = p;
    }
    void showr() {
        cout << "Passengers: " << passengers << endl;
    }
};

enum steering { power, rack_pinion, manual };

class car : public motorized, public road_use {
    enum steering strng;
public:
    car(enum steering s, enum motor m, int w, int r, int p) 
        : vehicle(w, r), motorized(m, w, r), road_use(p, w, r){
            strng = s;
        } 

    void show() {
        showv();
        showr();
        showm();
        cout << "Steering: ";
        switch (strng) {
            case power: 
                cout << "Power" << endl; 
                break;
            case rack_pinion: 
                cout << "Rack and Pinion" << endl; 
                break;
            case manual: 
                cout << "Manual"; 
                break;
        }
    }
};

int main() {
    car c(power, gas, 4, 500, 5);
    c.show();
    return 0;
}
```

## **Output :**
<p align="center">
<img width="472" height="230" alt="Screenshot 2024-10-15 at 10 44 27 PM" src="https://github.com/user-attachments/assets/8d08fa55-331d-4b04-be42-7a499ae90e19">
</p>

### **Discussion :**
<div align="justify">
The provided program defines a vehicle hierarchy using classes in C++. It includes a base class vehicle and derived classes like motorized and road_use. The program had errors related to the constructor calls and member functions, which were fixed by using virtual inheritance. This allows the car class to correctly inherit properties from both motorized and road_use without ambiguity. The final output displays details about the vehicle, including wheels, range, motor type, passengers, and steering type. Overall, it demonstrates how to structure related classes effectively in C++.
</div>


## **Virtual Functions**
## **Question 1 :** 
What is a virtual function?

### **Answer  :**
<div align="justify">
    
A virtual function is a member function declared within a base class that can be redefined (overridden) by a derived class. This allows for dynamic polymorphism, enabling the appropriate function to be called at runtime based on the actual object type rather than the type of the reference. By using the virtual keyword in the base class, derived classes can provide their own implementations of the function, ensuring that the correct version is executed when accessed through a base class reference.

</div>

## **Question 2 :** 
What types of functions cannot be made virtual?

### **Answer  :**
<div align="justify">
    
Non-member functions (such as friend functions) and constructor functions cannot be made virtual. Additionally, static member functions cannot be virtual because they do not operate on an instance of the class. Although private member functions can technically be declared as virtual, they are not accessible outside the class, making their virtual nature largely irrelevant. While destructors can be virtual, if a class is not intended for inheritance, its destructor should not be declared as virtual.

</div>

## **Question 3 :** 
How does a virtual function help achieve run-time polymorphism? Be specific.

### **Answer  :**
<div align="justify">
    
Virtual functions enable run-time polymorphism by allowing the program to decide which function to call based on the actual type of the object at runtime. When a base class reference or object points to a derived class object that has overridden a virtual function, the specific implementation of that function in the derived class is called. This mechanism ensures that the correct function is executed, regardless of the reference type, thus achieving dynamic behavior in the program.
```cpp
Base* b = new Derived(); // Base class pointer pointing to a derived class object
b->show();               // Calls the overridden show() in Derived class
```
In this example syntax, although b is a pointer of type Base, it points to a Derived object. When b->show() is invoked, the program determines at runtime to execute the Derived class's implementation of show.
</div>

## **Question 4 :** 
What is a pure virtual function?

### **Answer  :**
<div align="justify">
    
A pure virtual function (or abstract function) in C++ is a virtual function for which the implementation is not provided, only the declaration. A pure virtual function is declared by assigning 0 in the declaration, making the containing class an abstract class that cannot be instantiated. Derived classes must provide an implementation for the pure virtual function to be instantiated.<br>
**Syntax:**
```cpp
virtual void functionName() = 0; // Pure virtual function declaration
```
</div>

## **Question 5 :** 
What is an abstract class? What is a polymorphic class?

### **Answer  :**
<div align="justify">
    
Sometimes, the implementation of all functions cannot be provided in a base class because the implementation is not known. Such a class is called an abstract class. An abstract class typically contains at least one pure virtual function, making it impossible to instantiate directly.<br>

**Syntax for Abstract Class:**
```cpp
class AbstractClass {
public:
    virtual void pureVirtualFunction() = 0; // Pure virtual function
};
```
A polymorphic class in C++ is a class that contains at least one virtual function, allowing it to support dynamic binding and enabling run-time polymorphism. This means that the correct function implementation can be determined at runtime based on the actual object type.<br>

**Syntax for Polymorphic Class:**
```cpp
class PolymorphicClass {
public:
    virtual void display() {
        // Function implementation
    }
};
```
</div>

## **Question 6 :** 
Is the following fragment correct? If not, why not?
```cpp
class base {
public :
    virtual int (int a) = 0;
// ...
};
class derived : public base {
public :
    int f(int a, int b) { return a*b; }
// ...
}:
```

### **Answer  :**
<div align="justify">
    
No, the provided code fragment is incorrect due to several issues.<br>
Firstly, the virtual function in the base class lacks a name, which makes it invalid. A valid virtual function declaration must include a name followed by its parameters. Additionally, there is an unnecessary colon (:) at the end of the derived class declaration, which should be a semicolon (;) to properly terminate the class. <br>
Secondly, the derived class implements a function named f that takes two parameters, whereas the virtual function in the base class should match both the name and the parameter count. <br>
In essence, when overriding a virtual function, it is crucial that the derived function has the same return type, name, and parameters as the base function. The corrected version should look like this:
```cpp
class base {
public:
    virtual int f(int a) = 0; // Corrected: Added name 'f' to the virtual function
    // ...
};

class derived : public base {
public:
    int f(int a) override { return a * 2; } // Corrected: Same name and parameter count as in base class
    // ...
}; // Corrected: Replaced the colon with a semicolon
```
</div>

## **Question 7 :** 
Is the virtual quality inherited?

### **Answer  :**
<div align="justify">
    
Yes, the virtual quality is inherited in C++. When a base class declares a function as virtual, derived classes can override that function, and it retains its virtual behavior, allowing for dynamic polymorphism. This means that when a base class pointer points to a derived class object, the derived class's overridden function will be called at runtime, ensuring the correct behavior is executed based on the actual object type.

</div>


## **Conclusion :**
<div align="justify">
This lab report explored the fundamental concepts of operator overloading, inheritance, and virtual functions in C++. Each section presented multiple problems that highlighted the practical applications and importance of these features in object-oriented programming. Operator overloading demonstrated how to define custom behaviors for built-in operators, enhancing code readability and usability. Inheritance illustrated the principles of reusability and polymorphism, allowing for the creation of hierarchical relationships among classes. Finally, the section on virtual functions emphasized the significance of dynamic binding, enabling runtime polymorphism and providing flexibility in function overriding. Through these problems, we gained a deeper understanding of how these concepts contribute to the design and implementation of robust, maintainable software systems in C++.
</div>

