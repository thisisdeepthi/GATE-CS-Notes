# Introduction

- subset of C++
- Structure:
  - Header file => files with .h extension contains C func declaration nd macro defn
  [![image.png](https://i.postimg.cc/m2FZZhdD/image.png)](https://postimg.cc/56bWn9Wd)
  - Main func
  - variable declaration
  - body
  - return => to know the termination status

---

## int keyword

- size => 4 bytes
- signed int => 32 bits = 1 sign bit + 31 data bit (0 for +ve and 1 for -ve)
- unsigned int => only +ve integers can be stored, all 32 bit for data storage, format specifier %u.

---

## diff between int main() and int main(void)

- int main() => called with any number of arguments, but int main(void) can only be called without any argument. 

---

## macros and preprocessors

- all lines start with # are processes by preprocessor.
- include directive => contents of header file are copied to current file. <> - to look in the standard folder. "" - to look in current folder.
- To define a macro, #define MACRO_NAME fun or constant
- To undefine macro, #undef MACRO_NAME

---

## compilation process

- compiler => converts C prog to executable

1.Pre-processing => includes

- removal of comments
- macro expansion
- included files expansion
- conditional compilation

2.Compilation

- assembly level instructions

3.Assembly

- existing code converted to machine language

4.Linking

- linking all func calls with their defn

---

## Line splicing

- if backslash is at the end of single-line comment then the next line will also become a comment line but it is not in the case of multi-line comment.

-eg:
[![image.png](https://i.postimg.cc/fb81NLbJ/image.png)](https://postimg.cc/qtC1cpyT)

- 32 keywords in C and additional 31 in C++

---

## variables

- should start with letter or _ but not with num
- no space within variable name

Types:

1.Local

- declared nd used inside block (can't be used outside block)

2.Global

- declared outside block so can be used by all funs

3.Static

- preserves its value in multiple fun calls

4.Automatic

- variables declared inside block are automatic and some are explicitly declared with **auto** keyword.
- both behave as **local** variables

5.External

- shared between multiple C files 
- declared with **extern** keyword (declared only not defined)
- also **global**

- constant variable(const) => when initialized can't change their value
- In C, variables are statically scoped
- global and static variables have 0 as default since they have fixed memory location

---

## qns on variable declaration and scope

1. 

[![image.png](https://i.postimg.cc/zfgSxQpD/image.png)](https://postimg.cc/sB3hXwtb)

Ans: When constant value starts with 0, it is octal so the value is 3*8 + 2 = 26

- C allows a global variable to declare once again when first declaration is not initialized

- const, enum, constexpr, macros => these are used to declare variable as constant

- static nd global variables initialized by compiler so must be initialized with constant value in C but it is fine in cpp

---

## Facts

- no data type given, automatically convert to int 
- signed => default modifier for char nd int
- no modifiers for float (like short float, signed float gives compiler error)
- long modifier is allowed in double but no other modifiers are used
- typedef also storage class. volatile nd const => type qualifiers

---

## Storage classes

[![image.png](https://i.postimg.cc/sxBk3Rhf/image.png)](https://postimg.cc/tnjSzwk8)

---

## Const qualifier

[![image.png](https://i.postimg.cc/LsvwZ01P/image.png)](https://postimg.cc/R36XkdGC)

---

## Register keyword

- if we say a variable as register, we can't access it using pointer
- register can be used with pointer variables
- C doesn't allow multiple storage class. so register can't be used with static
- only works locally not globally
- no limit on no of register variables

---

## Extern keyword

- to extend the visibility of variables/fns
- when extern used with variable, it is declared not defined
- when extern variable is declared with initialisation, it is taken as the defn of variable

---

## Static keyword

- allocated memory in data segment not stack
- initialized to 0 if not
- initialized only using constant literals

---

## Return values

- printf() => total no of characters printed or neg val if error
- scanf() => total no of inputs scanned successfully or EOF if input failure occurs
- getchar(), fgetc(), getc() => int not char