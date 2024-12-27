# 1. Hierarchical Inheritance for Employee Management System

## Objective
Create a C++ program to simulate an employee management system using hierarchical inheritance. Design a base class `Employee` that stores basic details (name, ID, and salary). Create two derived classes:
- **Manager**: Add and calculate bonuses based on performance ratings.
- **Developer**: Add and calculate overtime compensation based on extra hours worked.

The program should allow input for both types of employees and display their total earnings.

## Input Format
1. Employee Type (1 for Manager, 2 for Developer).
2. Name (string), ID (integer), and salary (integer).
3. For Manager: Performance Rating (1–5).
4. For Developer: Extra hours worked (integer).

## Constraints
- Employee type: 1 ≤ type ≤ 2.
- Salary: 10,000 ≤ salary ≤ 1,000,000.
- Rating: 1 ≤ rating ≤ 5.
- Extra hours: 0 ≤ hours ≤ 100.
- Bonus per rating point: 10% of salary.
- Overtime rate: $500 per hour.

## Test Cases:

### Example 1: Manager with Rating Bonus

**Input:**
Employee Type: 1 Name: Alice ID: 101 Salary: 50000 Rating: 4  

**Output:**
Employee: Alice (ID: 101) Role: Manager Base Salary: 50000 Bonus: 20000 Total Earnings: 70000  

### Example 2: Developer with Overtime

**Input:**
Employee Type: 2 Name: Bob ID: 102 Salary: 40000 Extra Hours: 10  

**Output:**
Employee: Bob (ID: 102) Role: Developer Base Salary: 40000 Overtime Compensation: 5000 Total Earnings: 45000  

### Example 3: Invalid Employee Type

**Input:**
Employee Type: 3  

**Output:**
Invalid employee type.

## Solution
```cpp
#include <iostream>
#include <string>

using namespace std;

class Employee {
protected:
    string name;
    int id;
    int salary;

public:
    Employee(string n, int i, int s) : name(n), id(i), salary(s) {}

    virtual void calculateEarnings() = 0;

    void displayDetails() {
        cout << "Employee: " << name << " (ID: " << id << ")" << endl;
    }
};

class Manager : public Employee {
private:
    int rating;

public:
    Manager(string n, int i, int s, int r) : Employee(n, i, s), rating(r) {}

    void calculateEarnings() override {
        if (rating < 1 || rating > 5) {
            cout << "Invalid rating." << endl;
            return;
        }
        double bonus = salary * (rating * 0.10);
        double totalEarnings = salary + bonus;

        displayDetails();
        cout << "Role: Manager" << endl;
        cout << "Base Salary: " << salary << endl;
        cout << "Bonus: " << bonus << endl;
        cout << "Total Earnings: " << totalEarnings << endl;
    }
};

class Developer : public Employee {
private:
    int extraHours;

public:
    Developer(string n, int i, int s, int e) : Employee(n, i, s), extraHours(e) {}

    void calculateEarnings() override {
        if (extraHours < 0 || extraHours > 100) {
            cout << "Invalid extra hours." << endl;
            return;
        }
        int overtimeCompensation = extraHours * 500;
        int totalEarnings = salary + overtimeCompensation;

        displayDetails();
        cout << "Role: Developer" << endl;
        cout << "Base Salary: " << salary << endl;
        cout << "Overtime Compensation: " << overtimeCompensation << endl;
        cout << "Total Earnings: " << totalEarnings << endl;
    }
};

int main() {
    int employeeType;
    string name;
    int id, salary, rating, extraHours;

    cout << "Enter Employee Type (1 for Manager, 2 for Developer): ";
    cin >> employeeType;

    if (employeeType < 1 || employeeType > 2) {
        cout << "Invalid employee type." << endl;
        return 0;
    }

    cout << "Enter Name: ";
    cin >> name;
    cout << "Enter ID: ";
    cin >> id;
    cout << "Enter Salary: ";
    cin >> salary;

    if (salary < 10000 || salary > 1000000) {
        cout << "Invalid salary." << endl;
        return 0;
    }

    if (employeeType == 1) {
        cout << "Enter Performance Rating (1-5): ";
        cin >> rating;
        if (rating < 1 || rating > 5) {
            cout << "Invalid rating." << endl;
            return 0;
        }
        Manager manager(name, id, salary, rating);
        manager.calculateEarnings();
    } else if (employeeType == 2) {
        cout << "Enter Extra Hours Worked: ";
        cin >> extraHours;
        if (extraHours < 0 || extraHours > 100) {
            cout << "Invalid extra hours." << endl;
            return 0;
        }
        Developer developer(name, id, salary, extraHours);
        developer.calculateEarnings();
    }

    return 0;
}
```


