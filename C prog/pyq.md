# 2019 ques

1.

```
Consider the following C program:

#include <stdio.h>

int main()

{

int a[ ] = {2, 4, 6, 8, 10};

int i, sum = 0, *b = a + 4;

for (i = 0; i < 5; i++)

sum = sum + (*b – i) – *(b – i);

printf (“%d\n”, sum);

return 0;

}

The output of the above C program is __________. 

```

***Ans: 10***

```
Explanation: 
*b = a+4 => this points to a[4]
(*b - i) => *b is the value of a[4] which is 10
*(b - i) => a[b-i] i.e., if b points to 4th value, so *(b - 1) = a[4-1]
```

---

2.

```
Consider the following C program:

#include <stdio.h>

int r(){

static int num=7;

return num--;

}

int main(){

for (r();r();r())

printf(“%d”,r());

return 0;

}

Which one of the following values will be displayed on execution of the programs?

 (A)  41
 
 (B)  52
 
 (C)  63
 
 (D)  630
```

***Ans: 52***

```

Explanation:
on first iteration :- r()⟹ return 7 but num changed to 6.

r()⟹ return 6 but num changed to 5.⟹ condition evaluate to true ⟹ for loop body executes !

  printf("%d",r()); ⟹ return 5 but num changed to 4.⟹ print 5 on the screen.

r()⟹ return 4 but num changed to 3.

r()⟹ return 3 but num changed to 2.⟹ condition evaluate to true ⟹ for loop body executes !

  printf("%d",r()); ⟹ return 2 but num changed to 1.⟹ print 2 on the screen.

r()⟹ return 1 but num changed to 0.

r()⟹ return 0 but num changed to −1.⟹ condition evaluate to false ⟹ for loop over !
```

---

3.

```
Consider the following C function.

void convert(int n){ 

if(n<0)

     printf(“%d”,n);

else {

        convert(n/2);

        printf(“%d”,n%2);

}

}

Which one of the following will happen when the function convert is called with any positive integer n as argument?

 (A)  It will print the binary representation of n and terminate
 
 (B)  It will print the binary representation of n in the reverse order and terminate
 
 (C)  It will print the binary representation of n but will not terminate
 
 (D)  It will not print anything and will not terminate
```

***Ans: (D)***

```
Explanation:
If the n is 1, then 1/2=0.5=0 
0/2 = 0 
so the convert runs infinitely
```

---

4. 

```
Let T be a full binary tree with 8 leaves. (A full binary tree has every level full.) Suppose two leaves a and b of T are chosen uniformly and independently at random. The expected value of the distance between a and b in T (i.e., the number of edges in the unique path between a and b) is (rounded off to 2 decimal places) ___________ .
```

***Ans: 4.25***

**Explanation:**
Refer this link: [Refer](https://testbook.com/question-answer/let-t-be-a-full-binary-tree-with-8-leaves-a-full--5d5ab5f9fdb8bb738c382cf3)

---

## 2018 ques

5. 

```
Consider the following C program.

#include<stdio.h>
struct Ournode{
    char x,y,z;
};
int main(){
    struct Ournode p = {'1', '0', 'a'+2};
    struct Ournode *q = &p;
    printf ("%c, %c", *((char*)q+1), *((char*)q+2));
    return 0;
}
The output of this program is:
 (A) 0, c
 
 (B) 0, a+2
 
 (C) '0', 'a+2'
 
 (D) '0', 'c'
```

***Ans: (A)***

```
Explanation:
Here *q points to start of struct which is 1
'a'+2 is nothing but c
```

---

## 2017 ques

6. 

```
Consider the following C program

#include <stdio.h>
#include <string.h>
 
void printlength (char *s, char *t) {
   unsigned int c=0;
   int len = ((strlen(s) - strlen(t)) > c) ? strlen(s): strlen(t);
   printf("%d\n",len);
}
 
void main () {
   char *x = "abc",
   char *y = "defgh";
   printlength (x,y);
}
Rcall that strlen is defined in string. h as returning a value of type size_t, which is an unsigned int. The output of the program is ______.
```

***Ans: 3.0***

```
Since we are comparing with unsigned int which is c, that -2(strlen(s)-strlen(t)) is promoted to unsigned. So that it becomes 2.
```

---

7. 

```
The output of executing the following C program is ____________ .

#include <stdio.h>
 
int total (int v) {
   static int count = 0;
   while(v) {
      count += v&1; //it counts the number of 1s
      v >>= 1; // right shift by 1 bit
   }
   return count ;
}
 
void main () {
    static int x = 0;
    int i =5;
    for (; i>0;i--) {
        x=x+total(i);
    }
    printf("%d\n",x);
}
```

***Ans: 23***

---

