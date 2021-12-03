# OS notes

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

