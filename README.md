# Advanced C
<details>  
<summary>  Lesson 1 </summary>  
  
## COMPILER - MACRO  
### Compiler
- A compiler is a special program that translates a programming language's source code into machine code, bytecode or another programming language. In other words, we can say that it converts the high-level language to machine/binary language. The source code is typically written in a human-readable language such as C or C++.  
- The following are the phases through which our program passes before being transformed into an executable form:  

**1. Preprocessor:**
  - Removal of Comments
  - Expansion of Macros
  - Expansion of the included files
  - Conditional compilation  

**2. Compiling:** Compile filename.i and produce a filename.s. This file is in assembly-level instructions.  
**3. Assembling:** The filename.s is taken as input and turned into filename.o by the assembler. This file contains machine-level instructions.  
**4. Linking:** This is the final phase in which all the linking of function calls with their definitions is done. Linker knows where all these functions are implemented.   
### Macro
- Macros in the C programming language allows developers to define reusable pieces of code, constants, and even function-like constructs.
- A macro is a fragment of code which has been given a name. Whenever the name is used, it is replaced by the contents of the macro.   
- Macros in C are a feature of the C preprocessor.
- There are 3 main groups of macros:  
**1. #include:** The #include directive is used to include the contents of another file into the current source file.  
Example: `#include <stdio.h>`  
**2. #define, #undef:** The #define (#undef) directive is used to define (undefine) macros. It associates a name with a value or an expression.  
Example: 
```
#define PI 3.14
#undef PI
#define PI 3.1415
```  
**3. #if, #elif, #else, #ifdef, #ifndef:** Conditional compilation directives allow including or excluding specific code blocks based on predefined macros or conditions.
</details>  

<details>  
<summary>  Lesson 2 </summary>  
  
## STDARG - ASSERT
### STDARG
The stdarg.h header defines a variable type va_list and three macros which can be used to get the arguments in a function when the number of arguments are not known.  

**1. stdarg.h types:**  

**va_list:** type for iterating arguments  

**2. stdarg.h macros:**  

| Name  | Description |
| ------------- | ------------- |
| **va_start**  | Start iterating arguments with a va_list  |
| **va_arg**  | Retrieve an argument  | 
| **va_end**  | Free a va_list  |
| **va_copy**  | Copy contents of one va_list to another  |
### ASSERT
- Provides a macro called assert
- This macro can be used to verify assumptions made by the program.
- If this assumption is false, nothing happens and the program continues to execute.
- If this assumption is false, The program stops to execute and print a diagnostic message.
- Using for debugging, use #define NDEBUG to turn off debug mode.
</details> 

<details>  
<summary>  Lesson 3 </summary>  
  
## POINTER
Pointers are one of the core components of the C programming language. A pointer can be used to store the memory address of other variables, functions, or even other pointers. The use of pointers allows low-level memory access, dynamic memory allocation, and many other functionality in C.
### Void pointer
- The Void pointers in C are the pointers of type void. It means that they do not have any associated data type.
- One of the main properties of void pointers is that they cannot be dereferenced.
- Syntax: `void *ptr_void;`
### Function Pointer
- Pointer to function is a variable that holds the address of a function. That is, it points to the area in memory that contains the machine code of the function defined in the program. 
- Function pointers allow you to pass a function as an argument to another function, store the function's address in a data structure, or even pass the function as a return value from another function.
### Pointer to Constant
- A way to define a pointer that cannot change the value at the address it points to through dereference, but the value at that address can change.
- Syntax: 
```
int const *ptr_const;
const int *ptr_const;
```
### Constant Pointer
- In constant pointers, the memory address stored inside the pointer is constant and cannot be modified once it is defined. It will always point to the same memory address.
- Syntax: `int *const const_ptr = &value;`
### Pointer to Pointer
- Pointer to Pointer is a data type in a programming language that allows you to store the address of a pointer.
- Pointer to pointer provides a new pointer hierarchy, allowing you to change the value of the original pointer. This hierarchy can be useful in many situations, especially when you work with functions that need to change the value of a pointer.
- Syntax: `int **ptp = &ptr;`
- Application:
  - json data type
  - List data structure
### NULL Pointer
- The Null Pointers are those pointers that do not point to any memory location.
- They can be created by assigning a NULL value to the pointer.
- A pointer of any type can be assigned the NULL value.
</details> 

<details>  
<summary>  Lesson 4 </summary> 
  
