# Heap_Sort
O Heap Sort é um algoritmo de ordenação baseado na estrutura de dados Heap. Ele transforma a lista em um Heap Máximo, onde o maior elemento fica na raiz, e o remove sucessivamente, reconstruindo o heap até ordenar a lista. Tem complexidade O(n log n) no pior caso, sendo eficiente e usado em grandes volumes de dados.
import java.util.Arrays;

public class HeapSort {

   public static void main(String[] args) {
        int[] array = {4, 10, 3, 55, 17, 75, 93, 26, 89, 66};
        System.out.println("Array antes da ordenação: " + Arrays.toString(array));

        heapSort(array);

        System.out.println("Array depois da ordenação: " + Arrays.toString(array));
    }
    public static void heapSort(int[] array) {
        int n = array.length;
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(array, n, i);
        }
        for (int i = n - 1; i >= 0; i--) {
            int temp = array[0];
            array[0] = array[i];
            array[i] = temp;
            heapify(array, i, 0);
            System.out.println("Passo " + (n - i) + ": " + Arrays.toString(array));
        }
    }
    public static void heapify(int[] array, int n, int i) {
        int largest = i; 
        int leftChild = 2 * i + 1; 
        int rightChild = 2 * i + 2; 
        if (leftChild < n && array[leftChild] > array[largest]) {
            largest = leftChild;
        }
        if (rightChild < n && array[rightChild] > array[largest]) {
            largest = rightChild;
        }
        if (largest != i) {
            int swap = array[i];
            array[i] = array[largest];
            array[largest] = swap;
            heapify(array, n, largest);
        }
    }
}
