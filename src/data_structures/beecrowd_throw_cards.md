# 1110 - Throwing Cards Away

[Submit Solution](https://judge.beecrowd.com/en/problems/view/1110)

## Description

Dada uma pilha de $n$ cartas ordenadas de 1 a $n$, com a carta 1 no topo e a carta $n$ na base. A seguinte operação é realizada enquanto houver pelo menos duas cartas na pilha:
Jogue fora a carta do topo e mova a carta que agora está no topo da pilha para a base da pilha.

Sua tarefa é encontrar a sequência de cartas descartadas e a última carta remanescente.

## Input (Entrada)

O arquivo de entrada contém um número indeterminado de linhas. Cada linha (exceto a última) contém um número $n$ $\le$ 50. A última linha contém o número 0 e esta linha não deve ser processada. 

## Output (Saída)

Para cada número da entrada, produza duas linhas de saída. A primeira linha apresenta a sequência de cartas descartadas, cada número separado por uma vírgula `,` e um espaço em branco. A segunda linha relata a última carta restante. Nenhuma linha terá espaços em branco no início ou no final. Veja o exemplo para o formato esperado.

## Examples

| Input | Output |
| :--- | :--- |
| `7`<br>`19`<br>`10`<br>`6`<br>`0` | `Discarded cards: 1, 3, 5, 7, 4, 2`<br>`Remaining card: 6`<br>`Discarded cards: 1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 4, 8, 12, 16, 2, 10, 18, 14`<br>`Remaining card: 6`<br>`Discarded cards: 1, 3, 5, 7, 9, 2, 6, 10, 8`<br>`Remaining card: 4`<br>`Discarded cards: 1, 3, 5, 2, 6`<br>`Remaining card: 4` |
---

### Implementação em C++

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