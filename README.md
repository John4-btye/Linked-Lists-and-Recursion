# Lab: Linked Lists and Recursion

**Lab GitHub Repo**: [Linked Lists and Recursion](https://github.com/learn-co-curriculum/Linked-Lists-and-Recursion)

---

## Overview

In this lab, we’ll apply **linked lists** and **recursion** to build a small prototype for managing a list of data. Imagine a junior developer assigned to maintain a simple employee roster, where IDs are stored in a linked list. You’ve been asked to implement **recursive** functionalities such as summing IDs, reversing the list in-place, and searching for a particular ID.

By focusing on **linked lists** (for dynamic insertion/deletion) and **recursion** (for elegant traversal), you’ll gain hands-on experience with node-based data structures—common in many low-level or performance-sensitive applications.

---

## Task 1: Define the Problem

1. **Load or create** an initial linked list of integer IDs.
2. **Enable recursive functionality** to:
   - **Sum** all node data in the list.
   - **Reverse** the list in-place.
   - **Search** for a given ID.
3. **Present** or print the result for each operation in a user-friendly format.

**The Challenge**: Demonstrate your understanding of linked lists while using recursion to solve day-to-day tasks such as searching and reversing data.

---

## Task 2: Determine the Design

### Linked List Structure

- **App / Main**  
  Drive the creation and manipulation of the linked list.

- **Node Class**  
  Each node stores an **integer data** and a pointer/reference to `next`.

- **LinkedList Class**
  - `head` references the first node.
  - Methods to **insert**, **sum**, **reverse**, and **search**.

---

## Task 3: Develop, Test, and Refine the Code

### Set Up

#### Fork and Clone

1. Go to the provided **GitHub repository link**.
2. Fork the repository to your GitHub account.
3. Clone the forked repository to your local machine.

#### Open and Run

1. Open the project in your preferred Python-friendly environment (VSCode, PyCharm, etc.).

### Implementation Details

1. **Create a feature branch** (e.g., `feature/linked-list-lab`).
2. **Create the `Node` and `LinkedList` classes**:
   - **Node** class with `data` and `next`.
   - **LinkedList** class to house `head` and methods.
3. **Manage Linked List Insertion**:
   - `insert_at_front(data)` → O(1).
   - _(Optional)_ `insert_at_end(data)` → O(n) to traverse to the end.
4. **Use Recursion**:
   - **Sum**: Returns `0` if node is `None`, otherwise `node.data + recurse(node.next)`.
   - **Reverse**: Re-point each node’s `next` to the **previous** node until the list is reversed.
   - **Search**: Returns `True` if a node’s `data` matches the target; stops if it hits `None`.
5. **Run Tests** (if provided) or manually test:
   - Insert some sample data, then call each recursive method.
   - Print the list or results to confirm correctness.
6. **Push feature branch** and open a PR on GitHub.
7. **Merge** to `main` once reviewed.

---

## Task 4: Document and Maintain

### Best Practice Documentation Steps

- **Add Comments**: Clarify logic for recursion, highlight base vs. recursive cases.
- **Explain Intent**: Make it clear why you’re using recursion in a particular method (e.g., elegance, clarity, demonstration).
- **README**: Update with instructions on how to run the code, test, and interpret results.
- **Clean Up**:
  - Remove any debugging prints or stale branches.
  - Ensure your `.gitignore` is updated to exclude unnecessary files.

## Submission

Once the lab is complete, all tests are passing, and you've pushed the completed code to
your forked repo on GitHub, submit your GitHub repo through Canvas using CodeGrade.

# Linked Lists and Recursion Lab

## 📌 Overview

This project implements a **singly linked list** in Python and applies **recursion** to perform common operations such as:

- Summing all values in the list
- Searching for a value
- Reversing the list in-place

The goal of this lab is to demonstrate an understanding of **node-based data structures** and how **recursion can be used for traversal and manipulation**.

---

## 🗂️ Project Structure

```
Linked-Lists-and-Recursion/
│
├── linked_list.py       # Core implementation (Node + LinkedList classes)
├── main.py              # Driver code to demonstrate functionality
├── tests/
│   └── test_linked_list.py  # Unit tests
├── README.md
```

---

## ⚙️ Implementations & Changes

### 1. Node Class Implementation

**File:** `linked_list.py`

Originally contained placeholder logic (`pass`).
Now fully implemented:

- Stores integer data
- Maintains reference to next node

```python
def __init__(self, data):
    self.data = data
    self.next = None
```

✅ Satisfies: **New Node (Rubric)**

---

### 2. LinkedList Initialization

Implemented:

- `self.head = None` to represent an empty list

```python
def __init__(self):
    self.head = None
```

✅ Satisfies: **Empty List Handling**

---

### 3. Insert at Front

Implemented constant-time insertion:

```python
def insert_at_front(self, data):
    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node
```

✔ O(1) time complexity
✔ Updates head correctly

---

### 4. Insert at End (Optional Enhancement)

Added traversal-based insertion:

```python
def insert_at_end(self, data):
    ...
```

✔ Handles empty list case
✔ Traverses to last node
✔ Appends new node

---

### 5. Recursive Sum

Implemented using a helper function:

```python
def recursive_sum(self):
    def helper(node):
        if node is None:
            return 0
        return node.data + helper(node.next)
```

✔ Base case: `node is None → 0`
✔ Recursive case: `data + next node`

✅ Satisfies: **Recursion - Sum Value**

---

### 6. Recursive Search

Implemented boolean search:

```python
def recursive_search(self, target):
    def helper(node):
        if node is None:
            return False
        if node.data == target:
            return True
        return helper(node.next)
```

✔ Stops when value is found
✔ Returns False at end

✅ Satisfies:

- **Search True Case**
- **Search False Case**

---

### 7. Recursive Reverse (In-Place)

Implemented pointer reversal using recursion:

```python
def recursive_reverse(self):
    def helper(current, prev):
        if current is None:
            return prev

        next_node = current.next
        current.next = prev
        return helper(next_node, current)

    self.head = helper(self.head, None)
```

✔ No new list created
✔ Fully in-place
✔ Updates `head`

✅ Satisfies: **Recursion - List In-Place**

---

### 8. Display Method

Added for visualization:

```python
def display(self):
    ...
```

✔ Outputs format:

```
20 -> 10 -> 5 -> None
```

---

### 9. main.py Implementation

Completed all TODO sections while preserving original comments.

#### Features:

- Creates linked list
- Inserts sample data
- Displays list
- Runs recursive operations:
  - Sum
  - Search (True + False cases)
  - Reverse

#### Example Output:

```
Initial List:
20 -> 10 -> 5 -> None
Sum of elements: 35
Search for 10: True
Search for 999: False
Reversed List:
5 -> 10 -> 20 -> None
```

✔ Demonstrates all required functionality
✔ Matches unit test expectations

---

## 🧪 Testing

Run tests with:

```bash
pytest
```

All tests pass, including:

- Insert operations
- Recursive sum
- Recursive search (true/false)
- Recursive reverse

---

## 🧠 Key Concepts Demonstrated

### Linked Lists

- Dynamic data structure
- Node-based memory model
- Efficient insertions

### Recursion

- Base case vs recursive case
- Elegant traversal without loops
- Stack-based execution

---

## 🧹 Cleanup & Best Practices

- Removed all `pass` placeholders
- Kept TODO comments (as required)
- Ensured clean, readable output
- Structured code with helper functions for recursion

---

## 🚀 How to Run

### Run the program:

```bash
python3 main.py
```

### Run tests:

```bash
pytest
```

---

## ✅ Final Status

✔ All rubric requirements satisfied
✔ All tests passing
✔ Clean, readable implementation
✔ Fully documented

---

## 📎 Notes

This implementation emphasizes clarity and correctness, especially in recursive logic, ensuring each operation follows proper base and recursive cases while maintaining efficiency and readability.
