# 1287B - Hyperset

[Submit Solution](https://codeforces.com/contest/1287/problem/B)

## Description

As abelhas Alice e Alesya deram à apicultora Polina o famoso jogo de cartas "Set" como presente de Natal. O baralho consiste em cartas que variam em $k$ características, cada uma com três opções possíveis: 'S', 'E' ou 'T'.

Neste jogo, diz-se que uma combinação de três cartas diferentes forma um **set** se, para cada uma das $k$ características, as três cartas apresentarem essa característica como todas iguais ou todas mutuamente diferentes.

Dada uma coleção de $n$ cartas distintas, sua tarefa é encontrar o número de maneiras de escolher três cartas que formem um **set**.

## Input (Entrada)

A primeira linha contém dois inteiros $n$ e $k$ ($1 \\le n \\le 1500$, $1 \\le k \\le 30$) — o número de cartas e o número de características de cada carta, respectivamente.

Cada uma das próximas $n$ linhas contém uma string contendo exatamente $k$ caracteres. Cada caractere é 'S', 'E' ou 'T'. Todas as strings fornecidas são distintas.

## Output (Saída)

Imprima um único inteiro — o número de maneiras de escolher três cartas que formam um **set**.

## Examples

| Input | Output |
| :--- | :--- |
| `3 3`<br>`SET`<br>`ETS`<br>`TSE` | `1` |
| `3 4`<br>`SETE`<br>`ETSE`<br>`TSES` | `0` |
| `5 4`<br>`SETT`<br>`TEST`<br>`EEET`<br>`ESTE`<br>`STES` | `2` |

---

### Implementation in C++
```cpp
#include <bits/stdc++.h>

using namespace std;

#define endl "\n"
#define dbg(x) cerr << #x << " = " << x << endl;
int main() {
    ios_base::sync_with_stdio(false); cin.tie(NULL);
    int n, m, ans = 0; cin >> n >> m;
    vector<string> v;
    set<string> s;

    for(int i=0; i<n; i++) {
        string temp; cin >> temp;
        v.push_back(temp);
        s.insert(temp);
    }

    for(int i=0; i<n-1; i++) {
        for(int j=i+1; j<n; j++) {
            string target(m,' ');
            for(int k = 0; k<m; k++) {
                if(v[i][k] == v[j][k]) {
                    target[k] = v[i][k];
                } else {
                    target[k] = ('S' + 'E' + 'T') - v[i][k] - v[j][k];
                }
            }
            
            if(s.find(target) != s.end()) ans++;
        }
    }

    cout << ans/3 << endl;

    return 0;

}
```