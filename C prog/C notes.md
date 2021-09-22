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

## nkskf
