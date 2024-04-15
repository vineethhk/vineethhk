# Musings on Insertion Sort
## Objective
Below are a few ways in which one can implement an insertion sort. Objective of the exercise was to try and see how each of the implementation would perform in terms of space and time.
### Implementation I: Nested for loops
Utilizing nested for loops, we can traverse the list of elements in an array and perform pairwise comparison between the adjacent elements of an array.
```
def sort_nested(array):
    for i in range(1,len(array)):
        for j in range(i,0,-1):
            if array[j-1] > array[j]:
                array[j-1],array[j] = array[j],array[j-1]
    return array
```
Finding time of execution using the below code snippet:
```
import time
import random
a = list(range(0,35000))
random.shuffle(a)
start_time = time.time()
a1 = sort_nested(a)
print("--- %s seconds ---" % (time.time() - start_time))
```
Time taken is as indicated below:
```
--- 89.59043622016907 seconds ---
```
### Implementation II: Recursion
Using 2 recursive functions, we can implement a similar insertion sort. First recursive function is as indicated below:
```
def insertion_sort(array,key):
    if array[key-1] > array[key] and key >0 :
        array[key-1],array[key] = array[key],array[key-1]
        return insertion_sort(array,key-1)
```
The above recursive function compares adjacent elements and makes a swap wherever required. The next recursive function increments the key one at a time through the full list of integers. For every integer it finds in the input list, it will perform the required operation by using the function mentioned above. 
```
def sort_recursion(array,key=1):
    if key < len(array) and key >= 1:
        insertion_sort(array,key)
        return sort_recursion(array,key+1)
    else:
        return array
```
Finding time of execution using the below code snippet:
```
import time
import random
import sys
sys.setrecursionlimit(75000)
a = list(range(0,35000))
random.shuffle(a)
start_time = time.time()
a1 = sort_recursion(a)
print("--- %s seconds ---" % (time.time() - start_time))
```
Please note that the maximum depth by default in Python is 1000 for recursion. Therefore, it required the recursion depth to be increased. Time taken is as indicated below:
```
--- 111.46455335617065 seconds ---
```
While the runtimes itself could vary, we can expect the recursion implementation to take longer.
