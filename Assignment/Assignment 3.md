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
## **Problem 1 :** 
Overload the >> and << shift operator relative to the coord class so that the following types of operations are allowed: 
```cpp
ob << integer
ob >> integer
```
Make sure your operations shift the x and y values by the amount specified.

### **Code  :**
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
<img width="472" height="120" alt="Screenshot 2024-10-15 at 10 05 05 PM" src="https://github.com/user-attachments/assets/8748737e-e132-40a6-8218-3c0b17bd2776">
</p>

## **Problem 2 :** 
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

### **Code  :**
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
<img width="472" height="120" alt="Screenshot 2024-10-15 at 10 09 25 PM" src="https://github.com/user-attachments/assets/d9f78bec-1d00-4307-b816-247c163f5a0a">
</p> 

## **Problem 3 :** 
Rewrite your answer to Question 2 so that it uses reference parameters instead of value parameters to the operator functions. (Hint: You will need to use friend functions for the increment and decrement operators.)

### **Code  :**
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
<img width="472" height="120" alt="Screenshot 2024-10-15 at 10 09 25 PM" src="https://github.com/user-attachments/assets/02c094c2-a101-487c-bac5-4d8b3cc2c37e">
</p> 

## **Problem 4 :** 
How do friend operator functions differ from member operator functions?

### **Answer  :**
<div align="justify">
Member operator functions implicitly use the calling object as the left-hand operand, requiring only one argument for binary operators (none for unary). This allows intuitive chaining like obj1 + obj2 + obj3. In contrast, friend operator functions need two arguments for binary operators since neither operand is implied, and one for unary operators. This design provides flexibility to handle various operand types, such as allowing an integer to be added to an object (int + obj), which member functions cannot directly accommodate. Ultimately, the choice between the two depends on the desired operator behavior and the types of operands involved.
</div>

## **Problem 5 :** 
Explain why you might need to overload the assignment operator.

### **Answer  :**
<div align="justify">
Overloading the assignment operator is important for better memory management. The default assignment operator makes a simple copy of the object, which can cause issues if both objects try to access the same resource. By overloading the operator, I can ensure that each object has its own copy of the resource. This way, I can avoid problems like memory leaks and ensure that the program runs smoothly without unexpected behavior.
</div>

## **Problem 6 :** 
Can operator=() be a friend function?

### **Answer  :**
<div align="justify">
The assignment operator operator=() cannot be a friend function; it must be a member function because it directly modifies the left-hand object calling it. This ensures proper access to the object's state and allows for appropriate resource management. Implementing operator=() as a friend function would not be appropriate, as it wouldn't operate on the object being assigned to.
</div>