## MEMORY LAYOUT
The main.exe program (on windows), main.hex (loaded into the microcontroller) are stored in SSD or FLASH memory. When pressing run programs on the window (powering the microcontroller), these programs will be copied into RAM memory for execution.
### Text segment
- Contains executable instructions.
- Often read-only, to prevent a program from accidentally modifying its instructions.
- Store constants and pointers of char type.
- All variables stored in the Text segment cannot change their values ​​but can only be read.
### Data segment/ Initialized Data Segment
- Contains global and static variables initialized to a non-zero value.
- The value of the variable can be read and changed.
- All variables will be reclaimed after the program ends.
### BSS segment/ Uninitialized Data Segment
- Contains global and static variables initialized with a value of 0 or not assigned a value.
- The value of the variable can be read and changed.
- All variables will be reclaimed after the program ends.
### Stack
- Contains local variables and passed parameters.
- Can read and change the value of the variable during the program's runtime.
- After exiting the function, the memory area will be reclaimed.
### Heap
- The heap is used to dynamically allocate memory during program execution.
- This allows the program to create and release memory as needed, adapting to changes in data during runtime.
- Functions like malloc(), calloc(), realloc(), and free() are used to allocate and free memory on the heap.
- Can read and change the value of the variable during the program's runtime.
</details>

<details>  
<summary>  Lesson 5 </summary> 
  
## EXTERN - STATIC - VOLATILE - REGISTER
### EXTERN
- Used to notify that a variable or function has been declared elsewhere in the program or in another source file.
- This helps the program understand that the variable or function has been defined and will be used from another location, helping to manage associations between different parts of the program or between source files.
- Variables or functions declared with “extern” in C will have external linkage, indicating that they are linked externally.
- In a lengthy program that utilizes several files, the “extern” keyword is frequently employed to declare global variables in header files.
### STATIC
- **Static local variables:** declared within a function, it holds the variable's value across function calls and keeps the variable's scope within that function only.
- **Static global variables:** declared outside the function, it limits the scope of that variable to only the current source file, used to design library files.
### VOLATILE
- Signal to the compiler that a variable may change randomly, beyond the control of the program.
- Prevents the compiler from optimizing or removing operations on that variable, keeping operations on the variable performed as defined.
### REGISTER
- Used to indicate the programmer's intention that a variable be used frequently.
- May be stored in a computer register, rather than in RAM memory which lead to the increasing of accessing speed.
- Using register is only a recommendation to the compiler and does not guarantee that the variable will be stored in the register.
- The compiler may decide not to comply with this recommendation.
</details>

<details>  
<summary>  Lesson 6 </summary> 
  
## GOTO - SETJMP.H
### GOTO
- Allows a program to jump to a label that was previously placed in the same function.
- Provides control over the flow of a program.
- The use of **goto** is generally considered bad because it can make the source code difficult to read and maintain.
### SETJMP.H
- **setjmp.h** is a library in the C programming language, providing two main functions: setjmp and longjmp.
- Both of these functions are commonly used to perform exception handling in C, although it is not a typical way to handle exceptions in the language.
</details>

<details>  
<summary>  Lesson 7 </summary> 
  
## BITMASK
- A technique that uses bits to store and manipulate flags or status.
- Can be used to set, clear, and check the state of specific bits within a word.
- Bitmasks are commonly used to optimize memory, perform logical operations on a cluster of bits, and manage the state, access rights, or other properties of an object.
### NOT bitwise
- Used to perform bitwise NOT operations on each bit of a number. The result is the bitwise inverse of that number.
- Syntax: `int result = ~num;`
### AND bitwise
- Used to perform bitwise AND operations between each pair of bits of two numbers. The result is 1 if both corresponding bits are 1, otherwise 0.
- Syntax: `int result = num1 & num2;`
### OR bitwise
- Used to perform bitwise OR operations between each pair of bits of two numbers. The result is 1 if more than one corresponding bit is 1.
- Syntax: `int result = num1 | num2;`
### XOR bitwise
- Used to perform bitwise XOR between each pair of bits of two numbers. The result is 1 if only one corresponding bit is 1.
- Syntax: `int result = num1 ^ num2;`
### Shift left và Shift right bitwise
- Used to move bits left or right.
- In the case of <<, the bits on the right will be shifted to the left, and the bits on the left will be set to 0.
- Syntax: `int resultLeftShift = num << shiftAmount;`
- In the case of >>, the bits on the left will be shifted to the right, and the bits on the right will be set to 0 or 1 depending on the value of the highest bit (sign bit).
- Syntax: `int resultRightShift = num >> shiftAmount;`
</details>