# 2. Multi-Level Inheritance for Vehicle Simulation

## Objective
Create a C++ program to simulate a vehicle hierarchy using multi-level inheritance. Design a base class `Vehicle` that stores basic details (brand, model, and mileage). Extend it into the `Car` class to add attributes like fuel efficiency and speed. Further extend it into `ElectricCar` to include battery capacity and charging time. Implement methods to calculate:
- **Fuel Efficiency**: Miles per gallon (for Car).
- **Range**: Total distance the electric car can travel with a full charge.

## Input Format
1. Vehicle Type (1 for Car, 2 for Electric Car).
2. Brand (string), Model (string), and Mileage (double).
3. For Car: Fuel (gallons) and Distance Covered (miles).
4. For Electric Car: Battery Capacity (kWh), Efficiency (miles per kWh).

## Constraints
- Vehicle type: 1 ≤ type ≤ 2.
- Mileage: 0 ≤ mileage ≤ 500,000.
- Fuel: 1 ≤ fuel ≤ 100.
- Distance: 1 ≤ distance ≤ 1,000.
- Battery Capacity: 10 ≤ capacity ≤ 150.
- Efficiency: 1 ≤ efficiency ≤ 10.

## Test Cases:

### Example 1: Fuel Efficiency for Car

**Input:**
Vehicle Type: 1 Brand: Toyota Model: Corolla Mileage: 30000 Fuel: 15Distance: 300  

**Output:**
Vehicle: Toyota Corolla Mileage: 30000 Fuel Efficiency: 20 miles/gallon

### Example 2: Range of Electric Car

**Input:**
Vehicle Type: 2 Brand: Tesla Model: Model S Mileage: 5000 Battery Capacity: 100 Efficiency: 4  

**Output:**
Vehicle: Tesla Model S Mileage: 5000 Range: 400 miles

### Example 3: Invalid Vehicle Type

**Input:**
Vehicle Type: 3  

**Output:**
Invalid vehicle type.

## Solution
```cpp
#include <iostream>
#include <string>

using namespace std;

class Vehicle {
protected:
    string brand;
    string model;
    double mileage;

public:
    Vehicle(string b, string m, double mi) : brand(b), model(m), mileage(mi) {}

    virtual void displayDetails() {
        cout << "Vehicle: " << brand << " " << model << endl;
        cout << "Mileage: " << mileage << endl;
    }

    virtual void calculate() = 0; // Pure virtual function for calculating specifics
};

class Car : public Vehicle {
protected:
    double fuel;
    double distance;

public:
    Car(string b, string m, double mi, double f, double d) : Vehicle(b, m, mi), fuel(f), distance(d) {}

    void displayDetails() override {
        Vehicle::displayDetails();
    }

    void calculate() override {
        if (fuel <= 0) {
            cout << "Invalid fuel amount." << endl;
            return;
        }
        double fuelEfficiency = distance / fuel;
        cout << "Fuel Efficiency: " << fuelEfficiency << " miles/gallon" << endl;
    }
};

class ElectricCar : public Car {
private:
    double batteryCapacity;
    double efficiency;

public:
    ElectricCar(string b, string m, double mi, double bc, double eff) : Car(b, m, mi, 0, 0), batteryCapacity(bc), efficiency(eff) {}

    void displayDetails() override {
        Vehicle::displayDetails();
    }

    void calculate() override {
        if (batteryCapacity <= 0 || efficiency <= 0) {
            cout << "Invalid battery capacity or efficiency." << endl;
            return;
        }
        double range = batteryCapacity * efficiency;
        cout << "Range: " << range << " miles" << endl;
    }
};

int main() {
    int vehicleType;
    string brand, model;
    double mileage, fuel, distance, batteryCapacity, efficiency;

    cout << "Enter Vehicle Type (1 for Car, 2 for Electric Car): ";
    cin >> vehicleType;

    if (vehicleType < 1 || vehicleType > 2) {
        cout << "Invalid vehicle type." << endl;
        return 0;
    }

    cout << "Enter Brand: ";
    cin >> brand;
    cout << "Enter Model: ";
    cin >> model;
    cout << "Enter Mileage: ";
    cin >> mileage;

    if (vehicleType == 1) {  // Car
        cout << "Enter Fuel (gallons): ";
        cin >> fuel;
        cout << "Enter Distance Covered (miles): ";
        cin >> distance;
        Car car(brand, model, mileage, fuel, distance);
        car.displayDetails();
        car.calculate();
    } else if (vehicleType == 2) {  // Electric Car
        cout << "Enter Battery Capacity (kWh): ";
        cin >> batteryCapacity;
        cout << "Enter Efficiency (miles per kWh): ";
        cin >> efficiency;
        ElectricCar electricCar(brand, model, mileage, batteryCapacity, efficiency);
        electricCar.displayDetails();
        electricCar.calculate();
    }

    return 0;
}

```


