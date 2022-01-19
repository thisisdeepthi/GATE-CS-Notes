# K map rules

- No zeros allowed
- No diagonals
- only power of 2
- group as large as possible
- overlapping allowed

## Implicants

- Prime => all possible groups formed in kmap
- essential prime => cover atleast one minterm that can’t be covered by any other prime implicant
- reduntant prime => prime implicants for which each of its minterm is covered by some essential prime implicant
- selective prime => neither essential nor redundant prime implicants