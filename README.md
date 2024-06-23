# BreadcrumbsStack Implementation Using Linked List
Overview
The BreadcrumbsStack is a data structure that allows tracking the history of visited paths or pages in a manner similar to web browser history, but specifically for use cases where you might need to backtrack to previous states, such as in a file system navigator or a maze solver. This implementation of the BreadcrumbsStack uses a linked list to store the stack elements.

Features
Push Operation: Add a new element (breadcrumb) to the top of the stack.
Pop Operation: Remove and return the element (breadcrumb) from the top of the stack.
Peek Operation: Return the element at the top of the stack without removing it.
IsEmpty Operation: Check if the stack is empty.
Linked List-Based Stack
Why Linked List?
Using a linked list for stack implementation provides the following benefits:

Dynamic Size: The stack can grow and shrink as needed without needing to resize arrays or pre-allocate memory.
Memory Efficient: Only the necessary amount of memory is used, as each element is allocated individually.
Simpler Implementation: No need for managing array bounds and resizing logic.
Structure
The linked list-based stack consists of two main components:

Node: A class representing each element in the stack.
BreadcrumbsStack: A class encapsulating the stack operations.
Node Class
Each node in the linked list contains:

Data: The value or breadcrumb stored in the node.
Next: A reference to the next node in the stack.
BreadcrumbsStack Class
This class provides methods to interact with the stack:
Implementation
Here is the implementation of the BreadcrumbsStack using a linked list in Python:

python
Copy code
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class BreadcrumbsStack:
    def __init__(self):
        self.top = None

    def push(self, data):
        new_node = Node(data)
        new_node.next = self.top
        self.top = new_node

    def pop(self):
        if self.is_empty():
            raise IndexError("Pop from empty stack")
        data = self.top.data
        self.top = self.top.next
        return data

    def peek(self):
        if self.is_empty():
            raise IndexError("Peek from empty stack")
        return self.top.data

    def is_empty(self):
        return self.top is None
Usage Example
Here is an example of how to use the BreadcrumbsStack class:

python
Copy code
# Create a new BreadcrumbsStack
breadcrumbs = BreadcrumbsStack()

# Push some breadcrumbs onto the stack
breadcrumbs.push("Home")
breadcrumbs.push("Products")
breadcrumbs.push("Electronics")
breadcrumbs.push("Laptops")

# Peek at the top breadcrumb
print("Top breadcrumb:", breadcrumbs.peek())  # Output: Laptops

# Pop breadcrumbs from the stack
print("Popped breadcrumb:", breadcrumbs.pop())  # Output: Laptops
print("Popped breadcrumb:", breadcrumbs.pop())  # Output: Electronics

# Check if the stack is empty
print("Is the stack empty?", breadcrumbs.is_empty())  # Output: False

# Peek at the top breadcrumb again
print("Top breadcrumb:", breadcrumbs.peek())  # Output: Products


Push: Adds a new node to the top of the stack.
Pop: Removes the node from the top of the stack and returns its data.
Peek: Returns the data of the node at the top of the stack without removing it.
IsEmpty: Checks if the stack is empty.
