## Data Structures Notes - Udemy

### Section 1:

#### An Abstract data type : 

ADT is an abstraction of a data structure which provides only the interface to which a data structure must adhere to. For example, you would want to get from one place to another this is an abstract data type, however the means of getting there is defined by using a data structure and programming language. ADT does not have details on how it is supposed to be implemented.

Example : List is a ADT and Dynamic array and Linked List is a data structure.


#### time/space Complexity : 

Questions mostly computer scientists end up asking themselves:

  - how much *time* algo need?
  - how much *space* does algo need?

#### The Big-O Notation:
  
  - Big - O Notation - Only cares about the worst case like what happens when input is arbitarly large. *n* is the input size coming into the algorithm.
    - O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set
    - O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.
    - O(N^2) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. Like a for loop inside a for loop
    - O(2^N) denotes an algorithm whose growth doubles with each additon to the input data set. Exponential. Exa: Finding all subsets of a set.
    - O(log N) produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase. Example: Binary Search Tree


### Section 2

#### Static Arrays

A static array is a fixed length container containing n elements that can be referenced by a number from range [0, n-1]. All the adresses for elements in an array are continous and adjecent. indexes start from * 0 *
- To access elements in an array for static and dynamic is constant O(1).
- Searching takes linear time to search through the array O(n).
- Appending to a dynamic array is constant time.
- Deletion is also linear.

#### Dynamic Arrays

Dynamic array can grow and shring in size. A.add(-7), A.remove(-7).
Dynamic arrays are implemented using a static array with an initial capacity. If adding element will exceed  the capacity, then create a new static array with **_twice_** the capacity and copy the original elements into it.
We grow the array exponentially so that the cost of inserting as well as resizing becomes negligible.

### Section 3

#### Linked List

A linked list is a sequential list of nodes that hold data which point to other nodes also containing data. Every pointer points to the next node and the last one points to null. They are used in implementing Queues and Stacks.

### Section 4 (stacks and queues)
- Stacks 
  - uses LIFO (last in first out) method to access and add data elements.
  - Same end is used to insert and delete elements.
  - uses a single pointer
- Queues 
  - uses FIFO (First in first out) method to access and add data elements.
  - One end is used for insertion, i.e., rear end and another end is used for deletion of elements, i.e., front end.
  - uses 2 pointers (min)
  
### Section 5 (Priority Queues and Heap)
  
#### Priority Queue
is an extension of queue with following properties.
- Every item has a priority associated with it.
- An element with high priority is dequeued before an element with low priority.
- If two elements have the same priority, they are served according to their order in the queue.
- The priority part removal and addition is taken care of using a **_heap_**
- used for Dijkstra's Shortest Path alorithm, dynamically fetch the 'next best' or 'next worst' element.
  
 #### Heap
 
 Heap is a tree based DS that satisfies the _heap invariant_ (also called heap property): If A is a parent node of B then A is ordered with respect to B for all nodes A, B in the heap. This means value of the parent node is always greater than or equal to the value of the child node (**max heaps**) for all nodes or the other way around (**min heaps**). These are mostly binary trees but without a cycle.
 
 ```python
 # Python program for implementation of heap Sort 

# To heapify subtree rooted at index i. 
# n is size of heap 
def heapify(arr, n, i): 
	largest = i # Initialize largest as root 
	l = 2 * i + 1	 # left = 2*i + 1 
	r = 2 * i + 2	 # right = 2*i + 2 

	# See if left child of root exists and is 
	# greater than root 
	if l < n and arr[i] < arr[l]: 
		largest = l 

	# See if right child of root exists and is 
	# greater than root 
	if r < n and arr[largest] < arr[r]: 
		largest = r 

	# Change root, if needed 
	if largest != i: 
		arr[i],arr[largest] = arr[largest],arr[i] # swap 

		# Heapify the root. 
		heapify(arr, n, largest) 

# The main function to sort an array of given size 
def heapSort(arr): 
	n = len(arr) 

	# Build a maxheap. 
	for i in range(n, -1, -1): 
		heapify(arr, n, i) 

	# One by one extract elements 
	for i in range(n-1, 0, -1): 
		arr[i], arr[0] = arr[0], arr[i] # swap 
		heapify(arr, i, 0) 

# Driver code to test above 
arr = [ 12, 11, 13, 5, 6, 7] 
heapSort(arr) 
n = len(arr) 
print ("Sorted array is") 
for i in range(n): 
	print ("%d" %arr[i]), 

 ```

#### Turning Min PQ into Max PQ

- change the comparison equation
- negate the numbers.

### Section 6 - Union find

#### Union Find

Data structure that keeps track of elements which are split into one or more dishoint sets. 2 primary operations _find_ and _union_. Its used in Kruskal's minimum spanning tree algorithm, Network connection, image processing.

- Find Operation : Find which component a particular element belongs to, find the root of that component by following the parent nodes until a self lrrop is reached.

- Union Operation : Unify two elements find which are the root nodes of each component and if the root nodes are different make one of the root nodes be the parent of the other.


