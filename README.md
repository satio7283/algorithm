# algorithm final project
here i show the code that i used
## preproccesing
```C
#include <stdio.h>
#include <stdlib.h>
#include<math.h>
#include<time.h>
```
## initializing variables
```C
int size = 100000;
int array[100000];
```
## functions 
here is the functions (random_number, insertation_sort, print_array,swap,partition, quick_sort)
```C
void Random_number(int array[])
{
  int i;
  srand(time(NULL));
  for (i=0 ; i<size ; i++)
  {
       array[i] = rand() % 100000 + 1;

  }
}
// insertation sort
void insertion_sort(int arr[] , int size)
{
    int i, Comp, j;
    for (i = 1; i < size; i++) {
        Comp = arr[i];
        j = i - 1;
    while (j >= 0 && arr[j] > Comp) {
        arr[j + 1] = arr[j];
        j = j - 1;
        }
        arr[j + 1] = Comp;
    }
    printf("\nThe array is sorted using insertion sort in %u seconds\n", clock());
}
void printArray(int arr[], int size)
{
    int i;
    for (i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}
// swapping
void swap(int *i, int *j) {
  int temp = *i;
  *i = *j;
  *j = temp;
}

int partition(int array[], int low, int high) {

  int pivot = array[high];
  int i = (low - 1);
  int j;
  for (j = low; j < high; j++) {
    if (array[j] <= pivot) {
      i++;
      swap(&array[i], &array[j]);
    }
  }
  swap(&array[i + 1], &array[high]);
  return (i + 1);
}

void quickSort(int array[], int low, int high) {
  if (low < high) {
    int pi = partition(array, low, high);

    quickSort(array, low, pi - 1);
    quickSort(array, pi + 1, high);
  }
}

```
## Main Function
```C
int main()
{
  	int i;
	srand(time(NULL));
	for (i = 0; i < size; i++) {
		array[i] = rand() % 100000 + 1;
	}
	Random_number(array);

	printf("Array of 100000 random numbers is initialized\n");


	quickSort(array ,0, size - 1);
	printf("The array is sorted using quick sort in %u seconds", clock());

    insertion_sort(array, size);
    return 0;
}
```
