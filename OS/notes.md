# OS notes

## Points

1. Multiprogramming - running more than one process(eg. running excel nd firefox simultaneously)
2. Multiprocessing - using more than one CPU
3. Timesharing -  based on multiprogramming. Many prog are context switched so fast that user gets an illusion that processes run concurrently
4. Multitasking

## Program and Process

- Program => a file passive entity residing on disk
- Process => program in execution
    - has text(code),data,stack,heap,prog counter,register contents
- Thread share code, data and files along with heap. But has its own copy of stack,register and PC

### Process states

[![image.png](https://i.postimg.cc/HnmWqTdc/image.png)](https://postimg.cc/N9NwTqyB)

- PCB => details abt process. when context switched, state is stored and on resume state is retrieved

### Process creation

- ```init``` is parent of all process
- Child process can
    - use parent's resource and also allocated from os
    - execute same code as parent or loaded code ( ```exec() system call```)
- Parent process can execute
     - concurrently with child
     - wait till one or all children terminate => ```wait()``` provide status of child to parent
- When executing the same code, fork() returns zero for a child process
- ```exit()``` sys call to terminate
- Child process terminate
    - if no longer needed
    - excess resource usage
    - if parent terminates, child cannot exist. It is called **cascading termination**
- **Zombie process** - a process which has completed execution but its entry is still in the process table as its parent processs didn't invoke wait() sys call
- **Orphan process** - If parent terminates without wait() statement, child has no parent. By default, they become the child of the init process. init periodically issues wait() to release these processes

## IPC

- Cooperating process => need data from other process
- Independent process= => no need to share data

- Types
    - Shared memory => Fast, no kernel intervention, cache coherence prob
    - Message passing => slow, kernel intervention, distributed sys, higher performance (multiprocessor)

## Parallelism

- process run simultaneously, like on multiple cores of processor

## Concurrency

- Even in single processor sys, process run concurrently but not at same time

## Multithreading models

- Many to one:
    - Many user threads to one kernel thread
    - no concurrency
- One to one:
    - one user thread to one kernel thread
    - even if one thread is blocked, others are not blocked
    - true concurrency
- Many to many:
    - many user threads to same or less num of kernel threads
    - best multithreading model


## Scheduling

- Long term scheduler
    - job scheduler
    - from disk to main mem
- Short term scheduler
    - CPU schedling
    - must be fast
    - does the job of job scheduler also in some sys
- Middle term
    - semi executed processs are swapped to disk
    - swapping done by middle term



## Demand Paging

- OS copies a page from sec mem to main mem only if there is a need to access that page and the page is not in main mem

## Page fault

- If a page is not in main mem when it is accessed, then it is called miss and a page fault occurs.
- If no of page fault is high, then AMAT is very high

## Thrashing

- If the page fault and swapping of pages occur frequently at high rate, then the OS has to spend more time in swapping
- Thus the AMAT is high

```
Total AMAT = Page fault rate * MAT when page fault + (1-page fault rate) * MAT when no page fault
```

## Banker's Algorithm

- Deadlock avoidance
- To implement, we need four DS

    - Allocation => resources allocated to particular process
    - Max => max resources allocated to a particular process
    - Available => resources currently available (1D matrix)
    - Need => Max - allocation

- Two algorithms 

    - Resource request 
    - Safety algorithm


### Resource request algorithm

```
1) If Requesti <= Needi 
Goto step (2) ; otherwise, raise an error condition, since the process has exceeded its maximum claim.
2) If Requesti <= Available 
Goto step (3); otherwise, Pi must wait, since the resources are not available.
3) Have the system pretend to have allocated the requested resources to process Pi by modifying the state as 
follows: 
Available = Available – Requesti 
Allocationi = Allocationi + Requesti 
Needi = Needi– Requesti
```

### Safety algorithm

```
1) Let Work and Finish be vectors of length ‘m’ and ‘n’ respectively. 
Initialize: Work = Available 
Finish[i] = false; for i=1, 2, 3, 4….n
2) Find an i such that both 
a) Finish[i] = false 
b) Needi <= Work 
if no such i exists goto step (4)
3) Work = Work + Allocation[i] 
Finish[i] = true 
goto step (2)
4) if Finish [i] = true for all i 
then the system is in a safe state 
```

## Producer-consumer problem using semaphore

- Semaphore => an integer variable that can be accessed thru two operations: wait() and signal()
- wait() => reduces value of semaphore by 1
- signal() => increases by 1
- two types => binary and counting semaphores

### Problem

- Producer => can produce an item and place in the buffer
- consumer => pick items and consume
- when a producer is placing an item in the buffer, then at the same time consumer should not consume any item. In this, buffer is the critical section
- TO solve this prob, consider two counting semaphores - full and empty.
- Full keeps track of no of items in the buffer
- Empty keeps track of unoccupied slots

### Initialisation of semaphore

mutex = 1

full = 0

empty = n

Solution for producer

```
do{

//produce an item

wait(empty);
wait(mutex);

//place in buffer

signal(mutex);
signal(full);

}while(true)
```

When producer produces an item then the value of “empty” is reduced by 1 because one slot will be filled now. The value of mutex is also reduced to prevent consumer to access the buffer. Now, the producer has placed the item and thus the value of “full” is increased by 1. The value of mutex is also increased by 1 because the task of producer has been completed and consumer can access the buffer. 

Solution for consumer

```
do{

wait(full);
wait(mutex);

// remove item from buffer

signal(mutex);
signal(empty);

// consumes item

}while(true)
```

As the consumer is removing an item from buffer, therefore the value of “full” is reduced by 1 and the value is mutex is also reduced so that the producer cannot access the buffer at this moment. Now, the consumer has consumed the item, thus increasing the value of “empty” by 1. The value of mutex is also increased so that producer can access the buffer now. 

## Process scheduling algo

```
Arrival time - time at which process is arrived
Completion time - at which process completed its execution
Burst time - req by process for execution
Turn around time - ```completion - arrival time```
Waiting time - ```turn around - burst time```
```

1. FCFS
2. SJF
3. SRTF
4. Round robin
5. Priority