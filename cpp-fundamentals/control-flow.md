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

