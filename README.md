# Atividade-em-Dupla---Algoritmos-e-complexidades

* **Codigos utilizados para resolução das atividades:**
# 2.1
#include <iostream>
using namespace std;

int buscaLinear(int vetor[], int n, int valor, long long &comparacoes) {
    comparacoes = 0;

    for (int i = 0; i < n; i++) {
        comparacoes++;

        if (vetor[i] == valor) {
            return i;
        }
    }

    return -1;
}**

int buscaBinaria(int vetor[], int n, int valor, long long &comparacoes) {
    int inicio = 0;
    int fim = n - 1;

    comparacoes = 0;

    while (inicio <= fim) {
        int meio = inicio + (fim - inicio) / 2;

        comparacoes++;

        if (vetor[meio] == valor) {
            return meio;
        }

        if (vetor[meio] < valor) {
            inicio = meio + 1;
        } else {
            fim = meio - 1;
        }
    }

    return -1;
}

int main() {
    int n;

    cout << "Digite o tamanho do vetor: ";
    cin >> n;

    int *vetor = new int[n];

    for (int i = 0; i < n; i++) {
        vetor[i] = i;
    }

    int valores[3] = {0, n - 1, -1};

    for (int caso = 0; caso < 3; caso++) {
        int valor = valores[caso];

        long long compLinear, compBinaria;

        int posLinear = buscaLinear(
            vetor, n, valor, compLinear
        );

        int posBinaria = buscaBinaria(
            vetor, n, valor, compBinaria
        );

        cout << "\n============================\n";
        cout << "Valor pesquisado: " << valor << endl;

        cout << "\nBusca Linear\n";
        cout << "Posicao: " << posLinear << endl;
        cout << "Comparacoes: " << compLinear << endl;

        cout << "\nBusca Binaria\n";
        cout << "Posicao: " << posBinaria << endl;
        cout << "Comparacoes: " << compBinaria << endl;
    }

    delete[] vetor;

    return 0;
}

# 3.1
#include <iostream>
using namespace std;

int buscaLinear(int vetor[], int n, int valor,
                long long &comparacoes) {
    comparacoes = 0;

    for (int i = 0; i < n; i++) {
        comparacoes++;

        if (vetor[i] == valor) {
            return i;
        }
    }

    return -1;
}

int buscaBinaria(int vetor[], int n, int valor,
                 long long &comparacoes) {
    int inicio = 0;
    int fim = n - 1;

    comparacoes = 0;

    while (inicio <= fim) {
        int meio = inicio + (fim - inicio) / 2;

        comparacoes++;

        if (vetor[meio] == valor) {
            return meio;
        }

        if (vetor[meio] < valor) {
            inicio = meio + 1;
        } else {
            fim = meio - 1;
        }
    }

    return -1;
}

void realizarBusca(int vetor[], int n, int codigo) {

    long long comparacoesLinear;
    long long comparacoesBinaria;

    int posicaoLinear =
        buscaLinear(vetor, n, codigo, comparacoesLinear);

    int posicaoBinaria =
        buscaBinaria(vetor, n, codigo, comparacoesBinaria);

    cout << "\n==============================\n";
    cout << "Codigo pesquisado: " << codigo << endl;

    cout << "\n--- Busca Linear ---\n";

    if (posicaoLinear != -1) {
        cout << "Encontrado: sim\n";
        cout << "Posicao: " << posicaoLinear << endl;
    } else {
        cout << "Encontrado: nao\n";
    }

    cout << "Comparacoes: " << comparacoesLinear << endl;

    cout << "\n--- Busca Binaria ---\n";

    if (posicaoBinaria != -1) {
        cout << "Encontrado: sim\n";
        cout << "Posicao: " << posicaoBinaria << endl;
    } else {
        cout << "Encontrado: nao\n";
    }

    cout << "Comparacoes: " << comparacoesBinaria << endl;
}

int main() {

    const int n = 1000;

    int vetor[n];

    // Criando vetor ordenado de 0 até 999
    for (int i = 0; i < n; i++) {
        vetor[i] = i;
    }

    int codigo;

    cout << "=== CENTRAL DE CONSULTAS ===\n";

    cout << "\nDigite um codigo para pesquisar: ";
    cin >> codigo;

    realizarBusca(vetor, n, codigo);

    cout << "\nAgora sera realizado um teste com "
            "um codigo inexistente.\n";

    realizarBusca(vetor, n, 1000);

    return 0;
}
