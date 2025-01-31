#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define SIZE 10

void printArray(int arr[], int size, const char* label) {
    printf("%s: ", label);
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

void selectionSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < size; j++) {
            if (arr[j] < arr[minIdx]) {
                minIdx = j;
            }
        }
        // Swap
        int temp = arr[minIdx];
        arr[minIdx] = arr[i];
        arr[i] = temp;
    }
}

void bubbleSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        for (int j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main() {
    int rawData[SIZE];
    int selectionSorted[SIZE];
    int bubbleSorted[SIZE];

    srand(time(NULL)); // Seed for random number generation

    // Generate random data
    for (int i = 0; i < SIZE; i++) {
        rawData[i] = (rand() % 90) + 10; // Two-digit random integers
    }

    // Copy rawData to other arrays
    for (int i = 0; i < SIZE; i++) {
        selectionSorted[i] = rawData[i];
        bubbleSorted[i] = rawData[i];
    }

    // Display Raw Data
    printArray(rawData, SIZE, "Raw Data");

    // Perform Selection Sort
    selectionSort(selectionSorted, SIZE);
    printArray(selectionSorted, SIZE, "Selection Sort");

    // Perform Bubble Sort
    bubbleSort(bubbleSorted, SIZE);
    printArray(bubbleSorted, SIZE, "Bubble Sort");

    return 0;
}