# 3. Function Overloading for Complex Number Operations

## Objective
Design a C++ program using function overloading to perform arithmetic operations on complex numbers. Define a `Complex` class with real and imaginary parts. Overload functions to handle the following operations:
- **Addition**: Sum of two complex numbers.
- **Multiplication**: Product of two complex numbers.
- **Magnitude**: Calculate the magnitude of a single complex number.

The program should allow the user to select an operation, input complex numbers, and display results in the format a + bi or a - bi (where b is the imaginary part).

## Input Format
1. Operation Type (1 for Addition, 2 for Multiplication, 3 for Magnitude).
2. For Addition and Multiplication: Two complex numbers (real1, imaginary1, real2, imaginary2).
3. For Magnitude: One complex number (real, imaginary).

## Constraints
- Operation Type: 1 ≤ type ≤ 3.
- Real and Imaginary parts: -1000 ≤ real, imaginary ≤ 1000.

## Test Cases:

### Example 1: Addition of Complex Numbers

**Input:**
Operation Type: 1 Complex Number 1: 3 2 Complex Number 2: 1 -4  

**Output:**
Result: 4 - 2i

### Example 2: Multiplication of Complex Numbers

**Input:**
Operation Type: 2 Complex Number 1: 2 3 Complex Number 2: 1 -1  

**Output:**
Result: 5 + 1i

### Example 3: Magnitude of a Complex Number

**Input:**
Operation Type: 3 Complex Number: 3 4  

**Output:**
Result: Magnitude = 5

### Example 4: Invalid Operation

**Input:**
Operation Type: 4  

**Output:**
Invalid operation type.

## Solution
```cpp
#include <iostream>
#include <cmath>
#include <string>

using namespace std;

class Complex {
private:
    int real;
    int imaginary;

public:
    Complex(int r = 0, int i = 0) : real(r), imaginary(i) {}

    // Overload + operator for addition of complex numbers
    Complex operator+(const Complex& other) {
        return Complex(real + other.real, imaginary + other.imaginary);
    }

    // Overload * operator for multiplication of complex numbers
    Complex operator*(const Complex& other) {
        int r = real * other.real - imaginary * other.imaginary;
        int i = real * other.imaginary + imaginary * other.real;
        return Complex(r, i);
    }

    // Function to calculate the magnitude of the complex number
    double magnitude() {
        return sqrt(real * real + imaginary * imaginary);
    }

    // Function to display the complex number in the format a + bi or a - bi
    void display() {
        if (imaginary >= 0) {
            cout << real << " + " << imaginary << "i" << endl;
        } else {
            cout << real << " - " << -imaginary << "i" << endl;
        }
    }

    // Getter methods for real and imaginary parts
    int getReal() { return real; }
    int getImaginary() { return imaginary; }
};

int main() {
    int operation;
    cout << "Enter Operation Type (1 for Addition, 2 for Multiplication, 3 for Magnitude): ";
    cin >> operation;

    if (operation < 1 || operation > 3) {
        cout << "Invalid operation type." << endl;
        return 0;
    }

    if (operation == 1 || operation == 2) {
        int real1, imaginary1, real2, imaginary2;
        cout << "Enter Complex Number 1 (real imaginary): ";
        cin >> real1 >> imaginary1;
        cout << "Enter Complex Number 2 (real imaginary): ";
        cin >> real2 >> imaginary2;

        Complex c1(real1, imaginary1), c2(real2, imaginary2);

        if (operation == 1) {
            Complex result = c1 + c2;
            cout << "Result: ";
            result.display();
        } else if (operation == 2) {
            Complex result = c1 * c2;
            cout << "Result: ";
            result.display();
        }
    } else if (operation == 3) {
        int real, imaginary;
        cout << "Enter Complex Number (real imaginary): ";
        cin >> real >> imaginary;

        Complex c(real, imaginary);
        cout << "Result: Magnitude = " << c.magnitude() << endl;
    }

    return 0;
}

```

