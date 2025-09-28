# Week05 Quiz1:

## 1. Requirements:

In the task of this week, we intend to apply various operators to higher-order equation objects.
We want to allocate dynamic memory to an array composed of coefficients of higher-order equations and apply various operators to higher-order equation objects.

- Writing code using c++
- Use `Equation` class to complete your code. 
- Changing the provided class is not allowed. You can `only use the provided class and the functions defined within it`.
- You need to store the `given class definitions` in the `Equation.h` file. Store the `function definitions and the main function` in the `main.cpp` file.   
  `(Please submit the above two documents, and if you do not name the main file "main.cpp", the test will not pass and you will receive zero points)`
- Your submitted files should `include only one ".cpp" file named "main.cpp"`. Any ".cpp" files with other names will not be accepted by the test system.
- Please confirm the containment relationship between header file and main file.

<br/>
                  
### Equation class:
- Complete and use the following class:
  ```C++
  class Equation
  {
		friend bool operator==(const Equation& lhs, const Equation& rhs);
		friend ostream& operator<<(ostream& out, const Equation& eq);
	
		friend Equation operator+(const Equation& lhs, const Equation& rhs);
		friend Equation operator-(const Equation& lhs, const Equation& rhs);
		friend Equation operator*(const Equation& lhs, double rhs);
		friend Equation operator*(double lhs, const Equation& rhs);
  
	public:
		Equation(double coefficients[], int number);
		Equation(const Equation& rhs); // copy constructor, set the content of "rhs" to the content of itself
		~Equation();
		int degree() const { return size - 1; }
	
		Equation& operator= (const Equation& rhs);
		Equation& operator+= (const Equation& rhs);
		Equation& operator-= (const Equation& rhs);
		Equation& operator*= (double rhs);
  
	private:
		int size; // size of the coeff array (= degree + 1) 
		double* coeff; // coefs will be an array, store the coefficient of each item
  };
  ```
<br/>


- The degree of the equation is `one less than the number of terms (size)` entered by the user.
- Input and output the coefficients of each term in order from the highest degree to the constant term.  
  e.g. `1 2 3 4 -> x^3+2x^2+3x+4`
- The number of terms n entered by the user is an integer greater than or equal to 2, and n coefficients are input, including those with a coefficient of 0. When outputting the equation, terms with a coefficient of 0 are omitted.  
  e.g. `For the equation 5x^3+0x^2+2x^1-3=0, the number of terms is 4, and the coefficients are 5, 0, 2, -3. Since terms with zero coefficients (including the constant term) are not displayed in the equation output, this equation is printed as 5x^3+2x^1+3=0.`
- When the highest order coefficient is 0, the program will output an error message and ask for re-entry.  
  Error Message: `Error: The highest order coefficient shouldn't be zero. Please enter again.`
- The compound assignment operators (=, +-, -=, *=) are defined as member functions of the class, while the +, -, and * operators are defined as friend functions.
- The *= and * operators are not for the multiplication of equations but for the multiplication of an equation with a real number.
- The calculate result of `eq1` and `eq2` should be storage into another Equation `eq3`.
- Write a program that creates two equations, eq1 and eq2, based on user input and performs the following operations.
```C++
cout << "eq1: " << eq1 << endl; cout << "eq2: " << eq2 << endl; 
Equation C = eq1 + eq2; 
cout << "eq1+eq2: " << C << endl; 
if (eq1 == eq2) 
cout << "eq1 and eq2 are equal" << endl; 
else { 
cout << "eq1 and eq2 are not equal" << endl; 
Equation D = eq1 - eq2; 
cout << "eq1-eq2: " << D << endl; } 
Equation eq3(eq1); 
cout << "eq3 after eq3(eq1): " << eq3 << endl; 
eq3 += eq2; 
cout << "eq3 after eq3+=eq2: " << eq3 << endl; 
Equation eq4 = eq3 * 0.5; 
cout << "eq3*0.5: " << eq4 << endl; 
Equation eq5 = 4 * eq3; 
cout << "4*eq3: " << eq5 << endl;
```
  
<br/>

