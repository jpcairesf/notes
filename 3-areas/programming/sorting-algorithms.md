+++
date = 2024-03-10T15:24:15-00:00
+++

First we have to keep some concepts in mind.

- **Inplace/Outplace**: use/don't use extra memory
- **Unstable/Stable**: position order change/don't change for repeated values

### Selection Sort

Divides the input list into a sorted and an unsorted region. Repeatedly selects the smallest element from the unsorted region and swaps it with the first element in the unsorted region.

- Inplace and unstable
- O(n<sup>2</sup>) time and O(1) space

```python
def selection_sort(arr):
    for i in range(len(arr)):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
```

### Insertion Sort

Builds a sorted portion of the list one element at a time. Iterates through the unsorted portion, selects an element, and inserts it into its correct position in the sorted portion.

- Inplace and stable
- O(n<sup>2</sup>) time and O(1) space

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
```

### Bubble Sort

Repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. Pass through the list is repeated until no swaps are needed, indicating the list is sorted.

- Inplace and stable
- O(n<sup>2</sup>) timg and O(1) space

```python
def bubble_sort(arr):
    for i in range(len(arr)):
        for j in range(0, len(arr)-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
```

### Merge Sort

Divides the list into two halves recursively until each sublist contains a single element. Merges the sorted sublists back together, comparing elements to arrange them in the correct order.

- Outplace and stable
- O(n log n) time and O(n) space

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left_half = arr[:mid]
    right_half = arr[mid:]

    left_half = merge_sort(left_half)
    right_half = merge_sort(right_half)
    return merge(left_half, right_half)

def merge(left, right):
    result = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])
    return result
```

### Quick Sort

Chooses a pivot element from the array and partitions the other elements into two subarrays according to whether they are less than or greater than the pivot. Recursively sorts the subarrays and concatenates them.

- Inplace and unstable
- Average: O(n log n) time and O(log n)\* space
- Worst case: O(n<sup>2</sup>) time and O(n)* space
  *because of recursion stack

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr

    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]

    return quick_sort(left) + middle + quick_sort(right)
```

### Heap Sort

Builds a binary heap (max heap) from the input array. Repeatedly extracts the maximum element (root of the heap) and rebuilds the heap until the array is sorted. Not used as the main sorting algorithms of programming languages because it is unstable.

- Inplace and unstable
- O(n log n) time and O(1) space

```python
import heapq

def heap_sort(arr):
    heapq.heapify(arr)
    return [heapq.heappop(arr) for _ in range(len(arr))]
```