# 4. Polymorphism for Shape Area Calculations

## Objective
Create a C++ program that uses polymorphism to calculate the area of various shapes. Define a base class `Shape` with a virtual method `calculateArea()`. Extend this base class into the following derived classes:
- **Rectangle**: Calculates the area based on length and width.
- **Circle**: Calculates the area based on the radius.
- **Triangle**: Calculates the area using base and height.

The program should use dynamic polymorphism to handle these shapes and display the area of each.

## Input Format
1. Shape Type (1 for Rectangle, 2 for Circle, 3 for Triangle).
2. For Rectangle: Length and Width (float).
3. For Circle: Radius (float).
4. For Triangle: Base and Height (float).

## Constraints
- Shape Type: 1 ≤ type ≤ 3.
- Length, Width, Radius, Base, and Height: 1.0 ≤ value ≤ 10^4.
- Use π = 3.14159 for calculations.

## Test Cases:

### Example 1: Rectangle Area

**Input:**
Shape Type: 1 Length: 5 Width: 10  

**Output:**
Shape: Rectangle Area: 50.00

### Example 2: Circle Area

**Input:**
Shape Type: 2 Radius: 7  

**Output:**
Shape: Circle Area: 153.94

### Example 3: Triangle Area

**Input:**
Shape Type: 3 Base: 8 Height: 6  

**Output:**
Shape: Triangle Area: 24.00

### Example 4: Invalid Shape Type

**Input:**
Shape Type: 4  

**Output:**
Invalid shape type.

## Solution
```cpp
#include <iostream>
#include <cmath>
#include <iomanip>

using namespace std;

#define PI 3.14159

class Shape {
public:
    virtual void calculateArea() = 0;
    virtual ~Shape() {}
};

class Rectangle : public Shape {
private:
    float length;
    float width;
public:
    Rectangle(float l, float w) : length(l), width(w) {}

    void calculateArea() override {
        if (length >= 1.0 && length <= 10000.0 && width >= 1.0 && width <= 10000.0) {
            float area = length * width;
            cout << "Shape: Rectangle" << endl;
            cout << "Area: " << fixed << setprecision(2) << area << endl;
        } else {
            cout << "Invalid dimensions." << endl;
        }
    }
};

class Circle : public Shape {
private:
    float radius;
public:
    Circle(float r) : radius(r) {}

    void calculateArea() override {
        if (radius >= 1.0 && radius <= 10000.0) {
            float area = PI * radius * radius;
            cout << "Shape: Circle" << endl;
            cout << "Area: " << fixed << setprecision(2) << area << endl;
        } else {
            cout << "Invalid radius." << endl;
        }
    }
};

class Triangle : public Shape {
private:
    float base;
    float height;
public:
    Triangle(float b, float h) : base(b), height(h) {}

    void calculateArea() override {
        if (base >= 1.0 && base <= 10000.0 && height >= 1.0 && height <= 10000.0) {
            float area = 0.5 * base * height;
            cout << "Shape: Triangle" << endl;
            cout << "Area: " << fixed << setprecision(2) << area << endl;
        } else {
            cout << "Invalid dimensions." << endl;
        }
    }
};

int main() {
    int shapeType;
    cout << "Enter Shape Type (1 for Rectangle, 2 for Circle, 3 for Triangle): ";
    cin >> shapeType;

    Shape* shape = nullptr;

    if (shapeType == 1) {
        float length, width;
        cout << "Enter Length: ";
        cin >> length;
        cout << "Enter Width: ";
        cin >> width;
        if (length >= 1.0 && length <= 10000.0 && width >= 1.0 && width <= 10000.0) {
            shape = new Rectangle(length, width);
        } else {
            cout << "Invalid dimensions." << endl;
            return 0;
        }
    } else if (shapeType == 2) {
        float radius;
        cout << "Enter Radius: ";
        cin >> radius;
        if (radius >= 1.0 && radius <= 10000.0) {
            shape = new Circle(radius);
        } else {
            cout << "Invalid radius." << endl;
            return 0;
        }
    } else if (shapeType == 3) {
        float base, height;
        cout << "Enter Base: ";
        cin >> base;
        cout << "Enter Height: ";
        cin >> height;
        if (base >= 1.0 && base <= 10000.0 && height >= 1.0 && height <= 10000.0) {
            shape = new Triangle(base, height);
        } else {
            cout << "Invalid dimensions." << endl;
            return 0;
        }
    } else {
        cout << "Invalid shape type." << endl;
        return 0;
    }

    shape->calculateArea();
    delete shape;
    return 0;
}

```

