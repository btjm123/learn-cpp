# 🐧 Memory Painpoints

Fundamentally, ownership answers the question:&#x20;

> Who is responsible for cleaning up this piece of memory?

As we've seen earlier, memory can be allocated on two distinct regions (i.e the stack and the heap)

### Stack

When variables are allocated on the stack, there's no burden on us to deallocate the memory. C++ handles it for us automatically!

{% code title="main.cpp" %}
```cpp
int main() {
    int x = 10;
} // x is automatically destroyed by end of this scope
```
{% endcode %}

### Heap

#### Exercise

I tried my best to write a code snippet to simulate a game I had in mind. Unfortunately, the code doesn't seem to work for some reason. Do you mind helping me find out where the error(s) are ?

{% code title="main.cpp" %}
```cpp
#include <iostream>

int* spawnScoreBonus() {
    return new int(100); 
}

int* generatePlayerHealth() {
    int* health = new int(50);
    delete health;    
    return health;
}

int main() {
    int* score = spawnScoreBonus();
    std::cout << "Player gained score: " << *score << std::endl;

    int* health = generatePlayerHealth();
    std::cout << "Player health: " << *health << std::endl; 

    int* enemyHp = new int(200);
    int* archerTarget = enemyHp;
    int* knightTarget = enemyHp;
    delete knightTarget;
    delete archerTarget;
    
    return 0;
}
```
{% endcode %}

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="26a0">⚠️</span> Memory Issue 1</summary>

The `spawnScoreBonus()` function allocates a new block of memory containing `100` . Ownership of this object is transferred from `spawnScoreBonus()`  to `main()` .

This means the onus is on `main()` to `delete` the object but `score` is never deallocated, leading to a **memory leak**!

</details>



<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="26a0">⚠️</span> Memory Issue 2</summary>

In the `generatePlayerHealth()` function, `health` is deleted before being returned. This means the returned pointer is pointed to free'ed memory.

However, we are still trying to access the value `health` is pointing to in the `main()` function, leading a **dangling-pointer /** **use-after-free.**

</details>



<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="26a0">⚠️</span> Memory Issue 3</summary>

Both `archerTarget` and `knightTarget`  both point to the same integer of 200. So both pointers behave like owners and both delete the same blokc of memory.

This leads to a **double-free** scenario where both owners think they own the shared resource.

</details>

As we have seen earlier, even in a small piece of code, there can be many subtle memory issues. Imagine how many of such bugs exist in larger codebases!&#x20;

To tackle this, modern C++ (since C++11) introduced something a little smarter...
