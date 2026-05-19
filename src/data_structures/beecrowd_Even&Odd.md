# 1259 - Even and Odd

[Submit Solution](https://judge.beecrowd.com/en/problems/view/1259)

## Description
Considering the input of non-negative integer values​​, sort these numbers ​​according to the following criteria: First the even in ascending order followed by the odd in descending order.

## Entrada (Input)

The first line of input contains a positive integer number N (1 < N <= 105). This is the number of following input lines. The next N lines<br> contain, each one, a integer non-negative number.

## Saída (Output)

Print all numbers according to the explanation presented above. Each number must be printed in one line as shown below.

---

### Implementação em C++
```cpp
#include <bits/stdc++.h>

using namespace std;
#define dbg(x) cerr << #x << " = " << x << endl;
#define endl "\n"

bool customSort(int a, int b) {
    bool isAEven = (a%2 == 0);
    bool isBEven = (b%2 == 0);

    //Evens always come before Odds
    if (isAEven && !isBEven) return true;
    if (!isAEven && isBEven) return false;

    if (isAEven && isBEven) return a < b;

    return a > b;
}

int main() {
    ios_base::sync_with_stdio(false);cin.tie(NULL);
   
    int n; cin >> n;
    vector<int> v(n);

    for(int i=0; i<n; i++) {
        cin >> v[i];
    };

    sort(v.begin(),v.end(), customSort);

    for(int n : v)
        cout << n << endl;

    return 0;
}
```
