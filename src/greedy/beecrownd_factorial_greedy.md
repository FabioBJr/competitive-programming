# 1936- Factorial

**Time limit:** 1.00 s

[Submit Solution](https://judge.beecrowd.com/en/problems/view/1936)

## Description
The factor of a positive integer $N$, denoted by $N!$, is defined as the product of the positive integers smaller than or equal to N. For example $4! = 4 × 3 × 2 × 1 = 24$.

Given a positive integer $N$, you should write a program to determine the smallest number $k$ such that $N = a_1! + A_2! + ... + A_k!$, where each ai, for $1 ≤ i ≤ k$ is a positive integer.

For example, for $N = 10$ the answer is 3, it is possible to write N as the sum of three numbers factor: $10 = 3! + 2! + 2!$. For $N = 25$ the answer is 2, it is possible to write $N$ as the sum of two factorial numbers: $25 = 4! + 1!$.

## Input

The input consists of a single line containing an integer **N** $(1 ≤ N ≤ 10^5)$.

## Output

Its program should produce a single line with an integer representing the smallest amount of factor numbers whose sum is equal to the value of **N**.

## Example
| Input | Output |
| :--- | :--- |
| `10` | `3` |
| `25` | `2` |

---

### Implementation in C++
```cpp
#include <bits/stdc++.h>

using namespace std;

#define endl "\n"

int fact(int n) {
    if(n <= 1)
        return 1;

    return fact(n-1) * n;
}

int main() {
    ios_base::sync_with_stdio(false);cin.tie(NULL);
    int n, ans = 0; cin >> n;
    vector<int> v;

    for(int i=1; i<n; i++) {
        int temp = fact(i);
        if(n >= temp) {
            v.push_back(temp);
        } else break;
    }

    while(n > 0) {
        for(int i=v.size()-1; i>=0; i--) {
            if(n >= v[i]) {
                n -= v[i];
                ans++;
                break;
            }
        }
    }

    cout << ans << endl;

    return 0;
}
```

### Optimized version
```cpp
// 1. Gera fatoriais APENAS até ultrapassar 'n'
for(int i = 1; ; i++) {
    temp *= i;
    if(temp > n) break; // Protege contra o Integer Overflow
    v.push_back(temp);
}

// Como os fatoriais foram inseridos na ordem (1, 2, 6, 24...), 
// o último elemento é garantidamente o maior.
    
// 2. Lógica Gulosa: Percorre de trás para frente (do maior para o menor)
for(int i = v.size() - 1; i >= 0; i--) {
    // Usamos um 'while' para poder usar o mesmo fatorial várias vezes,
    // o que substitui a necessidade do seu 'break' e reinício do loop externo.
    while(n >= v[i]) {
        n -= v[i];
        cout << v[i] << " + ";
        ans++;
    }
}
```