# 1944 - FACE 2015 FREE GIFT

[Submit Solution](https://judge.beecrowd.com/pt/problems/view/1944)

## Description
In this year of 2015, FACE is supporting the third edition of the Programming Marathon, but, at this time, organization's staff is requesting your help to create a lottery system by using the FACE letters. As this fair uses a differentiated and cheerful proposal, each participant who enters into the fair receives 4 letters, each of them in a different color and in the form of a wooden block, as shown in Figure 1, and they must insert them in a panel. If, by the entering time, the 4 letters create the opposite of the 4 last letters, this visitor will receive the free gift.

For example: suppose there have already been three visitors who entered into the fair and the letters' distribution remained as follows: F A C E E C F A A C F E A C E F. See that the panel, for being empty, the letters F A C E were inserted in order to start the process, now, as the fourth visitor enters, he has inserted the letters F E C A and, with it, they will receive the free gift as it got the opposite of A C E F. After this situation, the letters must remain F A C E E C F A A C F E. Another important fact is that, the free gifts' distribution occurs in a certain period with a sample of a selected visitors number. REMENBER, always when the panel remains empty it is automatically inserted the letters F A C E.

## Input

The input contains several test cases. The first line of a test case contains an integer $N (1 ≤ N ≤ 100)$, representing the number of visitors who will receive the letters. In each subsequent line it must be informed the $4$ letters combination separated by space that the visitor wishes to insert on the panel. The stop is determined by $N$ equals to $0$.

## Output

For each of group of visitors, it must be informed how many of them will receive free gifts.

## Example
| Input | Output |
| :--- | :--- |
| 4<br>E C F A<br>A C E F<br>F E C A<br>A F C E | 2|

| Input | Output |
| :--- | :--- |
| 4<br>E A C F<br>A F C E<br>E F C A | 0 |

---

### Implementation in C++
```cpp
#include <bits/stdc++.h>

using namespace std;
#define dbg(x) cerr << #x << " = " << x << endl;
#define endl "\n"

int main() {
    ios_base::sync_with_stdio(false);cin.tie(NULL);
    int n; cin >> n;
    string panel = "FACE";
    int ans = 0;

    while(n--) {
        if (panel.empty()) {
            panel = "FACE";
        }

        char c1, c2, c3, c4;
        cin >> c1 >> c2 >> c3 >> c4;

        int len = panel.length();

        if(c1 == panel[len - 1] &&
           c2 == panel[len - 2] &&
           c3 == panel[len - 3] &&
           c4 == panel[len - 4]) {
            ans++;
            panel.erase(len - 4);
        } else {
            panel += c1;
            panel += c2;
            panel += c3;
            panel += c4;
        }
    }

    cout << ans << endl;

    return 0;
}
```