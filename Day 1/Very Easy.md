
# 1. Sum of Natural Numbers up to N

## Problem Statement
Calculate the sum of all natural numbers from 1 to `n`, where `n` is a positive integer. The sum can be computed using the following formula:

```
Sum = n * (n + 1) / 2
```

Given an integer `n`, print the sum of all natural numbers from 1 to `n`.

## Task
Write a program to calculate the sum of natural numbers from 1 to `n`.

### Input Format
- One integer `n`, the upper limit for calculating the sum.

### Constraints
- `1 ≤ n ≤ 10^4`

### Output Format
- Print the sum of all natural numbers from 1 to `n`.

## Test Cases

### Example 1
**Input:**
```
5
```

**Output:**
```
15
```

**Explanation:**
Using the formula, 
```
Sum = 5 * (5 + 1) / 2 = 15
```

### Example 2
**Input:**
```
100
```

**Output:**
```
5050
```

**Explanation:**
Using the formula, 
```
Sum = 100 * (100 + 1) / 2 = 5050
```

### Example 3
**Input:**
```
1
```

**Output:**
```
1
```

**Explanation:**
Using the formula, 
```
Sum = 1 * (1 + 1) / 2 = 1
```
## Solution

<!-- solution:start -->
<!-- tabs:start -->

#### C++

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    if (n < 1 || n > 10000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    cout << n * (n + 1) / 2 << endl;
    return 0;
}

```

<!-- tabs:end -->

<!-- solution:end -->


# 2. Check if a Number is Prime

## Objective
Check if a given number `n` is a prime number. A prime number is a natural number greater than 1 that has no positive divisors other than 1 and itself. 

To determine if a number is prime, iterate from 2 to √n and check if `n` is divisible by any number in this range. If it is divisible, it is not a prime number; otherwise, it is a prime.

## Task
Given an integer `n`, print "Prime" if the number is prime, or "Not Prime" if it is not.

### Input Format
- One integer `n`.

### Constraints
- `2 ≤ n ≤ 10^5`

### Output Format
- Print "Prime" if `n` is prime, otherwise print "Not Prime".

## Test Cases

### Example 1
**Input:**
```
7
```

**Output:**
```
Prime
```

**Explanation:**
7 has no divisors other than 1 and itself, so it is a prime number.

### Example 2
**Input:**
```
9
```

**Output:**
```
Not Prime
```

**Explanation:**
9 is divisible by 3, so it is not a prime number.

### Example 3
**Input:**
```
2
```

**Output:**
```
Prime
```

**Explanation:**
2 is a prime number as it has only two divisors: 1 and 2.

## Solution

<!-- solution:start -->
<!-- tabs:start -->

#### C++

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 2 || n > 100000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    bool isPrime = true;
    for (int i = 2; i <= sqrt(n); i++) {
        if (n % i == 0) {
            isPrime = false;
            break;
        }
    }

    if (isPrime) {
        cout << "Prime" << endl;
    } else {
        cout << "Not Prime" << endl;
    }

    return 0;
}

```

<!-- tabs:end -->

<!-- solution:end -->


# 3. Print Odd Numbers up to N

## Objective
Print all odd numbers between 1 and `n`, inclusive. Odd numbers are integers that are not divisible by 2. These numbers should be printed in ascending order, separated by spaces.

This problem is a simple introduction to loops and conditional checks. The goal is to use a loop to iterate over the numbers and check if they are odd using the condition `i % 2 ≠ 0`.

## Task
Given an integer `n`, print all odd numbers from 1 to `n`, inclusive.

### Input Format
- One integer `n`, the upper limit of the range.

### Constraints
- `1 ≤ n ≤ 10^4`

### Output Format
- A single line containing all odd numbers from 1 to `n`, separated by spaces.

## Test Cases

### Example 1
**Input:**
```
10
```

**Output:**
```
1 3 5 7 9
```

### Example 2
**Input:**
```
7
```

**Output:**
```
1 3 5 7
```

### Example 3
**Input:**
```
1
```

**Output:**
```
1
```
## Solution

<!-- solution:start -->
<!-- tabs:start -->

#### C++

```cpp
#include <iostream>
using namespace std;
int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 10000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    for (int i = 1; i <= n; i += 2) {
        cout << i;
        if (i + 2 <= n) {
            cout << " ";
        }
    }
    cout << endl;

    return 0;
}

```

<!-- tabs:end -->

<!-- solution:end -->
# 4. Sum of Odd Numbers up to N

## Objective
Calculate the sum of all odd numbers from 1 to n. An odd number is an integer that is not divisible by 2. The sum of odd numbers, iterate through all the numbers from 1 to n, check if each number is odd, and accumulate the sum.

## Task
Given an integer n, print the sum of all odd numbers from 1 to n.

## Input Format
One integer n, the upper limit of the range.

## Constraints
- 1 ≤ n ≤ 10^4

## Output Format
Print the sum of all odd numbers from 1 to n.

## Test Cases:
### Example 1:
**Input:**
5

**Output:**
9

**Explanation:**
The odd numbers are 1, 3, 5. Their sum is 1+3+5=9.

### Example 2:
**Input:**
10

**Output:**
25

**Explanation:**
The odd numbers are 1, 3, 5, 7, 9. Their sum is 1+3+5+7+9=25.

### Example 3:
**Input:**
1

**Output:**
1

**Explanation:**
The only odd number is 1.
## Solution

<!-- solution:start -->
<!-- tabs:start -->

#### C++

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 10000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    int sum = 0;
    for (int i = 1; i <= n; i += 2) {
        sum += i;
    }

    cout << sum << endl;

    return 0;
}


```

<!-- tabs:end -->

<!-- solution:end -->

# 5. Print Multiplication Table of a Number

## Objective
Print the multiplication table of a given number n from 1×n to 10×n.

## Task
Given an integer n, print the multiplication table of n.

## Input Format
One integer n.

## Constraints
- 1 ≤ n ≤ 100

## Output Format
For each integer i from 1 to 10, print the product n×i in the format: n x i = product

## Test Cases

### Example 1:
**Input:**
3

**Output:**
```
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
3 x 4 = 12
3 x 5 = 15
3 x 6 = 18
3 x 7 = 21
3 x 8 = 24
3 x 9 = 27
3 x 10 = 30
```

### Example 2:
**Input:** 
7

**Output:**
```
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
```

### Example 3:
**Input:** 
10

**Output:**
```
10 x 1 = 10
10 x 2 = 20
10 x 3 = 30
10 x 4 = 40
10 x 5 = 50
10 x 6 = 60
10 x 7 = 70
10 x 8 = 80
10 x 9 = 90
10 x 10 = 100
```

## Solution

<!-- solution:start -->
<!-- tabs:start -->

#### C++

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 100) {
        cout << "Invalid input" << endl;
        return 1;
    }

    for (int i = 1; i <= 10; i++) {
        cout << n << " x " << i << " = " << n * i << endl;
    }

    return 0;
}

```

<!-- tabs:end -->

<!-- solution:end -->
