
# 1. Count Digits in a Number

## Objective
Count the total number of digits in a given number n. The number can be a positive integer. For example, for the number 12345, the count of digits is 5. For a number like 900000, the count of digits is 6.

## Task
Given an integer n, your task is to determine how many digits are present in n. This task will help you practice working with loops, number manipulation, and conditional logic.

## Input Format
One integer n.

## Constraints
- 1 ≤ n ≤ 10^9

## Output Format
Print the number of digits in n.

## Test Cases

### Example 1:
**Input:**
12345

**Output:**
5

**Explanation:**
The number 12345 has 5 digits: 1, 2, 3, 4, 5.

### Example 2:
**Input:**
900000

**Output:**
6

**Explanation:**
The number 900000 has 6 digits: 9, 0, 0, 0, 0, 0.

### Example 3:
**Input:**
1

**Output:**
1

**Explanation:**
The number 1 has only 1 digit.
## Solution

<!-- solution:start -->
<!-- tabs:start -->

#### C++

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, count = 0;
    cin >> n;
    if (n < 1 || n > 1000000000) {
        cout << "Invalid input" << endl;
        return 1;
    }
    while (n != 0) {
        n /= 10;
        count++;
    }
    cout << count << endl;
    return 0;
}

```

<!-- tabs:end -->

<!-- solution:end -->

# 2. Reverse a Number

## Objective
Reverse the digits of a given number n. For example, if the input number is 12345, the output should be 54321. The task involves using loops and modulus operators to extract the digits and construct the reversed number.

## Task
Given an integer n, print the number with its digits in reverse order.

## Input Format
One integer n.

## Constraints
- 1 ≤ n ≤ 10^9

## Output Format
Print the number with its digits in reverse order.

## Test Cases

### Example 1:
**Input:**
12345

**Output:**
54321

**Explanation:**
The digits of 12345 in reverse order are 54321.

### Example 2:
**Input:**
9876

**Output:**
6789

**Explanation:**
The digits of 9876 in reverse order are 6789.

### Example 3:
**Input:**
1000

**Output:**
1

**Explanation:**
The digits of 1000 in reverse order are 0001, which is equivalent to 1 since leading zeros are not typically shown in numbers.

## Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 1000000000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    int reversed = 0;
    while (n != 0) {
        int digit = n % 10;
        reversed = reversed * 10 + digit;
        n /= 10;
    }

    cout << reversed << endl;

    return 0;
}
```
# 3. Find the Largest Digit in a Number

## Objective
Find the largest digit in a given number n. For example, for the number 2734, the largest digit is 7. You need to extract each digit from the number and determine the largest one. The task will involve using loops and modulus operations to isolate the digits.

## Task
Given an integer n, find and print the largest digit in n.

## Input Format
One integer n.

## Constraints
- 1 ≤ n ≤ 10^9

## Output Format
Print the largest digit in the number n.

## Test Cases

### Example 1:
**Input:**
2734

**Output:**
7

**Explanation:**
The digits of 2734 are 2, 7, 3, and 4. The largest digit is 7.

### Example 2:
**Input:**
9450

**Output:**
9

**Explanation:**
The digits of 9450 are 9, 4, 5, and 0. The largest digit is 9.

### Example 3:
**Input:**
1111

**Output:**
1

**Explanation:**
All digits of 1111 are 1, so the largest digit is also 1.

## Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 1000000000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    int largest = 0;
    while (n != 0) {
        int digit = n % 10;
        if (digit > largest) {
            largest = digit;
        }
        n /= 10;
    }

    cout << largest << endl;

    return 0;
}
```


# 4. Check if a Number is a Palindrome

## Objective
Check whether a given number is a palindrome or not. A number is called a palindrome if it reads the same backward as forward. For example, 121 is a palindrome because reading it from left to right is the same as reading it from right to left. Similarly, 12321 is also a palindrome, but 12345 is not.

## Task
Given an integer n, print "Palindrome" if the number is a palindrome, otherwise print "Not Palindrome".

## Input Format
One integer n.

## Constraints
- 1 ≤ n ≤ 10^9

## Output Format
Print "Palindrome" if the number is a palindrome, otherwise print "Not Palindrome".

## Explanation
- For input n=121, the number is the same when reversed, so it is a palindrome.
- For input n=12345, the number is not the same when reversed, so it is not a palindrome.

## Test Cases

### Example 1
**Input:**
121

**Output:**
Palindrome

**Explanation:**
The number 121 reads the same backward as forward.

### Example 2:
**Input:**
12345

**Output:**
Not Palindrome

**Explanation:**
The number 12345 does not read the same backward as forward.

### Example 3:
**Input:**
12321

**Output:**
Palindrome

**Explanation:**
The number 12321 reads the same backward as forward.

## Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 1000000000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    int original = n;
    int reversed = 0;

    while (n != 0) {
        int digit = n % 10;
        reversed = reversed * 10 + digit;
        n /= 10;
    }

    if (original == reversed) {
        cout << "Palindrome" << endl;
    } else {
        cout << "Not Palindrome" << endl;
    }

    return 0;
}
```


# 5. Find the Sum of Digits of a Number

## Objective
Calculate the sum of the digits of a given number n. For example, for the number 12345, the sum of the digits is 1+2+3+4+5=15. To solve this, you will need to extract each digit from the number and calculate the total sum.

## Task
Given an integer n, find and print the sum of its digits.

## Input Format
One integer n.

## Constraints
- 1 ≤ n ≤ 10^9

## Output Format
Print the sum of the digits of n.

## Test Cases

### Example 1
**Input:**
12345

**Output:**
15

**Explanation:**
The digits of 12345 are 1, 2, 3, 4, and 5. The sum is 1 + 2 + 3 + 4 + 5 = 15.

### Example 2:
**Input:**
4567

**Output:**
22

**Explanation:**
The digits of 4567 are 4, 5, 6, and 7. The sum is 4 + 5 + 6 + 7 = 22.

### Example 3:
**Input:**
999

**Output:**
27

**Explanation:**
The digits of 999 are 9, 9, and 9. The sum is 9 + 9 + 9 = 27.

## Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    if (n < 1 || n > 1000000000) {
        cout << "Invalid input" << endl;
        return 1;
    }

    int sum = 0;
    while (n != 0) {
        sum += n % 10;
        n /= 10;
    }

    cout << sum << endl;

    return 0;
}

