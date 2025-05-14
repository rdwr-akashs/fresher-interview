# Data Structures and Algorithms (DSA) Interview Questions for Freshers

---

## 🟢 Easy-Level Questions

1. **What is an array? How is it different from a linked list?**
   - Expected Answer: An array is a collection of elements stored in contiguous memory locations. A linked list consists of nodes where each node points to the next, and elements are not stored in contiguous memory.

2. **What is a stack? Can you give an example of where you might use one?**
   - Expected Answer: A stack is a linear data structure that follows the Last In, First Out (LIFO) principle. Example: Undo functionality in a text editor.

3. **What is a queue? How is it different from a stack?**
   - Expected Answer: A queue follows the First In, First Out (FIFO) principle. A stack uses LIFO (Last In, First Out).

4. **What is the difference between a singly linked list and a doubly linked list?**
   - Expected Answer: A singly linked list has nodes with a single pointer to the next node, while a doubly linked list has pointers to both the next and previous nodes.

5. **What is the time complexity of accessing an element in an array?**
   - Expected Answer: O(1) – Direct access using an index.

6. **Can you explain the concept of a hash table?**
   - Expected Answer: A hash table stores data in key-value pairs. The key is hashed to an index, where the value is stored.

7. **What is a binary search?**
   - Expected Answer: Binary search is an algorithm for finding an element in a sorted array by repeatedly dividing the search interval in half.

8. **What is the difference between a tree and a graph?**
   - Expected Answer: A tree is a hierarchical structure with a single root node, while a graph is a collection of nodes that may have more than one root and cycles.

9. **What is a heap?**
   - Expected Answer: A heap is a binary tree-based data structure that satisfies the heap property, i.e., the key of a parent node is always greater than or equal to the keys of its children (max-heap) or less than or equal to the keys of its children (min-heap).

10. **What is the time complexity of searching for an element in a linked list?**
   - Expected Answer: O(n) – Each element has to be checked sequentially.

---

## 🟡 Medium-Level Questions

11. **What is a binary tree? Can you explain its types?**
   - Expected Answer: A binary tree is a tree data structure where each node has at most two children. Types: Full Binary Tree, Complete Binary Tree, Perfect Binary Tree, and Balanced Binary Tree.

12. **What is a breadth-first search (BFS) and a depth-first search (DFS)? How do they differ?**
   - Expected Answer: BFS explores all neighbors at the present depth level before moving on to nodes at the next depth level. DFS explores as far as possible along a branch before backtracking.

13. **What is a graph traversal algorithm? Can you give examples?**
   - Expected Answer: Graph traversal algorithms visit each node in a graph. Examples: BFS, DFS.

14. **What is a circular linked list? How is it different from a regular linked list?**
   - Expected Answer: A circular linked list is a linked list where the last node points to the first node instead of null, forming a circle.

15. **Can you explain the quicksort algorithm? What is its time complexity?**
   - Expected Answer: Quicksort is a divide-and-conquer algorithm that divides the array into two subarrays, sorts them, and merges them. Its time complexity is O(n log n) on average and O(n²) in the worst case.

16. **What is the difference between an AVL tree and a Red-Black tree?**
   - Expected Answer: Both are self-balancing binary search trees. An AVL tree is more strictly balanced, while a Red-Black tree has less strict balancing, making it easier to maintain.

17. **What is the time complexity of searching for an element in a binary search tree (BST)?**
   - Expected Answer: O(log n) on average, but O(n) in the worst case (for unbalanced BST).

18. **What is a trie? Where is it used?**
   - Expected Answer: A trie is a tree-like data structure used to store a dynamic set of strings, often used in autocomplete systems and dictionaries.

19. **What is dynamic programming? Can you explain the Fibonacci sequence using dynamic programming?**
   - Expected Answer: Dynamic programming is a method for solving problems by breaking them down into simpler subproblems and storing the results of subproblems. Fibonacci sequence can be solved efficiently using dynamic programming by storing previously computed values.

20. **What is a priority queue? How does it differ from a regular queue?**
   - Expected Answer: A priority queue is a queue where each element is associated with a priority. Elements are dequeued based on their priority, not their arrival order.

---

## 🔴 Hard-Level Questions

21. **What is the time complexity of different sorting algorithms: Merge Sort, Quick Sort, and Bubble Sort?**
   - Expected Answer: 
     - Merge Sort: O(n log n)
     - Quick Sort: O(n log n) on average, O(n²) in the worst case
     - Bubble Sort: O(n²)

22. **Explain the concept of a graph’s topological sort. How is it performed?**
   - Expected Answer: Topological sort is a linear ordering of vertices in a Directed Acyclic Graph (DAG), where for every directed edge u → v, vertex u comes before v.

23. **What is Dijkstra’s algorithm? How does it find the shortest path in a graph?**
   - Expected Answer: Dijkstra's algorithm finds the shortest path from a source node to all other nodes in a graph with non-negative edge weights, by iteratively selecting the node with the minimum distance.

24. **Explain the difference between a greedy algorithm and dynamic programming.**
   - Expected Answer: Greedy algorithms make locally optimal choices at each step with the hope of finding a global optimum, while dynamic programming solves problems by breaking them down into overlapping subproblems and solving them once.

25. **How do you detect a cycle in a directed graph?**
   - Expected Answer: A cycle can be detected in a directed graph using Depth-First Search (DFS) by checking for back edges during traversal.

---

## 🤔 Tricky Questions

26. **How would you find the middle element of a linked list in a single pass?**
   - Expected Answer: Use two pointers: one moves one step at a time, and the other moves two steps at a time. When the fast pointer reaches the end, the slow pointer will be at the middle.

27. **How would you reverse a singly linked list?**
   - Expected Answer: You can reverse a singly linked list by changing the next pointers of the nodes one by one while iterating through the list.

28. **Can you implement a function to check if a given string is a palindrome using a stack?**
   - Expected Answer: You can use a stack to push characters of the string, then pop them and compare with the original string.

29. **What is the difference between BFS and DFS in terms of implementation?**
   - Expected Answer: BFS uses a queue for implementation, while DFS uses a stack or recursion.

30. **What is the maximum number of comparisons required to find the smallest and largest element in an array?**
   - Expected Answer: 3n/2 comparisons in the worst case, where n is the number of elements in the array.
