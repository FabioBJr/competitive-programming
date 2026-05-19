# 1164- Room Allocation

**Time limite** 1.00 s **Memory limit: 512 MB**

[Submit Solution](https://cses.fi/problemset/task/1164)

## Description
There is a large hotel, and n customers will arrive soon. Each customer wants to have a single room.

You know each customer's arrival and departure day. Two customers can stay in the same room if the departure day of the first customer is earlier than the arrival day of the second customer.

What is the minimum number of rooms that are needed to accommodate all customers? And how can the rooms be allocated?

## Input (Entrada)

The first input line contains an integer n: the number of customers.

Then there are n lines, each of which describes one customer. Each line has two integers a and b: the arrival and departure day.

## Output (Saída)

Print first an integer $k$: the minimum number of rooms required.

After that, print a line that contains the room number of each customer in the same order as in the input. The rooms are numbered 1,2,..., $k$. You can print any valid solution.

## Constraints
* $1 \le n \le 2 * 10^5$
* $1 \le a \le b \le 10^9$
---

### Implementation in C++
```cpp
#include <bits/stdc++.h>
using namespace std;
#define endl "\n"
#define all(x) x.begin(), x.end()
#define pb push_back
 
int main() {
 
    int n; cin >> n;
 
    vector<tuple<int, int , int>> customers(n);
 
    for(int i=0; i<n; i++) {
        int s, e; cin >> s >> e;
        customers[i] = make_tuple(s, e, i);
    }
 
    sort(all(customers));
 
    int room_count = 0;
    vector<int> ans(n);
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
 
    for(int i=0; i<n; i++) {
        int currStart = get<0>(customers[i]);
        int currEnd = get<1>(customers[i]);
        int originIdx = get<2>(customers[i]);
 
        if (!pq.empty() && pq.top().first < currStart) {
            int roomId = pq.top().second;
            pq.pop();
            pq.push({currEnd, roomId});
            ans[originIdx] = roomId;
        } else {
            room_count++;
            pq.push({currEnd, room_count});
            ans[originIdx] = room_count;
        }
    }
 
    cout << room_count << endl;
    for(int n : ans) cout << n << " ";
 
    return 0;
}
```
