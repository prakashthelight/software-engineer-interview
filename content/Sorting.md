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

## Merge Sort

```java
/**
 * sorts array using Merge Sort Algorithm - O(NlongN)
 * @param array
 */
public static void mergeSort(int[] array) {
	if (array == null) {
		return;
	}

	mergeSort(array, 0, array.length - 1);
}

/**
 * divide, sorts and merges arrays
 *
 * @param array
 * @param start
 * @param end
 */
private static void mergeSort(int[] array, int start, int end) {
	if (start >= end) {
		return;
	}

	int mid = (start + end) / 2;
	mergeSort(array, start, mid);
	mergeSort(array, mid + 1, end);
	merge(array, start, end);
}

/**
 * merges two sorted arrays
 *
 * @param array
 * @param start
 * @param end
 */
private static void merge(int[] array, int start, int end) {

	int[] temp = new int[end - start + 1];

	// create boundaries for both sub arrays to be merged
	int mid = (start + end) / 2;

	// temporary variables to be used in iteration
	int left = start;
	int right = mid + 1;

	// index for temp array
	int index = 0;

	// merge in temporary array
	while (left <= mid && right <= end) {
		if (array[left] <= array[right]) {
			temp[index] = array[left];
			left++;
			index++;
		} else {
			temp[index] = array[right];
			right++;
			index++;
		}
	}

	System.arraycopy(array, left, temp, index, mid - left + 1);
	System.arraycopy(array, right, temp, index, end - right + 1);

	// override back in original array
	System.arraycopy(temp, 0, array, start, temp.length);
}
```
