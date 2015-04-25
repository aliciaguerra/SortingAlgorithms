#Quicksort
- Quicksort is an efficient sorting algorithm.
- When implemented well, it can be two or three times faster than its main competitors, mergesort and heapsort.
- Quicksort is a comparison sort, meaning that it can sort items of any type for which a "less-than" relation is defined.
- In efficient implementations, it is not a stable sort, meaning that the relative order of equal sort items is not preserved.

#Algorithm
Quicksort is a divide and conquer algorithm. Quicksort first divides a large array into two larger sub-arrays: the low elements
and the higher elements. Quicksort can then recursively sort the subarrays. <br><br>
The steps are: <br>
1. Pick an element, called a pivot, from the array. <br>
2. Reorder the array so all the elements with values less than the pivot come before the pivot, while all elements with values
greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final
position. This is called the partition operation. <br>
3. Recursively apply the above steps to the sub-array of elements with smaller values and seperately to the sub-array of
elements with greater values. <br><br>

The base case of the recursion is arrays of size zero or one, which never need to be sorted. In pseudocode, a quicksort that 
the sorts elements from low to high (inclusive) of array A can be expressed compactly as:
```
quicksort(A, low, high):
if low<high:
p:= partition(A, low, high)
quicksort(A, low, p-1)
quicksort(A, p+1, high)
```
Sorting the entire array is accomplished by calling quicksort(A, 1, length(A)). The partition operation is step 2 from the
algorithm description above:
```
//low is the index of the leftmost element of ther subarray
//high is the index of the rightmost element of the subarray
partition(A, low, high)
pivotIndex := choosePivot(A, low, high)
pivotValue := A[pivotIndex]
//put the chosen pivot at A[high]
swap A[pivotIndex] and A[high]
storeIndex:= low

```
