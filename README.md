#include <stdio.h>

#define MAX_SIZE 100

void insertElement(int arr[], int *size) {
    if (*size >= MAX_SIZE) {
        printf("Array is full! Cannot insert more elements.\n");
        return;
    }
    int element, position;
    printf("Enter the element to insert: ");
    scanf("%d", &element);
    printf("Enter the position (0-based index): ");
    scanf("%d", &position);
    
    if (position < 0 || position > *size) {
        printf("Invalid position!\n");
        return;
    }
    
    for (int i = *size; i > position; i--) {
        arr[i] = arr[i - 1];
    }
    arr[position] = element;
    (*size)++;
    printf("Element inserted successfully.\n");
}

void retrieveElement(int arr[], int size) {
    int position;
    printf("Enter the position to retrieve (0-based index): ");
    scanf("%d", &position);
    
    if (position < 0 || position >= size) {
        printf("Invalid position!\n");
        return;
    }
    
    printf("Element at position %d is %d\n", position, arr[position]);
}

void displayArray(int arr[], int size) {
    printf("Current Array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[MAX_SIZE], size = 0, choice;
    
    while (1) {
        printf("\nChoose an operation:\n");
        printf("1. Insert element\n");
        printf("2. Retrieve element\n");
        printf("3. Display array\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1:
                insertElement(arr, &size);
                break;
            case 2:
                retrieveElement(arr, size);
                break;
            case 3:
                displayArray(arr, size);
                break;
            case 4:
                printf("Exiting program.\n");
                return 0;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    }
    return 0;
}
