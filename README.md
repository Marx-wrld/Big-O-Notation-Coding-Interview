# Big-O-Notation-Coding-Interview
Repo containing Big O notations, coding interview solutions. 

### Qn 1
- Big O(1) - For a constant time.
```
# Array
nums = [1, 2, 3]
nums.append(4)    # push to end
nums.pop()        # pop from end
nums[0]           # lookup
nums[1]
nums[2]

# HashMap / Set
hashMap = {}
hashMap["key"] = 10     # insert
print("key" in hashMap) # lookup
print(hashMap["key"])   # lookup
hashMap.pop("key")      # remove
````
### Qn 2
- Big O(n) - For a linear time where growth is proportional.
```
nums = [1, 2, 3]
sum(nums)           # sum of array
for n in nums:      # looping
    print(n)

nums.insert(1, 100) # insert middle
nums.remove(100)    # remove middle
print(100 in nums)  # search

import heapq
heapq.heapify(nums) # build heap

# sometimes even nested loops can be O(n)
# (e.g. monotonic stack or sliding window)
```
### Qn 3
- Big O(n^2) - Here performance is proportional to the square of the size of the input elements.
```
# Traverse a square grid
nums = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
for i in range(len(nums)):
    for j in range(len(nums[i])): 
        print(nums[i][j])


# Get every pair of elements in array
nums = [1, 2, 3]
for i in range(len(nums)):
    for j in range(i + 1, len(nums)):
        print(nums[i], nums[j])

# Insertion sort (insert in middle n times -> n^2)
```
### Qn 4
- Big O(n*m) - For a 2 dimensional matrix e.g - n number of rows and m number of columns.
```
# Get every pair of elements from two arrays
nums1, nums2 = [1, 2, 3], [4, 5]
for i in range(len(nums1)):
    for j in range(len(nums2)):
        print(nums1[i], nums2[j])

# Traverse rectangle grid
nums = [[1, 2, 3], [4, 5, 6]]
for i in range(len(nums)):
    for j in range(len(nums[i])):
        print(nums[i][j])
```
### Qn 5
- Big O(n^3) - Where algorithm runs in a cubic time
```
# Get every triplet of elements in array
nums = [1, 2, 3]
for i in range(len(nums)):
    for j in range(i + 1, len(nums)):
        for k in range(j + 1, len(nums)):
            print(nums[i], nums[j], nums[k])
 ```
### Qn 6
- Big O(logn) - As the input size grows, the number of operations grows, but very slowly. *Efficient than O(n)
```
# Binary search
nums = [1, 2, 3, 4, 5]
target = 6
l, r = 0, len(nums) - 1
while l <= r:
    m = (l + r) // 2
    if target < nums[m]:
        r = m - 1
    elif target > nums[m]:
        l = m + 1
    else:
        print(m)
        break

# Binary Search on BST
def search(root, target):
    if not root:
        return False
    if target < root.val:
        return search(root.left, target)
    elif target > root.val:
        return search(root.right, target)
    else: 
        return True

# Heap Push and Pop
import heapq
minHeap = []
heapq.heappush(minHeap, 5)
heapq.heappop(minHeap)
```
### Qn 7
- Big O(nlogn) - Implies that log n operations will occur for n times.
```
# HeapSort
import heapq
nums = [1, 2, 3, 4, 5]
heapq.heapify(nums)     # O(n)
while nums:
    heapq.heappop(nums) # O(logn)

# MergeSort (and most built-in sorting functions)
```
### Qn 8
- Big O(2^n) - Here the algorithm doubles with each addition to the input data set.
```
# Recursion, tree height n, two branches
def recursion(i, nums):
    if i == len(nums):
        return 0
    branch1 = recursion(i + 1, nums)
    branch2 = recursion(i + 2, nums)
```
### Qn 9
- Big O(c^n) - Here the algorithm might double, triple, quadruple e.t.c with addtion to the input data set. It can be (2^n), (3^n), (10^n) etc. 
```
# c branches, where c is sometimes n.
def recursion(i, nums, c):
    if i == len(nums):
        return 0
    
    for j in range(i, i + c):
        branch = recursion(j + 1, nums)
 ```
### Qn 10
- Big O(sqrt(n)) - Algortithm here requires O(n^1/2) evaluations where the size of input is n.
```
# Get all factors of n
import math
n = 12
factors = set()
for i in range(1, int(math.sqrt(n)) + 1):
    if n % i == 0:
        factors.add(i)
        factors.add(n // i)
```
### Qn 11
- Big O(n!) - Here the algorithm must perform n! calculations.

 ##### E.g- The Travelling Salesman Problem - *Given a set of cities and the distance between every pair of cities as an adjacency matrix, the problem is to find the shortest possible route that visits every city exactly once and returns to the starting point.

```
# Mostly used in Permutations & Graph problems


from sys import maxsize
from itertools import permutations
V = 4

def travellingSalesmanProblem(graph, s):
	vertex = []
	for i in range(V):
		if i != s:
			vertex.append(i)

	min_path = maxsize
	next_permutation=permutations(vertex)
	for i in next_permutation:
		current_pathweight = 0
		k = s
		for j in i:
			current_pathweight += graph[k][j]
			k = j
		current_pathweight += graph[k][s]
		min_path = min(min_path, current_pathweight)
		
	return min_path


if __name__ == "__main__":
	graph = [[0, 10, 15, 20], [10, 0, 35, 25],
			[15, 35, 0, 30], [20, 25, 30, 0]]
	s = 0
	print(travellingSalesmanProblem(graph, s))
 ```
![Interview](https://github.com/Marx-wrld/Big-O-Notation-Coding-Interview/assets/105711066/ddb1f69f-8a6f-468c-93fc-55db9ca01e19)
