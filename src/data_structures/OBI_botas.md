# OBI 2017 - Botas Trocadas

[Submit Solution](https://olimpiada.ic.unicamp.br/pratique/p2/2017/f1/botas/)

## Description
A divisão de Suprimentos de Botas e Calçados do Exército comprou um grande número de pares de botas de vários tamanhos para seus soldados. No entanto, por uma falha de empacotamento da fábrica contratada, nem todas as caixas entregues continham um par de botas correto, com duas botas do mesmo tamanho, uma para cada pé. O sargento mandou que os recrutas retirassem todas as botas de todas as caixas para reembalá-las, desta vez corretamente.

Quando o sargento descobriu que você sabia programar, ele solicitou com a gentileza habitual que você escrevesse um programa que, dada a lista contendo a descrição de cada bota entregue, determina quantos pares corretos de botas poderão ser formados no total.

## Input

A primeira linha da entrada contém um inteiro N indicando o número de botas individuais entregues. Cada uma das N linhas seguintes descreve uma bota, contendo um número inteiro M e uma letra L, separados por um espaço em branco. M indica o número do tamanho da bota e L indica o pé da bota: L= ‘D’ indica que a bota é para o pé direito, L= ‘E’ indica que a bota é para o pé esquerdo.

## Output

Seu programa deve imprimir uma única linha contendo um único número inteiro indicando o número total de pares corretos de botas que podem ser formados.

## Contraints
* $2 ≤ N ≤ 10^4$
* $N$ é par
* $30 ≤ M ≤ 60$
* L é o caractere ‘D’ ou o caractere ‘E’

## Example
| Input | Output |
| :--- | :--- |
| `4`<br>`40 D`<br>`41 E`<br>`41 D`<br>`40 E` | `2` |

| Input | Output |
| :--- | :--- |
| `6`<br>`38 E`<br>`39 E`<br>`40 D`<br>`38 D`<br>`40 D`<br>`37 E` | `1` |

---

### Implementation in C++
```cpp
#include <bits/stdc++.h> 

using namespace std;

#define endl '\n'

int main() {

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n; cin >> n;

    vector<pair<int, int>> botas(61,{0,0});

    for(int i = 0; i < n; i++) {
        int siz; cin >> siz;
        char foo; cin >> foo;

        if(foo == 'E') botas[siz].first++;
        else botas[siz].second++;

    }

    int ans = 0;

    for(int i=0; i<botas.size(); i++) {
        ans += min(botas[i].first, botas[i].second);
    }

    cout << ans << endl;

    return 0;
}
```