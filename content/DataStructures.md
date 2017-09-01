# Data Structures
## Arrays
- Fixed Size collection, cannot increase and decrease as per program;
- Constant Access Time given the index of item
- Space Efficient as consists of just Data
- Easy Iteration because of memory locality
- Java array max length is `Integer.MAX_VALUE = 2^31-1` (but actually be bit shorter)

## Linked List
- Single Linked List
- Double Linked List
- Supports insert, delete and search
- Should not overflow as there is not size limit (should be considering memory available)
- Easy Insertion and Deletion as no need to shift elements like in Arrays
- Takes extra memory for pointers
- Not efficient for random access to items

## Stacks & Queues
- Stack is Last In First Out (LIFO) data structure
- Supports `push()`, `peek()` and `pop()`
- LIFO is very helpful in recursive algorithms

- Queue is First In First Out (FIFO) data structure
- Supports enqueue and dequeue (`offer()`, and `poll()`)
- Used for searches in graph, specially Breadth First Search

- Stacks and Queues can be implemented using dynamic arrays or Linked Lists
- If capacity or max size is known, static arrays can also be used for implementing Stacks and Queues


## Maps or Dictionary
- Enables `key` based data Access
- Supports insert, delete, search
- Implemntation includes `Hashtables`, `Binary Search Trees`

## Hash Tables


## Binary Search Trees



## Priority Queues

## Graphs
