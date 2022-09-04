# C
Learning C 

C Programming Notes: 

Pre-processing directive: 
#include <stdio.h>

Int main(void){
	printf(“Hello\n”);
	return 0; 
}

getchar() function is used so that the program pauses until the user hits the enter key. getchar(); // To absorb the enter key


return 0; is used to indicate to the program that it ran successfully.

Comments: /*  */ 

Constants are defined by #define; Example #define PI 3.142

To output, an integer/string from printf one must but %d/%s
Scanf to read anything (input that matches format specifier) 
int a; 
Float num; 
Char text[20];
scanf (“%d %f %s”, &a, &num, text);
print(“You entered: %d”, a);
Note that the & must be used to access the variable addresses. The & isn't needed for a string because a string name acts as a pointer.
Note: the & sign before the variable name is the address operator - gives the address, location in memory of a variable. This is because scanf places an input value at a variable address. 
Note: scanf() stops reading when it encounters a space, so text such as “Mia Gauci” is 2 separate inputs for scanf() hence why we use gets for strings
Note: % are format specifiers
%[*][max_field]conversion character
The optional * will skip the input field.
The optional max_width gives the maximum number of characters to assign to an input field.
The conversion character converts the argument, if necessary, to the indicated type:
d decimal
c character
s string
f float
x hexadecimal

gets is to read input as an ordered sequence of characters - string

getchar() and putchar() are used for a single character 
Char a = getchar(); 
printf(“You entered: ”);
putchar(a);
Return 0; 

gets() and puts() are used for string 
Char a[100]; 
gets(a);
“You entered”;
puts(a);

Note: C may not evaluate a numeric expression as desired when the associative property allows any order. For example, x*y*z may be evaluated as (x * y) * z or as x * (y * z). If order is important, break the expression into separate statements.

Type casting is when you force the result of an expression to a different type: avg = (float) total/count; 

Y = (x >= 5)? 5:x; 
Equivalent to 
If (x>=5)
	y=5;
Else
	y=x; 

an if-else if statement is preferred over nested if statements for clarity.

for(initiative; condition; increment){
	Statements; 
}

#include <stdio.h>
Int sum_up(int x, int y);
Int main(){
	Int x, y, result;
	X = 3;
Y = 12;
Result = sum_up(x, y);
printf(“%d + %d = %d”, x, y, result);
Return 0; 
}

Int sum_up(int x, int y){
 x+=y;
return(x);
}

-
Recursive function 
	Int fact(int n){
If (n == 1) return 1; 
Return n * fact(n-1);
}

-
Traversing the array 
	Int a[10];
Int k; 
For (k = 0; k<10; k++){
A[k] = k *10;
}

-
Nested for loops
Int a[2][3] = {
{3,2,6}
{4,5,20}
}
Int k ,j;
For (k=0;k<2;k++){
	For(j=0;j<3;j++){
	printf(“%d”, a[k][j]);
}
printf(“\n”);
}



USING MEMORY:
The scanf() function places the value entered by the user at the location, or address, of the variable. This is accomplished by using the & symbol.

Pointers are very important in C programming because they allow you to easily work with memory locations.
They are fundamental to arrays, strings, and other data structures and algorithms.
A pointer is a variable that contains the address of another variable. In other words, it "points" to the location assigned to a variable and can indirectly access the variable.
Pointers are declared using the * symbol and take the form:
Pointer_type *identifier 

pointer_type is the type of data the pointer will be pointing to. The actual pointer data type is a hexadecimal number, but when declaring a pointer, you must indicate what type of data it will be pointing to.
Asterisk * declares a pointer and should appear next to the identifier used for the pointer variable.
The following program demonstrates variables, pointers, and addresses:

----
Int x = 5; 
Int y; 
Int *p  = NULL;
P = &x;

Y = *p + 2 // y = 7 
Y += *p // y = 12
*p = Y; //x = 12 
(*p)++ // 13

--
Pointers are especially useful with arrays. An array declaration reserves a block of contiguous memory addresses for its elements. With pointers, we can point to the first element and then use address arithmetic to traverse the array:
+ is used to move forward to a memory location
- is used to move backward to a memory location

An important concept with arrays is that an array name acts as a pointer to the first element of the array. Therefore, the statement ptr = a can be thought of as ptr = &a[0].
Consider the following statement, which prints the first element of the array: printf("%d ", *a);

Lets say we have int B[2][3]
1st memory location of B is B[0][0]= 400
Print B //400 returns a pointer to 1 dimensional array of 3 ints 
Print *B //400 returns a pointer to an integer 
Print B[0] //400
Print &B[0][0] //400 

3-dimensional array; 

Int c[3][2][2]
int(*p)[2][2] = c;
Print c //800 -> int(*)[2][2]; dereferencing a 2d array 
Print *c or c[0] or &c[0][0]// by dereferencing c once where by dereferencing I mean *; it gives a 1 dimensional array 








SEEING HOW PARAMETERS WORK:
Void test(int *x){
*x += *x/2;
}

Int main(){
Int v =8; 
test(&v);
printf(“%d”,v);
}

Keep in mind that a[k] = *(a+k)

Sum of elements in array;
	When we call int A[] in parameter we’re basically saying int *A i.e - arrays are always stored as reference parameters where basically the memory location of the element of the array is passed 
Arrays are called by reference not by value 









Linked Lists: 

Each node consists of a data item and an address of another node 
Node - a collection of 2 sub-elements that stores the element and the other part stores the link to the next node. 

Remember: 
Head points to the first node of the linked list 
Next pointer of the last node = NULL so if the node = NULL we reached the end of the linked list 

C pointers to struct;

