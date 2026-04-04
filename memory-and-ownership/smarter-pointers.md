# 🐽 Smarter Pointers

As we've seen, we humans are pretty dumb and inept at managing memory.&#x20;

Here's where smart pointers come in! They are smarter abstractions introduced in C++11 to help us manage memory automatically.

### Unique Pointers

#### Basics

{% code title="main.cpp" %}
```cpp
#include <iostream>
#include <memory>

int main() {
    std::unique_ptr<int> score = std::make_unique<int>(100);
    std::cout << *score << std::endl;
} // automatically deleted here
```
{% endcode %}

Semantically, unique pointers convey the idea there is **exactly only one owner** of the resource being pointed to.&#x20;

Unique pointers:

* cannot be copied
* can be moved
* are automatically deleted when it goes out of scope

#### Transferring Ownership

{% code title="main.cpp" %}
```cpp
#include <memory>

void consume(std::unique_ptr<int> p) {
    // owns the pointer
}

int main() {
    auto x = std::make_unique<int>(50);
    consume(std::move(x));  // transfer ownership
}
```
{% endcode %}

### Shared Pointers

{% code title="main.cpp" %}
```cpp
#include <iostream>
#include <memory>

int main() {
    auto p1 = std::make_shared<int>(10);
    auto p2 = p1;  // shared ownership

    std::cout << *p1 << std::endl; // 10
    std::cout << *p2 << std::endl; // 10
}
```
{% endcode %}

Both `p1` and `p2` point to the same object. Memory for the integer 10 is only free'ed when both `p1` and `p2` goes out o scope.&#x20;

Internally, a `shared _ptr` uses a reference count to track when it shoud deallocate. We can see the live reference count by invoking `use_count().`

{% code title="main.cpp" %}
```cpp
#include <iostream>
#include <memory>

int main() {
    auto p1 = std::make_shared<int>(10);
    std::cout << p1.use_count() << std::endl; // 1

    auto p2 = p1;
    std::cout << p1.use_count() << std::endl; // 2
}
```
{% endcode %}

### Tackling Our Original Code

#### Exercise

Given the original code in [memory-painpoints.md](memory-painpoints.md "mention"), can you try to use some of these abstractions to create better, memory-safe code?

<details>

<summary>Answer</summary>

{% code title="main.cpp" %}
```cpp
#include <iostream>
#include <memory>

std::unique_ptr<int> spawnScoreBonus() {
    return std::make_unique<int>(100);
}

std::unique_ptr<int> generatePlayerHealth() {
    return std::make_unique<int>(50);
}

int main() {
    std::unique_ptr<int> score = spawnScoreBonus();
    std::cout << "Player gained score: " << *score << std::endl;

    std::unique_ptr<int> health = generatePlayerHealth();
    std::cout << "Player health: " << *health << std::endl;

    std::shared_ptr<int> enemyHp = std::make_shared<int>(200);
    std::shared_ptr<int> archerTarget = enemyHp;
    std::shared_ptr<int> knightTarget = enemyHp;

    return 0;
}
```
{% endcode %}

</details>
