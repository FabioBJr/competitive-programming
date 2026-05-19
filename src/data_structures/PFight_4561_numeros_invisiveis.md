# 4561 - Números Invisíveis

[Submit Solution](#https://cp.nextline.com.br/problem/171)

## Descrição

Considere a sequência de todos os inteiros positivos em ordem crescente: 1, 2, 3, … Alguns desses números contêm o dígito 0 na sua escrita decimal — por exemplo, 10, 20, 100, 305. Chamamos de invisível todo número que não possui o dígito 0 em nenhuma posição.

A sequência dos invisíveis é: 1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, …, 19, 21, …, 99, 111, …

Note que após o 9 vem direto o 11 — o 10 é "pulado" por conter um zero. Da mesma forma, 20, 30, …, 100, 101, 110, … são todos pulados.

**Problem:**
Os números invisíveis podem ser indexados: o 1º é 1, o 2º é 2, …, o 9º é 9, o 10º é 11, e assim por diante. Dado N, encontre o N-ésimo número invisível.

## Input (Entrada)

Um único inteiro N $$(1 \\le N \\le 2^{63})$$.

## Output (Saída)

Um único inteiro: o N-ésimo número invisível.

## Examples

| Input | Output |
| :--- | :--- |
| `5` | `5` |
| `59` | `65` |
| `140` | `165` |
| `65536` | `98797` |

---

## Solution

O problema pode ser modelado como uma variação de **mudança de base**. Como os "números invisíveis" utilizam apenas os dígitos de 1 a 9, estamos na prática trabalhando com um sistema de **base 9**. 

No entanto, há um pequeno detalhe conhecido como *numeração bijetiva* (base sem o zero). Quando o resto da divisão por 9 for 0, em vez de adicionarmos um '0' à nossa resposta (o que é inválido para números invisíveis), nós adicionamos o dígito '9' e "emprestamos" 1 do próximo valor a ser dividido (`n = n / 9 - 1`).

### Implementação em C++
```cpp
#include <bits/stdc++.h>

using namespace std;

#define endl '\n'

int main() {

    unsigned long long n; cin >> n;
    vector<int> v;

    while(n > 0) {
        if (n % 9 == 0) {
            v.push_back(9);
            n = n / 9 - 1;
        } else {
            v.push_back(n%9);
            n /=9;
        }
    }

    for(int i=v.size()-1;i>=0;i--) cout << v[i];

    cout<<endl;

    return 0;
}
```