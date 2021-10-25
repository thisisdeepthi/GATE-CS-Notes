# Frequently Asked topics

- Relational Algebra
- SQL (majority)
- Normalization => FD
- Transaction => Serializability (def 1 qn)

---

## Cartesian product

- If T1 has m tuples and n cols and T2 has x tuples and r cols, then 

```
No of tuples = m * x
No of cols = n+r
```

---

## Operators

[![image.png](https://i.postimg.cc/DwrJ2S9v/image.png)](https://postimg.cc/9DfFbQXK)

---

## Notes

- Selection operator obeys commutative property while projection doesn't
- comma between tables in from clause means cartesian product 
- To perform natural join, the common attribute name must be the same.
- During natural join, if there are two common attributes, then join is done based on both. i.e., if rno nd name are there, then (rno,name) will be checked and the same goes for n number of common attributes.

