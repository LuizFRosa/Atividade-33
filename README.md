# Atividade-33

#include <stdio.h>
#include <stdlib.h>

// Função para realizar a ordenação por inserção
void insertionSort(int arr[], int n) {
    int i, key, j;
    for (i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;

        // Move os elementos de arr[0..i-1] que são maiores que key para uma posição à frente
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

// Função para imprimir o array
void printArray(int arr[], int size) {
    int i;
    for (i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int *arr;
    int n, i;

    // Solicita o tamanho do array ao usuário
    printf("Digite o número de elementos no array: ");
    scanf("%d", &n);

    // Aloca memória para o array
    arr = (int *)malloc(n * sizeof(int));

    if (arr == NULL) {
        printf("Falha na alocação de memória.\n");
        return 1;
    }

    // Solicita os elementos do array ao usuário
    printf("Digite os %d elementos do array:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Array original: ");
    printArray(arr, n);

    insertionSort(arr, n);

    printf("Array ordenado: ");
    printArray(arr, n);

    // Libera a memória alocada
    free(arr);

    return 0;
}
