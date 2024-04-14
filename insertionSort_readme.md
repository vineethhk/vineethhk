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