### Input
- The first line contains a number (int type) representing the number of terms in the first equation.  
  e.g. `4`
- The second line, enter the coefficients of each term starting from the highest degree to the constant term separate with spaces.  
  e.g. `1 2 0 4`.
- The third line contains a number (int type) representing the number of terms in the second equation.  
  e.g. `5`
- The fourth line, enter the coefficients of each term starting from the highest degree to the constant term separate with spaces.  
  e.g. `1 2 0 0 5`.

<br/>

### Output  

- Output the first equation on the first line.   
  e.g. `eq1: 1x^2-2=0`
- Output the second equation on the second line.  
  e.g. `eq2: 2x^3-4=0`
- Output the sum of the first and the second equation on the third line.  
  e.g. `eq1+eq2: 2x^3+1x^2-6=0`
- Output if the first and the second equation are equal on the 4th line.  
  e.g. `eq1 and eq2 are not equal`
- Output the difference of the first and the second equation on the 5th line.  
  e.g. `eq1-eq2: -2x^3+1x^2+2=0`
- Output the result of `changing eq3 to eq1` on the 6th line.  
  e.g. `eq3 after eq3(eq1): 1x^2-2=0`
- Output the sum of eq3 and eq2 using `+=` on the 7th line.  
  e.g. `eq3 after eq3+=eq2: 2x^3+1x^2-6=0`
- Output the product of eq3 and 0.5 using `*` on the 8th line.  
  e.g. `eq3*0.5: 1x^3+0.5x^2-3=0`
- Output the product of eq3 and 4 using `*` on the 9th line.  
  e.g. `4*eq3: 4x^4+12x^3+8x^2+36=0`


<br/>

### Error handling

-When the highest order coefficient is 0, the program will output an error message and ask for re-entry.  
 Error Message: `Error: The highest order coefficient shouldn't be zero. Please enter again.`

<br/>

## 2. Scoring Criteria (5 points in total):

- Uploaded `Equation.h` and `main.cpp` two files with no compilation errors: 1 point
- The cpp file calls header file and declares the given functions: 2 point
- The result is correct: 2 point

<br/>

## 3 Example
### Example1 (Red font for input, blue font for output):
![image](https://github.com/chyh001228/images/blob/main/w5q1_e1.png)

**Input:**

```
3
0 1 2
0 2 3
1 0 -2
4
2 0 0 -4
```

**Output:**

```
Error: The highest order coefficient shouldn't be zero. Please enter again.
Error: The highest order coefficient shouldn't be zero. Please enter again.
eq1: 1x^2-2=0
eq2: 2x^3-4=0
eq1+eq2: 2x^3+1x^2-6=0
eq1 and eq2 are not equal
eq1-eq2: -2x^3+1x^2+2=0
eq3 after eq3(eq1): 1x^2-2=0
eq3 after eq3+=eq2: 2x^3+1x^2-6=0
eq3*0.5: 1x^3+0.5x^2-3=0
4*eq3: 8x^3+4x^2-24=0
```

**Actual results:**  
![image](https://github.com/chyh001228/images/blob/main/w5q1_c_e1.png)

<br/>

### Example2 (Red font for input, blue font for output):
![image](https://github.com/chyh001228/images/blob/main/w5q1_e2.png)

**Input:**

```
4
1 2.4 0 5
4
1 2.4 0 5
```

**Output:**

```
eq1: 1x^3+2.4x^2+5=0
eq2: 1x^3+2.4x^2+5=0
eq1+eq2: 2x^3+4.8x^2+10=0
eq1 and eq2 are equal
eq3 after eq3(eq1): 1x^3+2.4x^2+5=0
eq3 after eq3+=eq2: 2x^3+4.8x^2+10=0
eq3*0.5: 1x^3+2.4x^2+5=0
4*eq3: 8x^3+19.2x^2+40=0
```

**Actual results:**  
![image](https://github.com/chyh001228/images/blob/main/w5q1_c_e2.png)  
(The deadline is 00:00a.m. on October 5, 2025)

<img src="https://cdn.imweb.me/upload/S201906178853c3e170808/c5d876d707352.jpg" width=30% align=center />
