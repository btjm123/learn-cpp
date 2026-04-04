# 🧚‍♀️ Basic Syntax & I/O

Let's kick things off by familiarising ourselves with the basic structure of a C++ program.

### Anatomy of a C++ Program

Recall the source code you previously saw:

{% code title="main.cpp" %}
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, world!";
    return 0;
}
```
{% endcode %}

Breaking it down:

<table><thead><tr><th width="190.94439697265625">Code</th><th>What it does</th></tr></thead><tbody><tr><td><pre><code>#include &#x3C;iostream>
</code></pre></td><td>Brings in the standard I/O library so that we can use things like <code>std::cout</code></td></tr><tr><td><pre><code>int main() {
</code></pre></td><td><p>The entry point of every C++ program.</p><p></p><ul><li><code>int</code>  indicates the return type of the function </li><li><code>main</code> is the function name.</li></ul></td></tr><tr><td><pre><code>std::cout &#x3C;&#x3C; "Hel...
</code></pre></td><td><p>Prints the text to the console.</p><p></p><p>👉 You can remember <code>&#x3C;&#x3C;</code> as <em>pushing</em> the text into the output stream (i.e <code>std::cout</code> in this case)</p></td></tr><tr><td><pre><code>return 0;
</code></pre></td><td><p>Recall that <code>int</code> is the return type of the <code>main</code> function.</p><p></p><p>Hence, at the end of our <code>main</code> function, we should<sup>[1]</sup> return an int.</p><p></p><p>You can return anything, really. But usually returning 0 indicates our program has successfully executed.</p></td></tr></tbody></table>

{% hint style="info" %}
Try augmenting the `Hello, world!` string to something else like your name!

![](<../.gitbook/assets/Screenshot 2026-04-01 at 2.36.09 AM.png>)
{% endhint %}

<sub>\[1] Your code will still compile even if you don't return anything from the main function.  This is because C++ implicilty returns 0 at the end of</sub> <sub></sub><sub>`main()`</sub><sub>. For more info, refer</sub> [<sub>here</sub>](https://stackoverflow.com/questions/19293642/why-does-the-main-function-work-with-no-return-value)<sub>.</sub>

### Newlines

If you try printing multiple times, you will notice that the output gets concatenated on the same line. You can fix this by adding a newline using `std::endl` .

<table><thead><tr><th>Code</th><th>Output</th></tr></thead><tbody><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp">#include &#x3C;iostream>

int main()
{
    std::cout &#x3C;&#x3C; "benn";
    std::cout &#x3C;&#x3C; "tan";
    std::cout &#x3C;&#x3C; "jia";
    return 0;
}
</code></pre></td><td><p><img src="../.gitbook/assets/Screenshot 2026-04-01 at 2.42.36 AM.png" alt="" data-size="original"></p><p></p></td></tr><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp">#include &#x3C;iostream>

int main()
{
    std::cout &#x3C;&#x3C; "benn" &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "tan" &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "jia";
    return 0;
}
</code></pre></td><td><p><img src="../.gitbook/assets/Screenshot 2026-04-01 at 2.43.39 AM.png" alt="" data-size="original"></p><p></p></td></tr></tbody></table>

### Input

It's not quite fun if we hardcode everything into program. Let's augment our program to accept user input externally.

To read input from the user, we can use `std::cin >>`

{% code title="main.cpp" %}
```cpp
#include <iostream>

int main() {
    int x;
    std::cin >> x;
    std::cout << "You entered: " << x << std::endl;
}
```
{% endcode %}

{% hint style="info" %}
Note that the direction of the arrows (`>>`) for `std::cin` is now reversed compared to `<<`.&#x20;

👉 You can remember as **data flowing into `x`**.
{% endhint %}

### Namespaces

If you find prefixing `std::` before the function calls cumbersome, you can  omit it with `using namespace std`

{% code title="main.cpp" %}
```cpp
#include <iostream>
using namespace std;
int main() {
    int x;
    cin >> x;
    cout << "You entered: " << x << endl;
}
```
{% endcode %}

However, this is generally discouraged in larger projects as it does lead to naming conflicts.

👉 It's usually best practice to be explicit and use `std::`&#x20;

### Exercise

Build a program that takes in and prints the result of the summation of two numbers.
