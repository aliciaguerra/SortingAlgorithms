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
//Compare remaining array elements against pivotValue=A[high]
for i from low to high-1, inclusive
if A[i] <= pivotValue
swap A[i] and A[storeIndex]
storeIndex := storeIndex+1
swap A[storeIndex] and A[high] //Move pivot to its final place
return storeIndex
```
This is the in-place partition algorithm. It partitions the portion of the array between indexes low and high, inclusively,
by moving all elements less than A[pivotIndex] before the pivot, and the greater elements after it. In the process it also
finds the final position for the pivot element, which it returns. It temporarily moves the pivot to the end of the subarray,
so that it does not get in the way. Because it only uses exchanges, the final list has the same elements as the original list.
Notice that an element may be echanged multiple times before reaching its final place. Also, in case of pivot duplicates in
the input array, they can be spread across the right subarray, in any order. This doesn't represent a partitioning failure,
as further sorting will reposition and finally "glue them together. <br>

Each recursive call to the combined quicksort function reduces the size of the array being sorted by at least one element,
since in each invocation the elemtn at storeIndex is placed in its final position. Therefore, this algorithm is guaranteed to
terminate recursion after at most n recursive calls. However, since partition reorders elements within a partition, this 
version of quicksort is not a stable sort.
