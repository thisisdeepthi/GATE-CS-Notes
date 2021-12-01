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