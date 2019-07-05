### Insertion sort

- It is a stable algorithm.
- It is a well known online algorithm as it can sort a list as it receives. All other algorithms need all elements to be provided before applying the algorithms.
- The idea is to divide the array into 2 subsets- sorted and unsorted. In each iteration, insertion sort removes one element from the unsorted array and finds the location it belongs within tht esorted subset, and inserts it here.

### Slection Sort 

- Selection sort is unstable
- Complexity - O(n^2)
- But memory efficient than insertion sort.
- The idea is to divide the array into 2 subsets- sorted and unsorted. The algorithm proceeds by finding the smallest element in the unsorted sublist and swapping it with the leftmost unsorted element.


### Bubble Sort

- Stable
- Simple algorithm but slow and impractical for most problems.
- Useful when the list is already sorted.
- Each pass of bubble sort steps through the list to be sorted, compares each pair of adhacent items and swaps thim if they are in the woring order.

### Merge Sort

- Efficient sorting algorithm which produces a stable sort.
- Divide the unsorted array into n subarrays, each of size 1 (an array of size 1 is considered sorted).
- Repeatedly merge subarrays to produce new sorted subarrays until only 1 subarray is left which would be our sorted array.

### Quick sort

- When implemented well is 2, 3 times faster than merge sort and heap sort.
- Complexity O(n log(n))
- Pick an element, called a pivot, from the array (usually the leftmost or the rightmost element of the partition
- Reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position.
- Recursively apply the above steps to the sub-array of elements with smaller values than pivot and separately to the sub-array of elements with greater values than pivot.

