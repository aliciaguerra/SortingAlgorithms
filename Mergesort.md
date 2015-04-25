#Merge Sort
Merge sort is an O(nlogn) comparison-based sorting algorithm. Most implementations produce a stable sort, which means
that the implementation preserves the input order of equal elements in the sorted output. Mergesort is a divide and conquer
algorithm.

#Algorithm
Conceptually, a merge sort algorithm works as follows: <br>
1. Divide the unsorted list into n sublists, each containing 1 element (a list of 1 element is considered sorted). <br>
2.Repeatedly merge sublists to produce new sorted sublists until there is only 1 sublist remaining. This will be the sorted 
list.

Top-Down Implementation
Example C like code using indices for top-down merge sort algorithm that recursively splits the list into sublists until the 
sublist size is 1, then merges those sublists to produce a sorted list. The copy back step could be avoided if the recursion
alternated between two functions so that the direction of the merge correpsonds with the level of recursion.
```
TopDownMergeSort(A[], B[], n){
TopDownSplitMerge(A, 0, n, B);
}
//iBegin is Inclusive; iEnd is Exclusive (A[iEnd] is not in the set)
TopDownSplitMerge(A[], iBegin, iEnd, B[])
{
if(iEnd-iBegin<2)    //if runSize==1
return;              //consider it sorted
}
//recursively split runs into two halves until run size==1,
//then merge them and return back up the call chain
iMiddle=(iEnd+iBegin)/2;                        //iMiddle=mid point
TopDownSplitMerge(A, iBegin, iMiddle, B);       //split/merge left half
TopDownSplitMerge(A, iMiddle, iEnd, B);         //split/merge right half
TopDownMerge(A, iBegin, iMiddle, iEnd, B);      //merge the two half runs
CopyArray(B, iBegin, iEnd, A);                  //copy the merged runs back to A

```
