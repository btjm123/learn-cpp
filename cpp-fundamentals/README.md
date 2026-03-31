# C++ Fundamentals

This guide aims to provide you with the fundamentals of C++. It's **not** meant to be an exhaustive guide. For more in-depth details, you should refer to the [official C++ reference](https://en.cppreference.com/w/).

We do assume that you have basic programming knowledge and are cognizant of common programming constructs (i.e variables, functions, loops).

### Getting started

To run C++ code, you will need a **compiler**. Alternatively, you can also use an online compiler like [JDoodle](https://www.jdoodle.com/online-compiler-c++17) to follow along.&#x20;

#### Mac

To check if you have the `clang++` compiler installed, run:

```bash
clang++ --version
```

If not, you can install it via:

```bash
xcode-select --install
```

A software update window will pop up. You will need to agree to the licensing agreement before you can commence installing.

If all goes well, you should be greeted with:

<figure><img src="../.gitbook/assets/Screenshot 2026-04-01 at 1.36.05 AM.png" alt=""><figcaption></figcaption></figure>

#### Windows

On Windows, the setup process varies. The simplest option is to install an Integrated Development Environment (IDE) like [Dev-C++](https://www.dev-cpp.com/) that bundles with a C++ compiler.&#x20;

#### Ubuntu / Debian

To check if you have the `g++`  compiler installed, you can check via:

```bash
g++ --version
```

If it is not installed, you can install it via your favourite package manager.

```bash
sudo apt update
sudo apt update g++
```
