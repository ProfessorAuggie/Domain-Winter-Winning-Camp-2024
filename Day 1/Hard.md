# 1. Implementing Polymorphism for Shape Hierarchies

## Objective
Write a program to demonstrate runtime polymorphism in C++ using a base class `Shape` and derived classes `Circle`, `Rectangle`, and `Triangle`. The program should use virtual functions to calculate and print the area of each shape based on user input.

## Input Format
- Radius of the circle for the first derived class.
- Length and breadth of the rectangle for the second derived class.
- Base and height of the triangle for the third derived class.

## Constraints
- 1 ≤ radius, length, breadth, base, height ≤ 10^3
- Use 3.14159 for the value of π

## Output Format
Print the computed area of each shape on a new line.

## Test Cases:

### Example 1

**Input:**
Radius = 5Length = 4, breadth = 6Base = 3, height = 7  

**Output:**
Area of Circle: 78.53975Area of Rectangle: 24Area of Triangle: 10.5  

**Explanation:**
- The area of the circle is 3.14159 × 5² = 78.53975.
- The area of the rectangle is 4 × 6 = 24.
- The area of the triangle is 0.5 × 3 × 7 = 10.5.

### Example 2

**Input:**
Radius = 10Length = 15, breadth = 8Base = 12, height = 9  

**Output:**
Area of Circle: 314.159Area of Rectangle: 120Area of Triangle: 54  

**Explanation:**
- The area of the circle is 3.14159 × 10² = 314.159.
- The area of the rectangle is 15 × 8 = 120.
- The area of the triangle is 0.5 × 12 × 9 = 54.

### Example 3

**Input:**
Radius = 1Length = 2, breadth = 3Base = 5, height = 8  

**Output:**
Area of Circle: 3.14159Area of Rectangle: 6Area of Triangle: 20  

**Explanation:**
- The area of the circle is 3.14159 × 1 = 3.14159.
- The area of the rectangle is 2 × 3 = 6.
- The area of the triangle is 0.5 × 5 × 8 = 20.

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
    if (radius < 1 || radius > 1000) {
        cout << "Invalid Radius" << endl;
        return 1;
    }

    cin >> length >> breadth;
    if (length < 1 || length > 1000 || breadth < 1 || breadth > 1000) {
        cout << "Invalid Length or Breadth" << endl;
        return 1;
    }

    cin >> base >> height;
    if (base < 1 || base > 1000 || height < 1 || height > 1000) {
        cout << "Invalid Base or Height" << endl;
        return 1;
    }

    Circle circle(radius);
    Rectangle rectangle(length, breadth);
    Triangle triangle(base, height);

    cout << fixed << setprecision(5);
    cout << "Area of Circle: " << circle.calculateArea() << endl;
    cout << "Area of Rectangle: " << rectangle.calculateArea() << endl;
    cout << "Area of Triangle: " << triangle.calculateArea() << endl;

    return 0;
}
```

# 2. Matrix Multiplication Using Function Overloading

## Objective
Implement matrix operations in C++ using function overloading. Write a function `operate()` that can perform:
- Matrix Addition for matrices of the same dimensions.
- Matrix Multiplication where the number of columns of the first matrix equals the number of rows of the second matrix.

## Input Format
- Matrix A: A 2D matrix of dimensions m×n
- Matrix B: A 2D matrix of dimensions n×p
- An integer indicating the operation type:
  - 1 for Matrix Addition
  - 2 for Matrix Multiplication

## Constraints
- 1 ≤ m, n, p ≤ 10
- Matrix elements are integers in the range -100 to 100

## Output Format
- For Matrix Addition, print the resulting matrix.
- For Matrix Multiplication, print the resulting matrix.
- If dimensions are invalid for the chosen operation, output: "Invalid dimensions for operation."

## Test Cases:

### Example 1: Matrix Addition

**Input:**
Matrix A:
1 2
3 4
Matrix B:
5 6
7 8
Operation: 1

**Output:**
6 8
10 12

### Example 2: Matrix Multiplication

**Input:**
Matrix A:
1 2 3
4 5 6
Matrix B:
7 8
9 10
11 12
Operation: 2

**Output:**
58 64
139 154

### Example 3: Invalid Dimensions

**Input:**
Matrix A:
1 2 3
4 5 6
Matrix B:
7 8 9
10 11 12
Operation: 2

**Output:**
Invalid dimensions for operation.

## Solution
```cpp
#include <iostream>
#include <vector>

