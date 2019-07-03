## Data Structures Notes - Udemy


- An Abstract data type : is an abstraction of a data structure which provides only the interface to which a data structure must adhere to. Like you want to get from one place to another is an abstract data type, however the means of getting there is defined by using a data structure and programming language. ADT does not have details on how it is supposed to be implemented.


Example : List is a ADT and Dynamic array and Linked List is a data structure.


- time/space Complexity : 
  - how much *time* algo need?
  - how much *space* does algo need?
  - Big - O Notation - Only cares about the worst case like what happens when input is arbitarly large. *n* is the input size coming into the algorithm.
    - O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set
    - O($N$) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.
    - O($N^2$) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. Like a for loop inside a for loop
    - O($2^N$) denotes an algorithm whose growth doubles with each additon to the input data set. Exponential
    - O($log N$) produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase. Example: Binary Search Tree
