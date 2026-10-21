# Advanced Data Structures Implementation (C++)

A performance-focused **C++ Template Library** implementing core computer science data structures, specifically a self-balancing **AVL Binary Search Tree** and a custom **HashMap**. 

This project demonstrates rigorous memory management, algorithmic balancing via tree rotations, and key-value pair mapping designed for optimized search, insertion, and retrieval complexities.

## 🚀 Key Features

* **Self-Balancing AVL Architecture:** Automatically balances node heights upon insertion using single and double tree rotations to guarantee \(O(\log n)\) search efficiency.
* **Generic Templating:** Utilizes C++ templates to support arbitrary data types for keys and values across both trees and maps.
* **Full-Featured HashMap:** Implements a complete suite of hash-table operations including collision handling, dynamic retrieval, and state resetting.
* **Linear Traversal Ecosystem:** Generates dynamic, sorted memory structures from the underlying tree elements natively.

## 🧱 Core Class Architecture & API Reference

### 1. AVL Tree (`Tree.h`)
The `Tree` class manages self-balancing binary search nodes containing generic key-value pairs.

* **`Insert(Key, Value)`:** Adds a unique key-value pair to the tree. If the key does not already exist, it triggers balancing algorithms and recursive rotations to adjust tree height.
* **`inOrderList()`:** Traverses the tree using an in-order algorithm to return a dynamically allocated array containing all stored values in perfectly sorted order.
* **`list()`:** Generates a flat array representing the structural arrangement of the tree corresponding to its overall allocation size.
* **Balancing Utilities:** Internal private routines compute structural height differentials to execute left/right balancing rotations.
<br>

## 📊 Algorithmic Complexity Profile

The implementations are optimized to meet standard theoretical time-complexity benchmarks. By utilizing self-balancing heights for the tree and optimized hashing metrics for the map, the operations scale efficiently:

### Time & Space Complexity Matrix

| Data Structure | Operation | Average Complexity | Worst-Case Complexity | Space Complexity |
| :--- | :--- | :--- | :--- | :--- |
| **AVL Tree** | `Insert()` | \(O(\log n)\) | \(O(\log n)\) | O(1) auxiliary |
| **AVL Tree** | `inOrderList()` | O(n) | O(n) | O(n) for array allocation |
| **HashMap** | `put()` | O(1) | O(n) * | O(1) auxiliary |
| **HashMap** | `get()` / `remove()`| O(1) | O(n) * | O(1) auxiliary |

> \* *Note on Worst-Case HashMap Performance: Worst-case O(n) performance only occurs under a complete hash collision scenario where all elements map to the exact same bucket, degrading the search array into a linear scan.*

<br>

### Key Optimization Mechanics
* **AVL Tree Rotations:** Standard Binary Search Trees can degrade into an inefficient O(n) linear chain if data is inserted in sorted order. The explicit height calculations and structural balancing rules implemented in `Tree.h` guarantee that operations never drop below \(O(\log n)\).
* **HashMap Distribution:** The internal `getHash` and `hashCode` routines work to uniformly scatter key distribution across allocated memory fields to maximize O(1) constant-time operations.

### 2. Hash Map (`HashMap.h`)
A robust key-value lookup system supporting standard dictionary behavior.

| Method | Description |
| :--- | :--- |
| **`put(Key, Value)`** | Hashes the target key and inserts the pair into the underlying bucket index. |
| **`get(Key)`** | Retrieves the associated value for an inputted key. |
| **`remove(Key)`** | Deletes a key-value node from the map. |
| **`containsKey(Key)` / `containsValue(Value)`** | Evaluates presence of specified keys or values in \(O(1)\) average time. |
| **`getKeys()`** | Extracts a raw array or collection containing all active identifiers. |
| **`getHash(Key)` / `hashCode(Key)`** | Determines the internal hash index assignment for consistent distribution. |
| **`isEmpty()` / `clear()`** | Checks current inventory tracking states or flushes memory pools completely. |

## 🛠️ Tech Stack

* **Language:** C++ (C++11 or higher recommended)
* **Paradigm:** Object-Oriented Programming (OOP) & Generic Template Programming
* **Memory Management:** Manual dynamic allocation using pointer arithmetic

## ⚙️ Getting Started

### Prerequisites
* A C++ compiler supporting modern standards (e.g., `g++` or `clang++`).
* A build environment terminal or command prompt.

### Compilation Example
Because this library leverages generic C++ templates, you can easily include the header files directly into a driver `main.cpp` file:

```cpp
#include "Tree.h"
#include "HashMap.h"
#include <iostream>

int main() {
    // Example: Create a self-balancing AVL Tree
    Tree<int, std::string> avlTree;
    avlTree.Insert(10, "Root Node");
    avlTree.Insert(20, "Right Child (Triggers Rotation)");
    
    return 0;
}
```

Compile the execution binary via your terminal:
```bash
g++ -std=c++11 main.cpp -o datastructures_demo
./datastructures_demo
```

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
