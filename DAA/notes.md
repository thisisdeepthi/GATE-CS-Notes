# DAA notes

## Greedy approach

- algorithm picks the best optimal solution at the moment regardless for consequences.

- Characteristics

    - 0/1 knapsack problem
    - Fractional knapsack problem
    - Huffman coding

### Fractional Knapsack problem

- Items are divisible here
- can put fraction of any item into the knapsack
- solved using greedy method

### Steps

1. Compute value/weight ratio for every item
2. Arrange all items in dec order of ratio
3. Start putting the items into the knapsack beginning from the item with the highest ratio. Put as many items as you can into the knapsack

Refer https://www.gatevidyalay.com/fractional-knapsack-problem-using-greedy-approach/ for example

---

### 0/1 knapsack problem

- Items are indivisible here
- cannot take fraction of any item
- either take an item completely or leave it
- solved using dynamic programming

### Steps

1. Draw a table say ‘T’ with (n+1)(n-no of items) number of rows and (w+1) (w- weight limit of knapsack) number of columns. Fill all the boxes of 0th row and 0th column with zeroes
2. Start filling the table row wise top to bottom from left to right.

Use the following formula-

```
T (i , j) = max { T ( i-1 , j ) , valuei + T( i-1 , j – weighti ) }
```

3. To identify the items that must be put into the knapsack to obtain that maximum profit,

Consider the last column of the table.

Start scanning the entries from bottom to top.

On encountering an entry whose value is not same as the value stored in the entry immediately above it, mark the row label of that entry.

After all the entries are scanned, the marked labels represent the items that must be put into the knapsack.

Refer https://www.gatevidyalay.com/0-1-knapsack-problem-using-dynamic-programming-approach/ for example

---