using namespace std;

void addMatrices(const vector<vector<int>>& A, const vector<vector<int>>& B, vector<vector<int>>& result) {
    int m = A.size();
    int n = A[0].size();
    
    if (A.size() != B.size() || A[0].size() != B[0].size()) {
        cout << "Invalid dimensions for operation." << endl;
        return;
    }

    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            result[i][j] = A[i][j] + B[i][j];
        }
    }
}

void multiplyMatrices(const vector<vector<int>>& A, const vector<vector<int>>& B, vector<vector<int>>& result) {
    int m = A.size();
    int n = A[0].size();
    int p = B[0].size();
    
    if (n != B.size()) {
        cout << "Invalid dimensions for operation." << endl;
        return;
    }

    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < p; ++j) {
            result[i][j] = 0;
            for (int k = 0; k < n; ++k) {
                result[i][j] += A[i][k] * B[k][j];
            }
        }
    }
}

int main() {
    int m, n, p, operation;
    
    cout << "Enter dimensions of matrix A (m n): ";
    cin >> m >> n;
    
    vector<vector<int>> A(m, vector<int>(n));
    cout << "Enter elements of matrix A: " << endl;
    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            cin >> A[i][j];
        }
    }
    
    cout << "Enter dimensions of matrix B (n p): ";
    cin >> n >> p;
    
    vector<vector<int>> B(n, vector<int>(p));
    cout << "Enter elements of matrix B: " << endl;
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < p; ++j) {
            cin >> B[i][j];
        }
    }
    
    cout << "Enter operation type (1 for addition, 2 for multiplication): ";
    cin >> operation;

    vector<vector<int>> result;
    
    if (operation == 1) {
        result = vector<vector<int>>(m, vector<int>(n));
        addMatrices(A, B, result);
        
        cout << "Result of addition: " << endl;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                cout << result[i][j] << " ";
            }
            cout << endl;
        }
    } 
    else if (operation == 2) {
        result = vector<vector<int>>(m, vector<int>(p));
        multiplyMatrices(A, B, result);
        
        cout << "Result of multiplication: " << endl;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < p; ++j) {
                cout << result[i][j] << " ";
            }
            cout << endl;
        }
    } 
    else {
        cout << "Invalid operation type." << endl;
    }

    return 0;
}
```


# 3. Polymorphism in Shape Classes

## Objective:

Design a C++ program using polymorphism to calculate the area of different shapes:
- A Rectangle (Area = Length × Breadth).
- A Circle (Area = π × Radius²).
- A Triangle (Area = ½ × Base × Height).

Create a base class `Shape` with a pure virtual function `getArea()`. Use derived classes `Rectangle`, `Circle`, and `Triangle` to override this function.

## Input Format
- Shape type (1 for Rectangle, 2 for Circle, 3 for Triangle).
- For Rectangle: Length and Breadth.
- For Circle: Radius.
- For Triangle: Base and Height.

## Constraints
- Shape type is an integer: 1 ≤ type ≤ 3.
- Dimensions are integers: 1 ≤ Dimension Value ≤ 100.
- Use π = 3.14159 for Circle Area calculation.

## Test Cases:

### Example 1: Rectangle Area

**Input:**
Shape Type: 1Length: 5Breadth: 4  

**Output:**
The area of the rectangle is: 20

### Example 2: Circle Area

**Input:**
Shape Type: 2Radius: 7  

**Output:**
The area of the circle is: 153.938

### Example 3: Triangle Area

**Input:**
Shape Type: 3Base: 10Height: 6  

**Output:**
The area of the triangle is: 30

## Solution:
```cpp
#include <iostream>
#include <cmath>
using namespace std;

class Shape {
public:
    virtual double getArea() const = 0;
    virtual ~Shape() {}
};

class Rectangle : public Shape {
    double length, breadth;
public:
    Rectangle(double l, double b) : length(l), breadth(b) {}
    double getArea() const override {
        return length * breadth;
    }
};

