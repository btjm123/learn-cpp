# Variables

Now that we are able to accept input and print output externally, we need a mechanism to **store data** inside our program.

### What is a Variable?

A variable is simply an named container that stores some value.

{% code title="main.cpp" %}
```cpp
int x = 5;
```
{% endcode %}

In the example above,

* `int`  indicates the **type** of the variable
* `x`  is the **name** of the variable
* `5` is the **value** of the variable

### Common Data Types

|               |                             |                         |
| ------------- | --------------------------- | ----------------------- |
| `int`         | `int age = 24`              | Integer (whole numbers) |
| `double`      | `double pi = 3.14`          | Floating point numbers  |
| `char`        | `char x = 'c'`              | Singular character      |
| `bool`        | `bool isGood = true`        | True / False            |
| `std::string` | `std::string name = "Benn"` | Sequence of characters  |

{% hint style="info" %}
⚠️ Common Pitfall

Use double quotes (`" "`) for strings and single quotes `' '` for characters
{% endhint %}

### Declaration vs Initialisation

Declaration is when we define a variable's **type** and **name** without assigning it a **value** yet. Initialisation is when we give it a **value**.

{% code title="main.cpp" %}
```cpp
int x;      // declaration
x = 10;     // assignment

int y = 10; // declaration + initialisation
```
{% endcode %}

### Arithmetic Operators

You can also perform arithmetic operations just like how you would do in normal math:

{% code title="main.cpp" %}
```cpp
int x = 10;
int y = 12;

int sum = x + y;
int difference = x - y;
int product = x * y;
double quotient = x / y; // note that we use the double here
int remainder = x % y;

int expression = ((x + y) * (x - y));
```
{% endcode %}

{% hint style="info" %}
⚠️ Common Pitfall

Integer division **truncates** the division&#x20;

So `10 / 12 = 0` instead of `0.83`&#x20;
{% endhint %}

### Exercise

Extending from our previous exercise, we now want to support different operations beyond addition. Our mini-calculator should now be able to add, subtract, multiply and divide two numbers!
