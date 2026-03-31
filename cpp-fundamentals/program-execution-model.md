# Program Execution Model

When one develops a C++ program, it does not run directly. Instead, it goes through a fixed sequence of steps before your computer actually understands and executes it.

### Running Your Source Code

Let's start with a simple single-file C++ program. The following _prints **Hello World**_ to the console.

{% code title="main.cpp" %}
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, world!" << std::endl;
    return 0;
}
```
{% endcode %}

This file is called the **source code.**

To run it, we need to compile the code:

{% code title="" %}
```sh
clang++ main.cpp -o hello-world
```
{% endcode %}

This will produce an executable file called `hello-world` which your computer can finally run:

{% code title="" %}
```sh
./hello-world
```
{% endcode %}

Each time you make changes to the source code, you will need to compile again.

<figure><img src="../.gitbook/assets/Screenshot 2026-04-01 at 2.03.33 AM.png" alt=""><figcaption></figcaption></figure>

### What Just Happened ?!

Think of a compiler as a black box that simply _**converts**_ source code to machine code.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>src: <a href="https://www.sitesbay.com/cpp/cpp-compiler">https://www.sitesbay.com/cpp/cpp-compiler</a></p></figcaption></figure>

<details>

<summary>What does a compiler exactly do?</summary>

This is beyond the scope of this workshop.

If you happen to be curious:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>src: <a href="https://www3.ntu.edu.sg/home/ehchua/programming/cpp/gcc_make.html">https://www3.ntu.edu.sg/home/ehchua/programming/cpp/gcc_make.html</a></p></figcaption></figure>

Compiling a C++ source code is usually a 4 step process. It composes of&#x20;

**a) preprocessing** where we substitute macros and header files with their actual content

**b) compilation** from C++ to platform-specific assembly

**c) assemble** where the resultant assembly code is assembled into actual object code

**d) linking** to link external library functions that the executable needs

You can even pause the compilation process at each stage to inspect the immediate outputs using varying CLI flags.

</details>