class Circle : public Shape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    double getArea() const override {
        return 3.14159 * radius * radius;
    }
};

class Triangle : public Shape {
    double base, height;
public:
    Triangle(double b, double h) : base(b), height(h) {}
    double getArea() const override {
        return 0.5 * base * height;
    }
};

int main() {
    int shapeType;
    cin >> shapeType;

    if (shapeType == 1) {
        double length, breadth;
        cin >> length >> breadth;
        if (length < 1 || length > 100 || breadth < 1 || breadth > 100) {
            cout << "Invalid dimensions" << endl;
            return 1;
        }
        Rectangle rect(length, breadth);
        cout << "The area of the rectangle is: " << rect.getArea() << endl;

    } else if (shapeType == 2) {
        double radius;
        cin >> radius;
        if (radius < 1 || radius > 100) {
            cout << "Invalid dimensions" << endl;
            return 1;
        }
        Circle circ(radius);
        cout << "The area of the circle is: " << circ.getArea() << endl;

    } else if (shapeType == 3) {
        double base, height;
        cin >> base >> height;
        if (base < 1 || base > 100 || height < 1 || height > 100) {
            cout << "Invalid dimensions" << endl;
            return 1;
        }
        Triangle tri(base, height);
        cout << "The area of the triangle is: " << tri.getArea() << endl;

    } else {
        cout << "Invalid shape type" << endl;
    }

    return 0;
}
```


# 4. Implement Multiple Inheritance to Simulate a Library System

## Objective
Create a C++ program using multiple inheritance to simulate a library system. Design two base classes:
- `Book` to store book details (title, author, and ISBN).
- `Borrower` to store borrower details (name, ID, and borrowed book).

Create a derived class `Library` that inherits from both `Book` and `Borrower`. Use this class to track the borrowing and returning of books.

## Input Format
- Book Details: Title, Author, ISBN.
- Borrower Details: Name, ID.
- Action type:
  - 1 to Borrow a Book.
  - 2 to Return a Book.

## Constraints
- Book title and author are strings (max length 50).
- ISBN is an integer: 1000 ≤ ISBN ≤ 9999.
- Borrower ID is an integer: 1 ≤ ID ≤ 1000.

## Test Cases:

### Example 1: Borrow a Book

**Input:**
Book Details:Title: C++ BasicsAuthor: John DoeISBN: 1234Borrower Details:Name: AliceID: 42  

**Output:**
Borrower Alice (ID: 42) has borrowed "C++ Basics" by John Doe (ISBN: 1234).

### Example 2: Return a Book

**Input:**
Book Details:Title: C++ BasicsAuthor: John DoeISBN: 1234Borrower Details:Name: AliceID: 42Action: 2  

**Output:**
Borrower Alice (ID: 42) has returned "C++ Basics" by John Doe (ISBN: 1234).

### Example 3: Invalid Action

**Input:**
Book Details:Title: Advanced C++Author: Jane SmithISBN: 5678Borrower Details:Name: BobID: 99Action: 3  

**Output:**
Invalid action type.

## Solution
```cpp
#include <iostream>
#include <string>
using namespace std;

// Base class for Book details
class Book {
protected:
    string title;
    string author;
    int ISBN;
public:
    Book(string t, string a, int i) : title(t), author(a), ISBN(i) {}
    string getTitle() const { return title; }
    string getAuthor() const { return author; }
    int getISBN() const { return ISBN; }
};

// Base class for Borrower details
class Borrower {
protected:
    string name;
    int ID;
    string borrowedBook;
public:
    Borrower(string n, int id) : name(n), ID(id), borrowedBook("") {}
    string getName() const { return name; }
    int getID() const { return ID; }
    string getBorrowedBook() const { return borrowedBook; }
    void borrowBook(const string& bookTitle) { borrowedBook = bookTitle; }
    void returnBook() { borrowedBook = ""; }
};

// Derived class for Library
class Library : public Book, public Borrower {
public:
    Library(string t, string a, int i, string n, int id) : Book(t, a, i), Borrower(n, id) {}

