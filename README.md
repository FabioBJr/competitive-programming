# Cheat Sheet

Useful for consulting a specific structure or library.

## Quick Start Template

```cpp
#include <bits/stdc++.h> // Includes every standard library (very useful in marathons)
#include <ext/pb_ds/assoc_container.hpp> // ordered_set
#include <ext/pb_ds/tree_policy.hpp>     // ordered_set

using namespace std;
using namespace __gnu_pbds; // ordered_set

// Compilation flag guide for C++20: g++ -x c++ -O2 -std=gnu++20 -static

// --- TYPEDEFS & MACROS ---
typedef long long ll;         // Use ll for large numbers to avoid overflow
typedef pair<int, int> pii;   // Useful for coordinates or pairs of values
typedef vector<int> vi;
// => set structure with find_by_order() function
typedef tree<int, null_type, less<int>, rb_tree_tag, tree_order_statistics_node_update> ordered_set; 

#define endl '\n'             // Faster than std::endl (doesn't flush the buffer)
#define pb push_back          // Shorthand for vector insertion
#define f first
#define s second
#define all(x) x.begin(), x.end() // Useful for sort(all(v))

#ifdef LOCAL
#define dbg(x) cerr << #x << " = " << x << endl;
#else
#define dbg(x) 42
#endif

const int INF = 0x3f3f3f3f;
const ll LINF = 0x3f3f3f3f3f3f3f3fll;

void fast_io() {
    // This makes cin/cout as fast as scanf/printf
    ios_base::sync_with_stdio(false); cin.tie(NULL);
}

int main() {
    fast_io();

    // Your logic goes here
    
    return 0;
}

```

---

## Included Libraries & Structures

### Standard Libraries

* **`<bits/stdc++.h>`**: A GCC-specific header that includes almost every standard C++ library (like `<iostream>`, `<vector>`, `<algorithm>`, etc.). It saves time during contests as you don't need to manually include multiple headers.
* **Policy-Based Data Structures (PBDS)**:
* `<ext/pb_ds/assoc_container.hpp>` and `<ext/pb_ds/tree_policy.hpp>` are included to use `ordered_set`.
* **`ordered_set`**: Functions like a regular `std::set` (using a Red-Black tree under the hood) but adds features like finding the $k$-th smallest element (`find_by_order`) or counting elements strictly smaller than a given value (`order_of_key`) in $O(\log n)$ time.



### Functions & Optimizations

* **`fast_io()`**: Essential for performance. It disables synchronization between C and C++ standard streams (`ios_base::sync_with_stdio(false)`) and unties `cin` from `cout` (`cin.tie(NULL)`), making standard I/O as fast as C's `scanf`/`printf`.

### Shortcuts & Type Definitions

* **`ll` (`long long`)**: Prevents integer overflow when dealing with large numbers up to ~ $9 \times 10^{18}$.
* **`pii` (`pair<int, int>`)**: A quick shortcut for declaring a pair of integers, heavily used for coordinates or graph edges.
* **`vi` (`vector<int>`)**: A short alias for a dynamic array of integers.
* **`INF` and `LINF`**: Constants representing safely large numbers for integer and long long types, respectively. `0x3f3f3f3f` is useful because `INF + INF` won't overflow a 32-bit integer.

### Macros

* **`endl` (`'\n'`)**: Redefining `endl` to `'\n'` speeds up output significantly by avoiding continuous flushing of the stream buffer.
* **`pb`**: Replaces `push_back` to save keystrokes.
* **`f` / `s`**: Shortcuts for `.first` and `.second` when working with pairs.
* **`all(x)`**: Expands to `x.begin(), x.end()`. Highly useful for quick sorting or searching, e.g., `sort(all(v))`.
* **`dbg(x)`**: A local debugging macro. If the code is compiled with `-DLOCAL`, it prints the variable name and its value to the standard error stream (`cerr`). Otherwise, it does nothing, preventing debug output from causing Wrong Answers on online judges.

---

## Standard Template Library (STL) Reference

### 1. Pair (`std::pair<T1, T2>`)

* **Characteristics**: Stores two heterogeneous objects as a single unit.
* **Usage**: `pair<int, string> p = {1, "Name"};`
* **Access**: `p.first` (or `p.f`) and `p.second` (or `p.s`).
* **Comparison**: Pairs are compared lexicographically (first element first, then second).

### 2. Set (`std::set<T>`)

* **Characteristics**:
* Does not allow duplicates.
* Elements are always sorted (default is ascending).
* Time Complexity: $O(\log n)$ for search, insert, and delete.


* **Usage**: `set<int> s; s.insert(10);`
* **Important**: To check if an element exists, use `s.find(value) != s.end()`.

### 3. Map (`std::map<K, V>`)

* **Characteristics**:
* Stores key-value pairs.
* Keys are kept sorted in order.
* Time Complexity: $O(\log n)$ for search and access.


* **Usage**: `map<string, int> m; m["apple"] = 5;`
* **Note**: If you access a key that doesn't exist (e.g., `m["banana"]`), it automatically creates that key with a default value (like `0`).