```python
class UF:
    """An implementation of union find data structure.
    It uses weighted quick union by rank with path compression.
    """

    def __init__(self, N):
        """Initialize an empty union find object with N items.

        Args:
            N: Number of items in the union find object.
        """

        self._id = list(range(N))
        self._count = N
        self._rank = [0] * N

[docs]
    def find(self, p):
        """Find the set identifier for the item p."""

        id = self._id
        while p != id[p]:
            p = id[p] = id[id[p]]   # Path compression using halving.
        return p

[docs]
    def count(self):
        """Return the number of items."""

        return self._count

[docs]
    def connected(self, p, q):
        """Check if the items p and q are on the same set or not."""

        return self.find(p) == self.find(q)

[docs]
    def union(self, p, q):
        """Combine sets containing p and q into a single set."""

        id = self._id
        rank = self._rank

        i = self.find(p)
        j = self.find(q)
        if i == j:
            return

        self._count -= 1
        if rank[i] < rank[j]:
            id[i] = j
        elif rank[i] > rank[j]:
            id[j] = i
        else:
            id[j] = i
            rank[i] += 1

    def __str__(self):
        """String representation of the union find object."""
        return " ".join([str(x) for x in self._id])

    def __repr__(self):
        """Representation of the union find object."""
        return "UF(" + str(self) + ")"
```
#### Path compression

Path compression helps the union find to boast its complexity in a(1). It directly connects a node to its root node so that during the union operation, it does not have to traverse through the tree to find the root. Makes the lookup very easy and efficient.

**Union Find** is the underlying data structure that allows us to do the Kuskal's Minimum Spanning Tree.

#### Kruskal's Algorithm

**Minimum Spanning Tree** is a subset of the edges which connect all verives in the graph with the minimal total edge cost.
1. Sort edges by ascending edge weight.
2. Walk through the sorted edges and look at the two nodes the edge belongs to, if the nodes are already unified we dont include this edge, (Not to create a circle) otherwise we include it and unify the nodes.
3. The algorithm terminates when every edge has been processed or all the vertices have been unified.

### Section 7 (Binary Trees and Binary Search Trees)

- A tree is an undirected graph which is connected and acyclic. For any 2 vertices we have one edge. A tree could be rooted or unrooted. A system path is a tree with the parent being the root directory (Output of cd ..) and the child the folders in the root directory.

#### Binary Tree

Simplt put its a trees with atmost 2 children.

#### Binary Search Tree

A binary search tree is a rooted binary tree, whose internal nodes each store a key (and optionally, an associated value) and each have two distinguished sub-trees, commonly denoted left and right. **The tree additionally satisfies the binary search property, which states that the key in each node _must be greater than or equal to any key stored in the left sub-tree_, and less than or equal to any key stored in the right sub-tree**

Complexities for Insertion, delete, Remmove, Search in O(log(n)) which is very efficient.

```python
class Node:
    def __init__(self, val):
        self.val = val
        self.leftChild = None
        self.rightChild = None
    
    def get(self):
        return self.val
    
    def set(self, val):
        self.val = val
        
    def getChildren(self):
        children = []
        if(self.leftChild != None):
            children.append(self.leftChild)
        if(self.rightChild != None):
            children.append(self.rightChild)
        return children
        
class BST:
    def __init__(self):
        self.root = None

    def setRoot(self, val):
        self.root = Node(val)

    def insert(self, val):
        if(self.root is None):
            self.setRoot(val)
        else:
            self.insertNode(self.root, val)

    def insertNode(self, currentNode, val):
        if(val <= currentNode.val):
            if(currentNode.leftChild):
                self.insertNode(currentNode.leftChild, val)
            else:
                currentNode.leftChild = Node(val)
        elif(val > currentNode.val):
            if(currentNode.rightChild):
                self.insertNode(currentNode.rightChild, val)
            else:
                currentNode.rightChild = Node(val)

    def find(self, val):
        return self.findNode(self.root, val)

    def findNode(self, currentNode, val):
        if(currentNode is None):
            return False
        elif(val == currentNode.val):
            return True
        elif(val < currentNode.val):
            return self.findNode(currentNode.leftChild, val)
        else:
return self.findNode(currentNode.rightChild, val)
```

#### Traversing a Binary Search tree

1. [Tree Traversal] (https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)

### Section 8 (Hash Table)

"_One data structure to rule them all_".

A hash table (HT) is a data structure that provides a mapping from keys to values using a technique called hashing. Its similar to a dictionary datastructure. The only condition is that the keys used should be hashable. Hash table is a fancy word for an aarray with index as a hash funciton output.

- _Hash collision_ : when 2 of the keys have the same hash function output we use 2 most common methods to correct it.

	- Seperate chaining: deals with hash collisions by maintaining a data structure (usually a linked list) to hold all the different values which hashed to a particular value.
	
	- Open Addressing : deals with collsioins by finding another place within the hash table for the object to go by offsetting it from the position to which it hashed to.
	
complexity on average O(1) " constant time".

#### Hash Function

It is a function that maps a key 'x' to a whole number in a fixed range.
- If H(x) = H(y) then objects x and y might be equal, but else they are definitely not equal

#### Double Hashing

DH is a probing method which probes according to a constant multiple of another hash function, P(k, x) = x * H2(k), where H2(k) is a second hash function. H2(k) must hash the same type of keys as H1(K)
```python.
# create a hash function that ouputs a value (0, 6) given a persons age and name

def hash function(Person):
	hash = person.age
	hash = hash + len(person.name)
	return hash%6
```
### Section 9 (Fenwick Tree or Binary indexed tree)

A Fenwick Tree is a data structure that supports sum range queries as well as setting values in a static array and getting the value of the prefix sum up some index efficiently.
- each cell is responsible for other cells as well.
	- the position of the least significant bit determines the range of responsiblity that cell has to the cells below itself.
