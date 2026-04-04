# 🐳 Arrays & Strings

Thus far, pointers pointed to a singular variable. But what if we have multiple values stored together (exactly, like an array!)

### Arrays

To declare an array:

{% code title="" %}
```cpp
int arr[3] = {10, 20, 30}; // array
int* p_arr = arr;          // pointer to array
```
{% endcode %}

Visually, this is how an array is represented:

<figure><img src="../.gitbook/assets/Screenshot 2026-04-05 at 12.46.02 AM.png" alt=""><figcaption></figcaption></figure>

Note that:

* All 3 elements sit **side-by-side** (i.e there exists no gaps between them). This is what we mean by **contiguous memory.**
* You may also have noticed that the difference between each memory address is 4 bytes. This because (usually) `int` occupies 4 bytes.

### Pointer Arithmetic

Since `p_arr`  stores the address of the first element, you can access `arr[0]` via dereferencing `*p_arr`. &#x20;

What about `arr[1]`? The cool thing about pointer arithmetic is that it's **type-aware,** you can simply perform `(p_arr + 1)` to move forward by 1 element of type `int` (i.e 4 bytes).

Functionally,

<table><thead><tr><th width="243.72222900390625">Operation</th><th>Result</th></tr></thead><tbody><tr><td><code>*p_arr</code></td><td>Move <code>p_arr</code> by 0 bytes, dereference to get <code>arr[0]</code></td></tr><tr><td><code>*(p_arr + 1)</code></td><td>Move <code>p_arr</code> by 4 bytes, dereference to get <code>arr[1]</code></td></tr><tr><td><code>*(p_arr + 2)</code></td><td>Move <code>p_arr</code> by 8 bytes, dereference to get <code>arr[2]</code></td></tr></tbody></table>

Note that `arr` is also decays into a pointer to the first element that shares the same memory address as `p_arr`, hence operations that can be done with `arr` can also be done with `p_arr`&#x20;

{% code title="main.cp" %}
```cpp
#include <iostream>

int main() {
    int arr[3] = {10, 20, 30};
    std::cout << arr[0] << std::endl; // 10
    std::cout << arr[1] << std::endl; // 20
    std::cout << arr[2] << std::endl; // 30
    
    std::cout << *(arr + 0) << std::endl; // 10
    std::cout << *(arr + 1) << std::endl; // 20
    std::cout << *(arr + 2) << std::endl; // 30
    
    int* p_arr = arr;
    std::cout << *(p_arr + 0) << std::endl; // 10
    std::cout << *(p_arr + 1) << std::endl; // 20
    std::cout << *(p_arr + 2) << std::endl; // 30
}
```
{% endcode %}

<details>

<summary>😎 Cool Fun Fact</summary>

We've learnt that we can access `arr[0]` via `*(arr + 0)`. Since addition is commutative, `*(arr + 0) == *(0 + arr)`, hence `0[arr]` works too!

{% code title="main.cpp" %}
```cpp
#include <iostream>
int main()
{
    int arr[3] = {10, 20, 30};
    std::cout << 1 [arr] << std::endl;
    std::cout << arr[1] << std::endl;
}
```
{% endcode %}

</details>

### Strings

Fundamentally, a string is simply an _array_ of characters ending with a special character `\0` (i.e null terminator)

The usual pointer arithmetic rules that we've learnt above apply too.

{% code title="main.cpp" %}
```cpp
#include <iostream>

int main() {
    char str[] = "hello";
    std::cout << str[0] << std::endl;        // 'h'
    std::cout << *(str + 1) << std::endl;    // 'e'
    
    char* str2 = "world";
    std::cout << str2[0] << std::endl;        // 'w'
    std::cout << *(str2 + 1) << std::endl;    // 'o'
}
```
{% endcode %}

Notice when we compile, we get a warning:

<figure><img src="../.gitbook/assets/Screenshot 2026-04-05 at 1.17.41 AM.png" alt=""><figcaption></figcaption></figure>

<details>

<summary>😕 Why the warning for <code>char str2*</code> but not <code>char str[]</code> ?</summary>

`"hello"`  is a string literal stored in read-only memory.

`char[]` has no issues since it copies the string literal onto its own array on the stack.

`char *` is pointing to the same string literal in read-only memory. Writing to it causes undefined behaviour hence the warning.

In fact, if you try compiling the program with stricter flags: `clang++ -std=c++17 -Wall -Wextra -pedantic-errors main.cpp -o hello-world`, the compiler rejects the code entirely.

<figure><img src="../.gitbook/assets/Screenshot 2026-04-05 at 1.20.16 AM.png" alt=""><figcaption></figcaption></figure>

To squash this, we can use `const char *`  to assert that we are not going to modify the string.

</details>
