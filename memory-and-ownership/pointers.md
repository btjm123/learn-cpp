# 🦋 Pointers

### Address of Variables

So far, we've been working with variables like:

{% code title="main.cpp" %}
```cpp
int x = 10;
```
{% endcode %}

But sometimes, we don't want the value itself, rather we will want to know **where is this value stored in memory?**

The variable `x` could have some address like `0x100..`.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2026-04-04 at 11.44.10 PM.png" alt=""><figcaption></figcaption></figure>

We don't know so lets find out using the ampersand `&` operator.

{% code title="main.cpp" %}
```cpp
int main()
{
    int x = 10;
    std::cout << "location of x: " << &x << std::endl;
}
```
{% endcode %}

<figure><img src="../.gitbook/assets/Screenshot 2026-04-04 at 11.46.24 PM.png" alt=""><figcaption></figcaption></figure>

### Type of Pointers

We know the type of `x`  is an `integer` , but what's the type of `&x` ?&#x20;

Instead of second guessing ourselves, let's rely on the C++ compiler to tell us. C++ offers a [`typeid` function ](https://en.cppreference.com/w/cpp/language/typeid.html)that seems useful:

{% code title="main.cpp" %}
```cpp
int main()
{
    int x = 10;
    std::cout << typeid(x).name() << std::endl;
    std::cout << typeid(&x).name() << std::endl;
}
```
{% endcode %}

<figure><img src="../.gitbook/assets/Screenshot 2026-04-04 at 11.52.29 PM.png" alt=""><figcaption></figcaption></figure>

The output may look cryptic but:

* `i` (as you might have guessed) represents **int**
* `Pi` (which you also might have guessed) represents **pointer to int** (`int*`)

Indeed, we can write it like so:

<table><thead><tr><th>Code</th><th>Visual Aid</th></tr></thead><tbody><tr><td><pre class="language-cpp"><code class="lang-cpp">int main()
{
    int x = 10;
    int* p = &#x26;x;
}
</code></pre></td><td><img src="../.gitbook/assets/Screenshot 2026-04-04 at 11.59.56 PM.png" alt=""></td></tr></tbody></table>

### De-referencing

Given a pointer of type (`int *`),  is there a way I can get the _actual_ _value (_&#x61;nd not the address) it points to?&#x20;

In other words,

{% code title="main.cpp" %}
```cpp
int main()
{
    int x = 10;
    int* p = &x;
    
    // can i get 10 using variable p alone?
}
```
{% endcode %}

Yes we can! Since the pointer `p`  stores an address, we can dereference the pointer using `*` to get the value! Think of dereferencing as follow the address to get the value stored there.

<table><thead><tr><th>Code</th><th>Visual Aid</th></tr></thead><tbody><tr><td><pre class="language-cpp"><code class="lang-cpp">int main()
{
    int x = 10;
    int* p = &#x26;x;
    int y = *p;
    
    std::cout &#x3C;&#x3C; "value of x: " &#x3C;&#x3C; x &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "value of y: " &#x3C;&#x3C; y &#x3C;&#x3C; std::endl;
}
</code></pre></td><td><img src="../.gitbook/assets/Screenshot 2026-04-05 at 12.15.36 AM.png" alt=""></td></tr></tbody></table>

Realise while both values of x and y are the same, they are **not** pointing to the same 10. They each contain their own version of 10 (and possess their own memory addresses).&#x20;

<details>

<summary>How do you make <code>x</code>  and <code>y</code> to point to the same 10 then?</summary>

Simple: we don't make two variables. We declare 1 variable and multiple pointers to the same variable.

<table><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp">#include &#x3C;iostream>

int main() {
    int x = 10;
    int* y = &#x26;x;   // y points to x
    int* z = &#x26;x;   // z also points to x

    std::cout &#x3C;&#x3C; x &#x3C;&#x3C; std::endl;   // 10
    std::cout &#x3C;&#x3C; *y &#x3C;&#x3C; std::endl;  // 10

    *y = 20;  // modify via pointer

    std::cout &#x3C;&#x3C; x &#x3C;&#x3C; std::endl;   // 20 (x changed!)
}
</code></pre></td><td><img src="../.gitbook/assets/Screenshot 2026-04-05 at 12.25.38 AM.png" alt=""></td></tr></tbody></table>

</details>

### Pointer-Ception

And yes because pointers also have addresses, we can have _pointers that point to a pointer that points to a value._

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th>Code</th><th>Output</th></tr></thead><tbody><tr><td><pre class="language-cpp" data-title="main.cpp"><code class="lang-cpp"><strong>#include &#x3C;iostream>
</strong>
int main() {
    int x = 10;            // normal variable
    int* p = &#x26;x;           // pointer to x
    int** pp = &#x26;p;         // pointer to pointer

    std::cout &#x3C;&#x3C; "x value: " &#x3C;&#x3C; x &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "Address of x (&#x26;x): " &#x3C;&#x3C; &#x26;x &#x3C;&#x3C; std::endl;

    std::cout &#x3C;&#x3C; "p (points to x): " &#x3C;&#x3C; p &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "Value at p (*p): " &#x3C;&#x3C; *p &#x3C;&#x3C; std::endl;

    std::cout &#x3C;&#x3C; "pp (points to p): " &#x3C;&#x3C; pp &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "Value at pp (*pp): " &#x3C;&#x3C; *pp &#x3C;&#x3C; std::endl;
    std::cout &#x3C;&#x3C; "Value at *pp (**pp): " &#x3C;&#x3C; **pp &#x3C;&#x3C; std::endl;

    return 0;
}
</code></pre></td><td><img src="../.gitbook/assets/Screenshot 2026-04-05 at 12.27.53 AM.png" alt="" data-size="original"></td></tr></tbody></table>

