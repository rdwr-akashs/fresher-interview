# Operating System (OS) Interview Questions and Answers

## 1. What is a deadlock?
A **deadlock** is a situation in an operating system where a set of processes become stuck in a state where each process is waiting for a resource that is held by another process in the set. As a result, none of the processes can proceed or complete their execution.

Example: Process A holds Resource 1 and waits for Resource 2, while Process B holds Resource 2 and waits for Resource 1.

---

## 2. What are the four conditions for a deadlock?
For a deadlock to occur, the following four conditions must be true simultaneously:

1. **Mutual Exclusion** – At least one resource must be held in a non-shareable mode.
2. **Hold and Wait** – A process is holding at least one resource and waiting to acquire additional resources held by other processes.
3. **No Preemption** – Resources cannot be forcibly taken from processes holding them.
4. **Circular Wait** – A closed chain of processes exists, where each process holds at least one resource that the next process in the chain requires.

---

## 3. What is segmentation?
**Segmentation** is a memory management technique where the memory is divided into different segments based on the logical divisions of a program, such as functions, arrays, objects, etc. Each segment is assigned a segment number and an offset.

Benefits:
- Supports modular programming.
- Enables better memory protection and isolation.

---

## 4. What is a page fault?
A **page fault** occurs when a program tries to access a page in memory that is not currently loaded into RAM. The operating system must then:
1. Pause the program.
2. Load the required page from disk (secondary storage) into RAM.
3. Resume the program from the point it was interrupted.

This process can slow down system performance if page faults happen frequently.

---

## 5. What is a semaphore?
A **semaphore** is a synchronization primitive used to manage access to shared resources in concurrent or multi-threaded environments. It helps avoid race conditions and ensures mutual exclusion.

There are two types of semaphores:
- **Counting Semaphore** – Can take any non-negative integer value.
- **Binary Semaphore (Mutex)** – Takes only 0 or 1 (similar to a lock).

Example:
```c
semaphore.wait();  // Decrement the semaphore
// Critical section
semaphore.signal();  // Increment the semaphore
```

---

## 6. What is scheduling?
**Scheduling** in operating systems refers to the method by which work (processes or threads) is assigned to the CPU. It aims to optimize CPU utilization, throughput, response time, and fairness among processes.

### Common Scheduling Algorithms:
- **First-Come, First-Served (FCFS)**
- **Shortest Job Next (SJN)**
- **Round Robin (RR)**
- **Priority Scheduling**
- **Multilevel Queue Scheduling**

Each algorithm has different trade-offs and is suitable for different types of workloads.