    void performAction(int actionType) {
        if (actionType == 1) {
            borrowBook(getTitle());
            cout << "Borrower " << getName() << " (ID: " << getID() << ") has borrowed \"" << getTitle() << "\" by " << getAuthor() << " (ISBN: " << getISBN() << ")." << endl;
        } else if (actionType == 2) {
            returnBook();
            cout << "Borrower " << getName() << " (ID: " << getID() << ") has returned \"" << getTitle() << "\" by " << getAuthor() << " (ISBN: " << getISBN() << ")." << endl;
        } else {
            cout << "Invalid action type." << endl;
        }
    }
};

int main() {
    string title, author, name;
    int ISBN, ID, actionType;

    cout << "Enter Book Title: ";
    cin >> title;
    cout << "Enter Book Author: ";
    cin >> author;
    cout << "Enter ISBN: ";
    cin >> ISBN;

    cout << "Enter Borrower Name: ";
    cin >> name;
    cout << "Enter Borrower ID: ";
    cin >> ID;

    cout << "Enter Action (1 to borrow, 2 to return): ";
    cin >> actionType;

    Library lib(title, author, ISBN, name, ID);
    lib.performAction(actionType);

    return 0;
}
```


# 5. Implement Polymorphism for Banking Transactions

## Objective
Design a C++ program to simulate a banking system using polymorphism. Create a base class `Account` with a virtual method `calculateInterest()`. Use the derived classes `SavingsAccount` and `CurrentAccount` to implement specific interest calculation logic:
- **SavingsAccount**: Interest = Balance × Rate × Time.
- **CurrentAccount**: No interest, but includes a maintenance fee deduction.

## Input Format
1. Account Type (1 for Savings, 2 for Current).
2. Account Balance (integer).
3. For Savings Account: Interest Rate (as a percentage) and Time (in years).
4. For Current Account: Monthly Maintenance Fee.

## Constraints
- Account type: 1 ≤ type ≤ 2.
- Balance: 1000 ≤ balance ≤ 1,000,000.
- Interest Rate: 1 ≤ rate ≤ 15.
- Time: 1 ≤ time ≤ 10.
- Maintenance Fee: 50 ≤ fee ≤ 500.

## Test Cases:

### Example 1: Savings Account Interest

**Input:**
Account Type: 1Balance: 10000Interest Rate: 5Time: 3  

**Output:**
Savings Account Interest: 1500

### Example 2: Current Account Fee

**Input:**
Account Type: 2Balance: 20000Maintenance Fee: 200  

**Output:**
Balance after fee deduction: 19800

### Example 3: Invalid Account Type

**Input:**
Account Type: 3  

**Output:**
Invalid account type.

## Solution
```cpp
#include <iostream>
using namespace std;

class Account {
public:
    virtual void calculateInterest() = 0;
    virtual ~Account() {}
};

class SavingsAccount : public Account {
    int balance, rate, time;
public:
    SavingsAccount(int b, int r, int t) : balance(b), rate(r), time(t) {}
    void calculateInterest() override {
        cout << "Savings Account Interest: " << (balance * rate * time) / 100 << endl;
    }
};

class CurrentAccount : public Account {
    int balance, fee;
public:
    CurrentAccount(int b, int f) : balance(b), fee(f) {}
    void calculateInterest() override {
        cout << "Balance after fee deduction: " << balance - fee << endl;
    }
};

int main() {
    int type;
    cin >> type;

    if (type == 1) {
        int balance, rate, time;
        cin >> balance >> rate >> time;
        if (balance < 1000 || balance > 1000000 || rate < 1 || rate > 15 || time < 1 || time > 10) {
            cout << "Invalid input" << endl;
            return 1;
        }
        SavingsAccount sa(balance, rate, time);
        sa.calculateInterest();
    } else if (type == 2) {
        int balance, fee;
        cin >> balance >> fee;
        if (balance < 1000 || balance > 1000000 || fee < 50 || fee > 500) {
            cout << "Invalid input" << endl;
            return 1;
        }
        CurrentAccount ca(balance, fee);
        ca.calculateInterest();
    } else {
        cout << "Invalid account type." << endl;
    }

    return 0;
}
```
