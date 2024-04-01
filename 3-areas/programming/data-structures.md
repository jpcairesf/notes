+++
date = 2024-03-09T07:50:00-00:00
+++

# Data Structures

A very simplified note to cover the most important data structures with examples in python, operations time complexity and trade offs.

## Arrays

A contiguous memory block that stores elements of the same data type. The memory address of the first element in the array is the base address and any other element's address can be calculated using the base address and the size of each element.

```python
array = []
array.append(1)
array.append(3)
print(array[1]) # 3
array.append(2)
print(array.remove(3)) # 3
print(array.index(2)) # 1
```

#### Operations

- **Access by index**: `O(1)` by calculating the position
- **Access by value**: `O(n)` by traversal
- **Write in the beginning**: `O(n)`, requires shifting elements
- **Write in the end**: `O(1)`, no shifting required

#### Pros And Cons

**Pros**: Direct access using indexes, contiguous storage minimizes memory overhead, easy to sort.
**Cons**: Fixed (limited) size, inefficient writing due to shifting, unfilled memory keep allocated.

## Linked List

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class LinkedList:
    def __init__(self):
        self.head = None
# implements the following methods:
#    def append(self, val):
#    def remove(self, val):
#    def display(self):

linked_list = LinkedList()
linked_list.append(1)
linked_list.append(2)
linked_list.append(3)
linked_list.display()  # Output: 1 -> 2 -> 3 -> None
linked_list.remove(2)
linked_list.display()  # Output: 1 -> 3 -> None
```

A linear data structure where elements (nodes) are connected through pointers. Doesn't require contiguous memory locations and each node contains a reference to the next one, allowing to be placed anywhere in the memory.

#### Operations

- **Access by index**: `O(n)` by traversal
- **Access by value**: `O(n)` by traversal
- **Write in the beginning**: `O(1)` by pointing the new node to the old head
- **Write in the end**: `O(n)` by traversing and then pointing the last node to the new

#### Pros And Cons

**Pros**: Dynamic size, no waste of memory, more efficient writing operations.
**Cons**: Access always requires traversing, node requires extra memory for pointers, traversing have a higher constant factor compared to arrays.

## Stack

It's a LIFO-behaved data structure with a pointer to the last element for fast access. The stack itself is a pre-allocated region of memory with a fixed size, and the memory for individual function calls on the stack is dynamically managed. So the nature of the allocation depends on the type of stack and the context in which it's used.

```python
stack = []
stack.push(1)
stack.push(3)
print(stack.pop()) # 3
stack.push(2)
print(stack.pop()) # 2
print(stack.pop()) # 1
```

#### Operations

- **Access in the end**: `O(1)` by stack pointer
- **Write in the end**: `O(1)` by accessing via stack pointer and updating it

## Queue

It's a FIFO-behaved data structure that also can be pre-allocated or dynamically allocated depending on the type and context.

```python
from collections import deque

queue = deque()
deque.append(1)
deque.append(3)
print(queue.popleft()) # 1
deque.append(2)
print(queue.popleft()) # 3
print(queue.popleft()) # 2
```

#### Operations

- **Access in the beginning/end**: `O(1)` by pointers
- **Enqueue (insertion)**: `O(1)` by accessing via pointer and updating it
- **Dequeue (deletion)**: `O(1)` by accessing via pointer and updating it

## Hash Map

It's a key-value pair collection, where each key is unique. It provides operation efficiency (**all operations are** `O(1)`) through memory overhead. Uses hashing function to convert a key into an index and maintains an array where each index corresponds to a bucket that can hold multiple pairs.

## Set

It's a unordered collection of distinct elements. Internally uses hash maps and **all operations are** `O(1)`.

## Binary Tree

It's a hierarchical data structure in which each node has at most two children and the topmost node is called root.

#### Traversal

```python
def preorder_print(self, start, traversal):
    """Root->Left->Right"""
    if start:
        traversal += (str(start.value) + "-")
        traversal = self.preorder_print(start.left, traversal)
        traversal = self.preorder_print(start.right, traversal)
    return traversal
```

```python
def inorder_print(self, start, traversal):
    """Left->Root->Right"""
    if start:
        traversal = self.inorder_print(start.left, traversal)
        traversal += (str(start.value) + "-")
        traversal = self.inorder_print(start.right, traversal)
    return traversal
```

```python
def postorder_print(self, start, traversal):
    """Left->Right->Root"""
    if start:
        traversal = self.postorder_print(start.left, traversal)
        traversal = self.postorder_print(start.right, traversal)
        traversal += (str(start.value) + "-")
    return traversal
```

## Heap

Is a specialized tree-based data structure that satisfies the heap property (for max and min heaps) and **all operations are** `O(log n)`. It's used to implement priority queues, for heap sort and graph algorithms like Dijkstra's.

```python
import heapq

min_heap = []
heapq.heappush(min_heap, 4)
heapq.heappush(min_heap, 1)
heapq.heappush(min_heap, 3)
min_element = heapq.heappop(min_heap)
print(min_element) # 1

max_heap = []
heapq.heappush(max_heap, -1)
heapq.heappush(max_heap, -4)
heapq.heappush(max_heap, -3)
max_element = -heapq.heappop(max_heap)
print(max_element) # 4
```
