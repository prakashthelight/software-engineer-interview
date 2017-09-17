# Sorting

## Bubble Sort

```java
/**
 * sorts array using bubble sort algorithm - O(n^2)
 *
 * @param array
 */
public static void bubbleSort(int[] array) {
	if (array == null)
		return;

	int n = array.length;

	// loop 0 -> n - 1
	for (int i = 0; i < n - 1; i++) {
		// loop 0 -> n - 1 - i
		for (int j = 0; j < n - 1 - i; j++) {
			if (array[j] > array[j + 1]) {
				int temp = array[j];
				array[j] = array[j + 1];
				array[j + 1] = temp;
			}
		}
	}
}
```

## Selection Sort
```java
/**
 * sorts array using selection sort algorithm - O(n^2)
 *
 * @param array
 */
public static void selectionSort(int[] array) {
	if (array == null)
		return;

	int n = array.length;

	// loop 0 -> n - 1
	for (int i = 0; i < n - 1; i++) {
		// loop i + 1 -> n
		for (int j = i + 1; j < n; j++) {
			if (array[i] > array[j]) {
				int temp = array[i];
				array[i] = array[j];
				array[j] = temp;
			}
		}
	}
}
```
