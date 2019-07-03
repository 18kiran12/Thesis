## Data Structures Notes - Udemy

### Section 1:

#### An Abstract data type : 

ADT is an abstraction of a data structure which provides only the interface to which a data structure must adhere to. Like you want to get from one place to another is an abstract data type, however the means of getting there is defined by using a data structure and programming language. ADT does not have details on how it is supposed to be implemented.

Example : List is a ADT and Dynamic array and Linked List is a data structure.


#### time/space Complexity : 

  - how much *time* algo need?
  - how much *space* does algo need?
  
  
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
  



