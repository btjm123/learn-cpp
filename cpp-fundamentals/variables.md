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
