# 1110 - Throwing Cards Away

[Submit Solution](https://judge.beecrowd.com/en/problems/view/1110)

## Description

Given in an ordered deck of n cards numbered 1 to n with card 1 at the top and card n at the bottom. The following operation is performed as long as there are at least two cards in the deck:

Throw away the top card and move the card that is now on the top of the deck to the bottom of the deck.

Your task is to find the sequence of discarded cards and the last, remaining card.

Each line of input (except the last) contains a number n ≤ 50. The last line contains 0 and this line should not be processed. For each number from the input produce two lines of output. The first line presents the sequence of discarded cards, the second line reports the last remaining card.

## Input (Entrada)

The input file contains a non determinated number of lines. Each line contains an integer number. The last line contain the number zero (0).

## Output (Saída)

For each test case, print two lines. The first line presents the sequence of discarded cards, each number separated by a comma ',' and one blank space. The second line reports the last remaining card. No line will have leading or trailing spaces. See the sample for the expected format.

## Examples

| Input | Output |
| :--- | :--- |
| `7`<br>`19`<br>`10`<br>`6`<br>`0` | `Discarded cards: 1, 3, 5, 7, 4, 2`<br>`Remaining card: 6`<br>`Discarded cards: 1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 4, 8, 12, 16, 2, 10, 18, 14`<br>`Remaining card: 6`<br>`Discarded cards: 1, 3, 5, 7, 9, 2, 6, 10, 8`<br>`Remaining card: 4`<br>`Discarded cards: 1, 3, 5, 2, 6`<br>`Remaining card: 4` |
---

### Implementation in C++

```cpp
#include <bits/stdc++.h>

using namespace std;
#define dbg(x) cerr << #x << " = " << x << endl;
#define endl "\n"

int main() {
    ios_base::sync_with_stdio(false);cin.tie(NULL);
    int n;
    do {
        cin >> n;
        deque<int> d;
        vector<int> v;

        if(n !=0) {
            for(int i = 1; i <= n; i++) {
                d.push_back(i);
            }

            while(d.size() > 1) {
                v.push_back(d.front());
                d.pop_front();
                d.push_back(d.front());
                d.pop_front();
            }

            cout << "Discarded cards: ";
            for(int i=0; i < v.size(); i++) {
                if(i < v.size()-1) {
                    cout << v[i] << ", ";
                } else {
                    cout << v[i] << endl;
                }
            }
            cout << "Remaining card: " << d.front() << endl;
        }

    } while(n != 0);



    return 0;
}
```