<details>  
<summary>  Lesson 8 </summary> 
  
## STRUCT - UNION
### Struct
- A struct is a data structure that allows programmers to define a new data type by grouping together variables of different data types.
- Struct allows creating a larger and more organized data entity from its members.
- Syntax:
```
struct structureName {
  dataType member1;
  dataType member2;
  ...
};
```
### Union
- Union is a data structure that helps programmers combine many different data types into the same memory area.
- The main purpose of union is to save memory by sharing the same memory area among its members.
- At a time, only one member of the union can be used.
- Syntax: 
```
union unionName {
  dataType member1;
  dataType member2;
  ...
};
```
</details>

<details>  
<summary>  Lesson 9 </summary> 
  
## JSON
- JSON stands for "JavaScript Object Notation".
- JSON is a common data transfer format in programming and communication between web servers and browsers, as well as between different systems.
- JSON is designed to be easy to read and write for humans, as well as easy to parse and generate for computers.
- It uses a lightweight syntax based on key - value pairs, similar to objects and arrays in JavaScript.
- Each JSON object consists of a set of "key" and "value" pairs, while each JSON array is a set of values.
</details>

<details>  
<summary>  Lesson 10 </summary> 
  
## LINKED LIST
- Linked list is a data structure in computer programming, used to organize and store data.
- Linked List is a linear data structure, in which elements are not stored at a contiguous location, rather they are linked using pointers.
- A linked list consists of a chain of "nodes", each containing a data value and a pointer to the next node in the chain.

</details>

<details>  
<summary>  Lesson 11 </summary> 
  
## JSON
- JSON stands for "JavaScript Object Notation".
- JSON is a common data transfer format in programming and communication between web servers and browsers, as well as between different systems.
- JSON is designed to be easy to read and write for humans, as well as easy to parse and generate for computers.
- It uses a lightweight syntax based on key - value pairs, similar to objects and arrays in JavaScript.
- Each JSON object consists of a set of "key" and "value" pairs, while each JSON array is a set of values.
</details>

<details>  
<summary>  Lesson 12 </summary> 
  
## STACK - QUEQUE
### Stack
- Stack is a data structure that follows the "Last In, First Out" (LIFO) principle, meaning that the last element added to the stack will be the first element removed.
- Basic operations on the stack include:
  - **push:** to add an element to the top of the stack
  - **pop:** to remove an element at the top of the stack.
  - **top:** to get the value of the element at the top of the stack.
### Queque
- Queue is a data structure that follows the "First In, First Out" (FIFO) principle, meaning that the first element added to the queue will be the first element removed.
- Basic operations on queues include:
  - **enqueue:** add elements to the end of the queue
  - **dequeue:** get elements from the beginning of the queue.
  - **front:** get the value of the element at the top of the queue.

</details>

# Advanced C++
<details> 
<summary>  Lesson 13 </summary> 
  
## CLASS
### Class
- Class is a fundamental block of a program that has its own set of methods and variables.
- You can access these methods and variables by creating an object or the instance of the class.
- A class is a collection of objects of the same kind.
- A C++ class is like a blueprint for an object.
### Object
- An object is a recognizable entity having a state and behavior, and these objects hold variables of a class in accordance with the access modifiers.
- It is also known as an instance of a class.
- You can call a member function with the help object and use the dot operator.
- During the declaration of the class, no memory is assigned, but when you create an object, then the memory is allocated.
### Constructor
- Whenever you create an object of a class, a constructor is invoked, and that is why it is called a special member function.
- The constructor's name is like that of the class, and it doesn’t have any return type.
- Even if you do not include a constructor in the class, the compiler creates a default constructor.
- These are generally used for assigning initial values to variables.
### Destructor
- Destructor is another special member function that is called by the compiler when the scope of the object ends.
- It deallocates all the memory previously used by the object of the class so that there will be no memory leaks.
### Class method
- Class methods – also known as member functions – are functions defined inside a class that operates on the class objects.
- They access the class's data members and other member functions and define the behavior or actions that objects of the class can perform.
- Class methods are declared and defined within the class definition itself or defined outside the class definition.

</details>
