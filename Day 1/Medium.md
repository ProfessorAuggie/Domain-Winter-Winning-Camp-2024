# 1. Function Overloading for Calculating Area

## Objective
Write a program to calculate the area of different shapes using function overloading. Implement overloaded functions to compute the area of a circle, a rectangle, and a triangle.

## Input Format
- Radius of the circle for the first function.
- Length and breadth of the rectangle for the second function.
- Base and height of the triangle for the third function.

## Constraints
- 1 ≤ radius, length, breadth, base, height ≤ 1000
- Use 3.14159 for the value of π.

## Output Format
Print the computed area of each shape in a new line.

## Test Cases

### Example 1

**Input:**
Radius = 5
Length = 4, breadth = 6
Base = 3, height = 7

**Output:**
78.53975
24
10.5

**Explanation:**
- The area of the circle with radius 5 is 3.14159 * 5² = 78.53975.
- The area of the rectangle with length 4 and breadth 6 is 4 * 6 = 24.
- The area of the triangle with base 3 and height 7 is 0.5 * 3 * 7 = 10.5.

### Example 2

**Input:**
Radius = 10
Length = 15, breadth = 8
Base = 12, height = 9

**Output:**
314.159
120
54

**Explanation:**
- The area of the circle with radius 10 is 3.14159 * 10² = 314.159.
- The area of the rectangle with length 15 and breadth 8 is 15 * 8 = 120.
- The area of the triangle with base 12 and height 9 is 0.5 * 12 * 9 = 54.

### Example 3

**Input:**
Radius = 1
Length = 2, breadth = 3
Base = 5, height = 8

**Output:**
3.14159
6
20

**Explanation:**
- The area of the circle with radius 1 is 3.14159 * 1² = 3.14159.
- The area of the rectangle with length 2 and breadth 3 is 2 * 3 = 6.
- The area of the triangle with base 5 and height 8 is 0.5 * 5 * 8 = 20.

## Solution
```cpp
#include <iostream>
#include <cmath>
using namespace std;

const double PI = 3.14159;

double area(double radius) {
    return PI * radius * radius;
}

int area(int length, int breadth) {
    return length * breadth;
}

double area(double base, double height) {
    return 0.5 * base * height;
}

int main() {
    double radius, base, height;
    int length, breadth;

    cin >> radius;
    if (radius < 1 || radius > 1000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << area(radius) << endl;

    cin >> length >> breadth;
    if (length < 1 || length > 1000 || breadth < 1 || breadth > 1000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << area(length, breadth) << endl;

    cin >> base >> height;
    if (base < 1 || base > 1000 || height < 1 || height > 1000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << area(base, height) << endl;

    return 0;
}
```

# 2. Function Overloading with Hierarchical Structure

## Objective
Write a program that demonstrates function overloading to calculate the salary of employees at different levels in a company hierarchy. Implement overloaded functions to compute salary for:
- Intern (basic stipend).
- Regular employee (base salary + bonuses).
- Manager (base salary + bonuses + performance incentives).

## Input Format
- Intern: Basic stipend.
- Regular employee: Base salary and bonuses.
- Manager: Base salary, bonuses, and performance incentives.

## Constraints
- 1 ≤ stipend, base salary, bonuses, incentives ≤ 10^6

## Output Format
Print the calculated salary for each level of the hierarchy on a new line.

## Test Cases

### Example 1

**Input:**
Stipend = 10000
Base salary = 50000, bonuses = 20000
Base salary = 80000, bonuses = 30000, incentives = 20000

**Output:**
Intern Salary: 10000
Employee Salary: 70000
Manager Salary: 130000

**Explanation:**
- Intern receives only the stipend: 10000.
- Regular employee salary is calculated as 50000 + 20000 = 70000.
- Manager's salary includes all components: 80000 + 30000 + 20000 = 130000.

### Example 2

**Input:**
Stipend = 15000
Base salary = 60000, bonuses = 25000
Base salary = 100000, bonuses = 40000, incentives = 30000

**Output:**
Intern Salary: 15000
Employee Salary: 85000
Manager Salary: 170000

### Example 3

**Input:**
Stipend = 5000
Base salary = 45000, bonuses = 15000
Base salary = 70000, bonuses = 20000, incentives = 10000

**Output:**
Intern Salary: 5000
Employee Salary: 60000
Manager Salary: 100000

## Solution
```cpp
#include <iostream>
using namespace std;

double calculateSalary(double stipend) {
    return stipend;
}

double calculateSalary(double baseSalary, double bonuses) {
    return baseSalary + bonuses;
}

double calculateSalary(double baseSalary, double bonuses, double incentives) {
    return baseSalary + bonuses + incentives;
}

int main() {
    double stipend, baseSalary, bonuses, incentives;

    cout << "Enter Stipend: ";
    cin >> stipend;
    if (stipend < 1 || stipend > 1000000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << "Intern Salary: " << calculateSalary(stipend) << endl;

    cout << "Enter Base Salary and Bonuses: ";
    cin >> baseSalary >> bonuses;
    if (baseSalary < 1 || baseSalary > 1000000 || bonuses < 1 || bonuses > 1000000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << "Employee Salary: " << calculateSalary(baseSalary, bonuses) << endl;

    cout << "Enter Base Salary, Bonuses, and Incentives: ";
    cin >> baseSalary >> bonuses >> incentives;
    if (baseSalary < 1 || baseSalary > 1000000 || bonuses < 1 || bonuses > 1000000 || incentives < 1 || incentives > 1000000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << "Manager Salary: " << calculateSalary(baseSalary, bonuses, incentives) << endl;

    return 0;
}
```

