# Control Flow

So far, our programs have executed line-by-line, step-by-step from top to bottom. In the real world however, we might want to

* make decisons based on a condition
* repeat certain actions
* organise logic into reusable pieces

This is where **control flow** comes in

### Conditionals

Conditionals let our program make decisions.

{% code title="main.cpp" %}
```cpp
int score = 85;

if (score == 100) {
    std::cout << "Perfect" << std::endl;
} else if (score >= 90) {
    std::cout << "Grade A" << std::endl;
} else if (score >= 80) {
    std::cout << "Grade B" << std::endl;
} else if (score >= 70) {
    std::cout << "Grade C" << std::endl;
} else {
    std::cout << "Needs improvement" << std::endl;
}
```
{% endcode %}

{% hint style="info" %}
⚠️ Common Pitfall

`=` means assignment while `==` checks for equality

{% code title="" %}
```cpp
int x = 5;      // assignment
x == 5;         // comparison
```
{% endcode %}
{% endhint %}

### Loops

Loops lets us repeat certain blocks of code

#### while loop

A `while` loop keeps running as long as the condition is fufilled.

<table><thead><tr><th width="354.14404296875">Code</th><th>Output</th></tr></thead><tbody><tr><td><pre class="language-cpp" data-title=""><code class="lang-cpp">int x = 1;

while (x &#x3C;= 5) {
    std::cout &#x3C;&#x3C; x &#x3C;&#x3C; std::endl;
    x++;
}
</code></pre></td><td><img src="../.gitbook/assets/Screenshot 2026-04-01 at 12.19.51 PM.png" alt="" data-size="original"></td></tr></tbody></table>

#### for loop

A `for` loop is useful when we know how many times we want to repeat something.

<table><thead><tr><th width="353.73614501953125"></th><th></th></tr></thead><tbody><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp">for (int i = 1; i &#x3C;= 5; i++) {
    std::cout &#x3C;&#x3C; i &#x3C;&#x3C; std::endl;
}
</code></pre></td><td><img src="../.gitbook/assets/image (2).png" alt="" data-size="original"></td></tr></tbody></table>

#### break / continue

`break` forces the loop to terminate prematurely.

`continue` skips the rest of the current iteration.

<table><thead><tr><th width="354.77777099609375"></th><th></th></tr></thead><tbody><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp">for (int i = 1; i &#x3C;= 5; i++) {
    if (i == 3) {
        break;
    }
    std::cout &#x3C;&#x3C; i &#x3C;&#x3C; std::endl;
}
</code></pre></td><td><p><img src="../.gitbook/assets/Screenshot 2026-04-01 at 12.25.16 PM.png" alt="" data-size="original"></p><p></p></td></tr><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp">for (int i = 1; i &#x3C;= 5; i++) {
    if (i == 3) {
        continue;
    }
    std::cout &#x3C;&#x3C; i &#x3C;&#x3C; std::endl;
}
</code></pre></td><td><img src="../.gitbook/assets/Screenshot 2026-04-01 at 12.24.30 PM.png" alt="" data-size="original"></td></tr></tbody></table>

### Functions

Functions let us group code into reusable blocks.

#### Basic Usage

{% code title="main.cpp" %}
```cpp
#include <iostream>

void greet() {
    std::cout << "Hello!" << std::endl;
}

int main() {
    greet();
}
```
{% endcode %}

Here:

* `void` means the function does not return anything
* `greet` is the function name
* `greet()`  _calls_ the function, causing **Hello!** to be printed.

#### Function Parameters

Our current `greet` function always print the same message (which isn't very flexible). Let's augment it by adding a parameter so that our greeting message can change depending on the person.

{% code title="main.cpp" %}
```cpp
#include <iostream>

void greet(std::string name) {
    std::cout << "Hello, " << name << "!" << std::endl;
}

int main() {
    greet("Benn");
    greet("Bryan");
    greet("Anton Tim");
}
```
{% endcode %}

#### Functions Return Value

A return value is the value the function sends back to the caller after it's done executing. At the call site, you can use the result however you wish.

{% code title="main.cpp" %}
```cpp
#include <iostream>

int add(int x, int y) {
    return x + y;
}

int main() {
    int result = add(3, 4);
    std::cout << result << std::endl;
}
```
{% endcode %}

### Exercise(s)

⭐ Write a function `countdown(int n)` that takes in a number `n` and prints from `n` down to 1.

{% code title="" %}
```shellscript
countdown(5)
5
4
3
2
1
```
{% endcode %}

⭐⭐ Write a program that hardcodes a secret number. It will repeatedly ask the user to guess. Depending on the user's guess, the program will feedback **Too low, Too high** or **Correct.**

{% code title="" %}
```
Guess the number: 50
Too high

Guess the number: 25
Too low

Guess the number: 30
Too low

Guess the number: 42
Correct!
```
{% endcode %}