# 5. Advanced Function Overloading for Geometric Shapes

## Objective
Create a C++ program that demonstrates function overloading to calculate the area of different geometric shapes. Implement three overloaded functions named `calculateArea` that compute the area for the following shapes:
- **Circle**: Accepts the radius.
- **Rectangle**: Accepts the length and breadth.
- **Triangle**: Accepts the base and height.

Additionally, use a menu-driven program to let the user choose the type of shape and input the respective parameters. Perform necessary validations on the input values.

## Input Format
- An integer `1 ≤ choice ≤ 3` representing the shape type:
  1. Circle
  2. Rectangle
  3. Triangle
- For each shape:
  - Circle: A positive floating-point number for the radius.
  - Rectangle: Two positive floating-point numbers for length and breadth.
  - Triangle: Two positive floating-point numbers for base and height.

## Constraints
- 1 ≤ choice ≤ 3.
- 0.0 < parameters ≤ 10^6.

## Test Cases:

### Example 1: Circle

**Input:**
Choice: 1 Radius: 7.5  

**Output:**
Shape: Circle Radius: 7.5Area: 176.714  

### Example 2: Rectangle

**Input:**
Choice: 2 Length: 8.0 Breadth: 4.5  

**Output:**
Shape: Rectangle Length: 8.0 Breadth: 4.5 Area: 36.000  

### Example 3: Triangle

**Input:**
Choice: 3 Base: 6.0 Height: 9.0  

**Output:**
Shape: Triangle Base: 6.0 Height: 9.0 Area: 27.000  

### Example 4: Invalid Choice

**Input:**
Choice: 4  

**Output:**
Invalid choice. Please select a valid shape type.

## Solution
```cpp
#include <iostream>
#include <iomanip>
#include <cmath>

using namespace std;

#define PI 3.14159

// Function to calculate area of a Circle
double calculateArea(double radius) {
    return PI * radius * radius;
}

// Function to calculate area of a Rectangle
double calculateArea(double length, double breadth) {
    return length * breadth;
}

// Function to calculate area of a Triangle
double calculateArea(double base, double height) {
    return 0.5 * base * height;
}

int main() {
    int choice;
    cout << "Enter choice (1 for Circle, 2 for Rectangle, 3 for Triangle): ";
    cin >> choice;

    if (choice == 1) {
        double radius;
        cout << "Enter radius: ";
        cin >> radius;
        if (radius > 0.0 && radius <= 1000000.0) {
            double area = calculateArea(radius);
            cout << "Shape: Circle" << endl;
            cout << "Radius: " << fixed << setprecision(1) << radius << endl;
            cout << "Area: " << fixed << setprecision(3) << area << endl;
        } else {
            cout << "Invalid input. Radius should be greater than 0 and less than or equal to 10^6." << endl;
        }
    } else if (choice == 2) {
        double length, breadth;
        cout << "Enter length: ";
        cin >> length;
        cout << "Enter breadth: ";
        cin >> breadth;
        if (length > 0.0 && breadth > 0.0 && length <= 1000000.0 && breadth <= 1000000.0) {
            double area = calculateArea(length, breadth);
            cout << "Shape: Rectangle" << endl;
            cout << "Length: " << fixed << setprecision(1) << length << endl;
            cout << "Breadth: " << fixed << setprecision(1) << breadth << endl;
            cout << "Area: " << fixed << setprecision(3) << area << endl;
        } else {
            cout << "Invalid input. Length and Breadth should be greater than 0 and less than or equal to 10^6." << endl;
        }
    } else if (choice == 3) {
        double base, height;
        cout << "Enter base: ";
        cin >> base;
        cout << "Enter height: ";
        cin >> height;
        if (base > 0.0 && height > 0.0 && base <= 1000000.0 && height <= 1000000.0) {
            double area = calculateArea(base, height);
            cout << "Shape: Triangle" << endl;
            cout << "Base: " << fixed << setprecision(1) << base << endl;
            cout << "Height: " << fixed << setprecision(1) << height << endl;
            cout << "Area: " << fixed << setprecision(3) << area << endl;
        } else {
            cout << "Invalid input. Base and Height should be greater than 0 and less than or equal to 10^6." << endl;
        }
    } else {
        cout << "Invalid choice. Please select a valid shape type." << endl;
    }

    return 0;
}

```