# 3. Encapsulation with Employee Details

## Objective
Write a program that demonstrates encapsulation by creating a class `Employee`. The class should have private attributes to store:
- Employee ID
- Employee Name
- Employee Salary

Provide public methods to set and get these attributes, and a method to display all details of the employee.

## Input Format
- Employee ID as an integer.
- Employee Name as a string.
- Employee Salary as a floating-point number.

## Constraints
- 1 ≤ Employee ID ≤ 10^6
- Name can have up to 50 characters.
- 1.0 ≤ Salary ≤ 10^7

## Output Format
Print the employee details, including ID, Name, and Salary, on separate lines.

## Test Cases

### Example 1

**Input:**
ID = 101
Name = John Doe
Salary = 75000.5

**Output:**
Employee ID: 101
Employee Name: John Doe
Employee Salary: 75000.5

**Explanation:**
Encapsulation ensures that employee details are accessed and modified only through public methods.

### Example 2

**Input:**
ID = 202
Name = Jane Smith
Salary = 85000.75

**Output:**
Employee ID: 202
Employee Name: Jane Smith
Employee Salary: 85000.75

### Example 3

**Input:**
ID = 303
Name = Robert Brown
Salary = 67000.0

**Output:**
Employee ID: 303
Employee Name: Robert Brown
Employee Salary: 67000.0

## Solution
```cpp
#include <iostream>
#include <string>
using namespace std;

class Employee {
private:
    int id;
    string name;
    double salary;

public:
    void setID(int empID) {
        if (empID >= 1 && empID <= 1000000) {
            id = empID;
        } else {
            cout << "Invalid Employee ID" << endl;
        }
    }

    int getID() {
        return id;
    }

    void setName(string empName) {
        if (empName.length() <= 50) {
            name = empName;
        } else {
            cout << "Invalid Employee Name" << endl;
        }
    }

    string getName() {
        return name;
    }

    void setSalary(double empSalary) {
        if (empSalary >= 1.0 && empSalary <= 10000000) {
            salary = empSalary;
        } else {
            cout << "Invalid Employee Salary" << endl;
        }
    }

    double getSalary() {
        return salary;
    }

    void displayDetails() {
        cout << "Employee ID: " << id << endl;
        cout << "Employee Name: " << name << endl;
        cout << "Employee Salary: " << salary << endl;
    }
};

int main() {
    Employee emp;

    int id;
    string name;
    double salary;

    cout << "Enter Employee ID: ";
    cin >> id;
    emp.setID(id);

    cout << "Enter Employee Name: ";
    cin.ignore();
    getline(cin, name);
    emp.setName(name);

    cout << "Enter Employee Salary: ";
    cin >> salary;
    emp.setSalary(salary);

    cout << endl;
    emp.displayDetails();

    return 0;
}
```

# 4. Inheritance with Student and Result Classes

## Objective
Create a program that demonstrates inheritance by defining:
- A base class `Student` to store details like Roll Number and Name.
- A derived class `Result` to store marks for three subjects and calculate the total and percentage.

## Input Format
- Roll Number as an integer.
- Name as a string.
- Marks in three subjects as integers.

## Constraints
- 1 ≤ Roll Number ≤ 10^6
- Name can have up to 50 characters.
- 0 ≤ Marks in each subject ≤ 100

## Output Format
Print the student details, marks, total, and percentage.

## Test Cases

### Example 1

**Input:**
Roll Number = 101Name = Alice SmithMarks = 85, 90, 80  

**Output:**
Roll Number: 101Name: Alice SmithMarks: 85, 90, 80Total: 255Percentage: 85.0%  

**Explanation:**
The `Result` class inherits `Student` details and calculates `Total = 85 + 90 + 80` and `Percentage = (255/300) × 100`.

### Example 2

**Input:**
Roll Number = 202Name = Bob MartinMarks = 70, 75, 65  

**Output:**
Roll Number: 202Name: Bob MartinMarks: 70, 75, 65Total: 210Percentage: 70.0%  

### Example 3

**Input:**
Roll Number = 303Name = Clara BrownMarks = 95, 92, 88  

**Output:**
Roll Number: 303Name: Clara BrownMarks: 95, 92, 88Total: 275Percentage: 91.67%  