Struct name{
	Member1;
	Member2; 
}
Int main(){
	//ptr is a pointer to struct 
	Struct name *ptr, Harry; 
}

To access members of a structure using pointers we use the -> operator

#include <stdio.h>
struct person
{
   int age;
   float weight;
};

int main()
{
    struct person *personPtr, person1;
//the address of person1 is stored in the personPtr pointer
//Hence the members of person1 are accessed using the personPtr pointer
    personPtr = &person1;   

    printf("Enter age: ");
//personPtr->age is equivalent to (*personPtr).age
    scanf("%d", &personPtr->age);

    printf("Enter weight: ");
//personPtr->weight is equivalent to (*personPtr).weight
    scanf("%f", &personPtr->weight);

    printf("Displaying:\n");
    printf("Age: %d\n", personPtr->age);
    printf("weight: %f", personPtr->weight);

    return 0;
}


Data item and the next node in a struct;

Struct node{
	Int data; 
	Struct node *next; 
}

NOTE: MALLOC() - memory allocation of linked list nodes- function reserves a block of memory of the specified number of bytes. And, it returns a pointer of void which can be cast into pointers of any form.: malloc is used to assign a specified amount of memory for an array to be created and returns a pointer to the space allocated in memory using this function. 

Ptr = (castType*)malloc(size);

//Allocating 400 bytes of memory since the size of the float is 4bytes and the pointer ptr holds the address of the 1st byte in the allocated memory. If memory isn’t located, the expression results in a NULL pointer 
Example: ptr = (float*)malloc(100*sizeof(float));

The malloc() function allocates memory and leaves the memory uninitialized, whereas the calloc() function allocates memory and initializes all bits to zero 

//Allocating contiguous space in memory for 25 elements of type float 
Example; ptr = (float*) calloc(25, sizeof(float));

//Frees the space allocated in the memory pointed by ptr 
free(ptr);









// Program to calculate the sum of n numbers entered by the user

#include <stdio.h>
#include <stdlib.h>

int main() {
  int n, i, *ptr, sum = 0;

  printf("Enter number of elements: ");
  scanf("%d", &n);

//Allocating memory to store all the integers 
  ptr = (int*) malloc(n * sizeof(int));
 
  // if memory cannot be allocated
  if(ptr == NULL) {
    printf("Error! memory not allocated.");
    exit(0);
  }

  printf("Enter elements: ");
  for(i = 0; i < n; ++i) {
//stores int at the particular memory location assigned 
    scanf("%d", ptr + i);
    sum += *(ptr + i);
  }

  printf("Sum = %d", sum);
  
  // deallocating the memory
  free(ptr);

  return 0;
}



Each struct node has a data item and a pointer to another struct node
//Creating a simple linked list with 3 items to understand how it works


Struct sPerson *getNewPerson(const int age){
	//making a pointer to a new structure 
	Struct sPerson *newPerson = Null; 
	//Allocate memory for all the bytes needed to store sPerson
	newPerson = malloc(sizeof(struct sPerson));
	//assigning the age value
	newPerson->age = age; 
	//printing the memory address
	printf(“created new person at %p \n”, newPerson);
	//returns the pointer to the newly allocated memory 
	return newPerson; 
}

Dynamic memory allocation of structs

#include <stdio.h>
#include <stdlib.h>
struct person {
   int age;
   float weight;
   char name[30];
};

int main()
{
   struct person *ptr;
   int i, n;

   printf("Enter the number of persons: ");
   scanf("%d", &n);

   // allocating memory for n numbers of struct person
   ptr = (struct person*) malloc(n * sizeof(struct person));

   for(i = 0; i < n; ++i)
   {
       printf("Enter first name and age respectively: ");

       // To access members of 1st struct person,
       // ptr->name and ptr->age is used

       // To access members of 2nd struct person,
       // (ptr+1)->name and (ptr+1)->age is used
       scanf("%s %d", (ptr+i)->name, &(ptr+i)->age);
   }

   printf("Displaying Information:\n");
   for(i = 0; i < n; ++i)
       printf("Name: %s\tAge: %d\n", (ptr+i)->name, (ptr+i)->age);

   return 0;
}

Traversing a linked list; 

struct node *temp = head;
printf("\n\nList elements are - \n");
while(temp != NULL) {
  printf("%d --->",temp->data);
  temp = temp->next;
}

Strings stored in character arrays 
Size of array > no. of characters in string +1 
Terminate char array by using C[4] = “\0”; 
	
C exam: Code-based 
Q1: 
Q2: write 3 methods/functions - revise resurrection, parameter passing by reference and by value  
By reference use pointers - use * - n% symbol 
Q3: Generating random things - make sure that we know how to generate random characters 
//SHOOT ME SHOOT ME SHOOT ME
Q4: Linked lists - Adding a node at the end of the list and a node at the end of the list 


Palindrome and Anagram 

Side notes:
When comparing an array of integers(marks[i] == search)
2D arrays: int matrix[4][2] where 4 is the number of rows, 2 is the number of columns 
It is very important that every string will be longenough to allow C to put the null character at the end. Note that if there is not enoughspace for the null character then C will not know which is the end of the string anit cantherefore display garbage characters on the screen when display
Strcpy - copies one string to another 
Strlen - gets the length of the string 
Strcat - adds the characters of a string to one another 
Strcmp - compares strings 
Strnicmp - case insensitive 
Strcspn - returns the position of a character in a string

Char s[10] = “hello”; 
For (int i=0; i<strlen(s); i++)
{
	S[i] = toupper(s[i]);
}
puts(s);
Return 0; 

To check whether a char is a digit, letter, uppercase whatever use the ctype.h library found on page 42 of the notes 