## Solution
```cpp
#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

class Student {
protected:
    int rollNumber;
    string name;

public:
    void setDetails(int roll, string studentName) {
        if (roll >= 1 && roll <= 1000000) {
            rollNumber = roll;
        } else {
            cout << "Invalid Roll Number" << endl;
            return;
        }

        if (studentName.length() <= 50) {
            name = studentName;
        } else {
            cout << "Invalid Name" << endl;
        }
    }

    void displayDetails() {
        cout << "Roll Number: " << rollNumber << endl;
        cout << "Name: " << name << endl;
    }
};

class Result : public Student {
private:
    int marks[3];
    int total;
    double percentage;

public:
    void setMarks(int m1, int m2, int m3) {
        if ((m1 >= 0 && m1 <= 100) && (m2 >= 0 && m2 <= 100) && (m3 >= 0 && m3 <= 100)) {
            marks[0] = m1;
            marks[1] = m2;
            marks[2] = m3;
        } else {
            cout << "Invalid Marks" << endl;
            return;
        }
    }

    void calculateResult() {
        total = marks[0] + marks[1] + marks[2];
        percentage = (total / 300.0) * 100.0;
    }

    void displayResult() {
        displayDetails();
        cout << "Marks: " << marks[0] << ", " << marks[1] << ", " << marks[2] << endl;
        cout << "Total: " << total << endl;
        cout << "Percentage: " << fixed << setprecision(2) << percentage << "%" << endl;
    }
};

int main() {
    Result student;

    int rollNumber, mark1, mark2, mark3;
    string studentName;

    cout << "Enter Roll Number: ";
    cin >> rollNumber;

    cout << "Enter Name: ";
    cin.ignore();
    getline(cin, studentName);

    cout << "Enter Marks (3 subjects): ";
    cin >> mark1 >> mark2 >> mark3;

    student.setDetails(rollNumber, studentName);
    student.setMarks(mark1, mark2, mark3);
    student.calculateResult();

    cout << endl;
    student.displayResult();

    return 0;
}
```

# 5. Polymorphism with Shape Area Calculation

## Objective
Create a program that demonstrates polymorphism by calculating the area of different shapes using a base class `Shape` and derived classes for `Circle`, `Rectangle`, and `Triangle`. Each derived class should override a virtual function to compute the area of the respective shape.

## Input Format
- Radius for a circle.
- Length and breadth for a rectangle.
- Base and height for a triangle.

## Constraints
- 1 ≤ Radius, Length, Breadth, Base, Height ≤ 10^4
- Use π = 3.14159 for circle area calculations.

## Output Format
Print the area of each shape on separate lines, rounded to 2 decimal places.

## Test Cases

### Example 1

**Input:**
Radius = 7Length = 10, Breadth = 5Base = 8, Height = 6  

**Output:**
Circle Area: 153.94Rectangle Area: 50.00Triangle Area: 24.00  

**Explanation:**
- Circle area is calculated as πr² = 3.14159 × 7² = 153.94.
- Rectangle area is Length × Breadth = 10 × 5 = 50.
- Triangle area is 0.5 × Base × Height = 0.5 × 8 × 6 = 24.

### Example 2

**Input:**
Radius = 5 Length = 12, Breadth = 8 Base = 15, Height = 10  

**Output:**
Circle Area: 78.54 Rectangle Area: 96.00 Triangle Area: 75.00  

### Example 3

**Input:**
Radius = 10 Length = 20, Breadth = 15 Base = 10, Height = 12  

**Output:**
Circle Area: 314.16 Rectangle Area: 300.00 Triangle Area: 60.00  

## Solution
```cpp
#include <iostream>
#include <iomanip>
#include <cmath>
using namespace std;

class Shape {
public:
    virtual double calculateArea() = 0;
    virtual ~Shape() {}
};

class Circle : public Shape {
private:
    double radius;

public:
    Circle(double r) : radius(r) {}
    double calculateArea() override {
        return 3.14159 * radius * radius;
    }
};

class Rectangle : public Shape {
private:
    double length, breadth;

public:
    Rectangle(double l, double b) : length(l), breadth(b) {}
    double calculateArea() override {
        return length * breadth;
    }
};

class Triangle : public Shape {
private:
    double base, height;

public:
    Triangle(double b, double h) : base(b), height(h) {}
    double calculateArea() override {
        return 0.5 * base * height;
    }
};

int main() {
    double radius, length, breadth, base, height;

    cin >> radius;
    if (radius < 1 || radius > 10000) {
        cout << "Invalid Radius" << endl;
        return 1;
    }

    cin >> length >> breadth;
    if (length < 1 || length > 10000 || breadth < 1 || breadth > 10000) {
        cout << "Invalid Length or Breadth" << endl;
        return 1;
    }

    cin >> base >> height;
    if (base < 1 || base > 10000 || height < 1 || height > 10000) {
        cout << "Invalid Base or Height" << endl;
        return 1;
    }

    Circle circle(radius);
    Rectangle rectangle(length, breadth);
    Triangle triangle(base, height);

    cout << fixed << setprecision(2);
    cout << "Circle Area: " << circle.calculateArea() << endl;
    cout << "Rectangle Area: " << rectangle.calculateArea() << endl;
    cout << "Triangle Area: " << triangle.calculateArea() << endl;

    return 0;
}
```
