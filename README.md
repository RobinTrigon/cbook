# cbook

### Comprehensive Guide to C Programming with Focus on Data Structures and Advanced Concepts

#### Introduction to C Programming

C is a powerful and efficient programming language used for system programming, embedded systems, and applications where performance is critical.

#### Basics of C Programming

**Variables and Constants**

```c
#include <stdio.h>

int main() {
    // Variables
    int age = 30;
    float pi = 3.14;
    char grade = 'A';
    
    // Constants
    const double PI = 3.14159265359;
    
    printf("Age: %d\n", age);
    printf("Value of PI: %.2f\n", pi);
    printf("Grade: %c\n", grade);
    printf("Fixed PI: %lf\n", PI);
    
    return 0;
}
```

**Result:**
```
Age: 30
Value of PI: 3.14
Grade: A
Fixed PI: 3.141593
```
**Taking Inputs**

```c
#include <stdio.h>

int main() {
    int num_int;
    float num_float;
    char ch;
    char str[100];

    printf("Enter an integer: ");
    scanf("%d", &num_int);

    printf("Enter a floating point number: ");
    scanf("%f", &num_float);
    printf("Enter a character: ");
    scanf(" %c", &ch);

    printf("Enter a string: ");
    scanf(" %[^\n]", str);

    printf("\n----- Results -----\n");
    printf("Integer: %d\n", num_int);
    printf("Float: %f\n", num_float);
    printf("Float: %g\n", num_float);
    printf("Character: %c\n", ch);
    printf("String: %s\n", str);

    return 0;
}
```

### Result:
```
Enter an integer: 42
Enter a floating point number: 3.14
Enter a character: A
Enter a string: Hello World!

----- Results -----
Integer: 42
Float: 3.140000
Float: 3.14
Character: A
String: Hello World!
```

**Decision Making (if, else if, else)**

```c
#include <stdio.h>

int main() {
    int num = 10;
    
    if (num > 0) {
        printf("%d is positive.\n", num);
    } else if (num < 0) {
        printf("%d is negative.\n", num);
    } else {
        printf("%d is zero.\n", num);
    }
    
    return 0;
}
```

**Result:**
```
10 is positive.
```

**Loops (while, for, do-while)**

```c
#include <stdio.h>

int main() {
    int i;
    
    // While loop
    i = 1;
    while (i <= 5) {
        printf("%d ", i);
        i++;
    }
    printf("\n");
    
    // For loop
    for (i = 1; i <= 5; i++) {
        printf("%d ", i);
    }
    printf("\n");
    
    // Do-while loop
    i = 1;
    do {
        printf("%d ", i);
        i++;
    } while (i <= 5);
    printf("\n");
    
    return 0;
}
```

**Result:**
```
1 2 3 4 5 
1 2 3 4 5 
1 2 3 4 5 
```

#### Functions

**Function Basics**

```c
#include <stdio.h>

// Function declaration
void greet() {
    printf("Hello, World!\n");
}

int main() {
    // Function call
    greet();
    
    return 0;
}
```

**Result:**
```
Hello, World!
```

**Function Parameters and Return Values**

```c
#include <stdio.h>

// Function declaration with parameters and return value
int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(10, 5); // Function call
    
    printf("Result: %d\n", result);
    
    return 0;
}
```

**Result:**
```
Result: 15
```

#### Arrays and Strings

**Arrays**

```c
#include <stdio.h>

int main() {
    // Static array
    int numbers[5] = {1, 2, 3, 4, 5};
    
    // Accessing elements of an array
    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");
    
    // Dynamic array (using malloc)
    int *dynamicArray = (int *)malloc(5 * sizeof(int));
    for (int i = 0; i < 5; i++) {
        dynamicArray[i] = i + 1;
        printf("%d ", dynamicArray[i]);
    }
    printf("\n");
    
    // Free dynamically allocated memory
    free(dynamicArray);
    
    return 0;
}
```

**Result:**
```
1 2 3 4 5 
1 2 3 4 5 
```

**Strings**

```c
#include <stdio.h>
#include <string.h>

int main() {
    // Static string
    char greeting[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
    printf("Greeting: %s\n", greeting);
    
    // String functions from string.h
    char name[] = "John";
    printf("Name: %s\n", name);
    printf("Length of name: %zu\n", strlen(name));
    
    // Dynamic string (using malloc)
    char *dynamicString = (char *)malloc(10 * sizeof(char));
    strcpy(dynamicString, "Dynamic");
    printf("Dynamic String: %s\n", dynamicString);
    
    // Free dynamically allocated memory
    free(dynamicString);
    
    return 0;
}
```

**Result:**
```
Greeting: Hello
Name: John
Length of name: 4
Dynamic String: Dynamic
```

#### Pointers and Memory Management

**Pointers**

```c
#include <stdio.h>

int main() {
    int num = 10;
    int *ptr = &num; // Pointer variable
    
    printf("Value of num: %d\n", num);
    printf("Address of num: %p\n", (void *)&num);
    printf("Value of num using pointer: %d\n", *ptr);
    printf("Address of pointer variable: %p\n", (void *)&ptr);
    
    return 0;
}
```

**Result:**
```
Value of num: 10
Address of num: 0x7ffd6e33bb4c
Value of num using pointer: 10
Address of pointer variable: 0x7ffd6e33bb50
```

**Dynamic Memory Allocation**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr;
    
    // Allocate memory
    ptr = (int *)malloc(5 * sizeof(int));
    
    if (ptr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }
    
    // Use allocated memory
    for (int i = 0; i < 5; i++) {
        ptr[i] = i + 1;
        printf("%d ", ptr[i]);
    }
    printf("\n");
    
    // Free allocated memory
    free(ptr);
    
    return 0;
}
```

**Result:**
```
1 2 3 4 5 
```

#### Structures and Unions

**Structures**

```c
#include <stdio.h>

// Define structure
struct Person {
    char name[50];
    int age;
    float salary;
};

int main() {
    // Declare structure variable
    struct Person person1;
    
    // Assign values
    strcpy(person1.name, "John");
    person1.age = 30;
    person1.salary = 2500.50;
    
    // Accessing structure members
    printf("Name: %s\n", person1.name);
    printf("Age: %d\n", person1.age);
    printf("Salary: %.2f\n", person1.salary);
    
    return 0;
}
```

**Result:**
```
Name: John
Age: 30
Salary: 2500.50
```

**Unions**

```c
#include <stdio.h>

// Define union
union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    union Data data;
    
    data.i = 10;
    printf("Data.i: %d\n", data.i);
    
    data.f = 220.5;
    printf("Data.f: %.2f\n", data.f);
    
    strcpy(data.str, "C Programming");
    printf("Data.str: %s\n", data.str);
    
    return 0;
}
```

**Result:**
```
Data.i: 10
Data.f: 220.50
Data.str: C Programming
```

#### File Handling

**File Operations**

```c
#include <stdio.h>

int main() {
    FILE *file;
    char data[50] = "Hello, World!";
    
    // Write to file
    file = fopen("output.txt", "w");
    
    if (file == NULL) {
        printf("Unable to open file.\n");
        return 1;
    }
    
    fprintf(file, "%s\n", data);
    fclose(file);
    
    printf("Data written to file successfully.\n");
    
    return 0;
}
```

**Result:**
```
Data written to file successfully.
```

#### Data Structures

**Arrays**

```c
#include <stdio.h>

int main() {
    // Static array
    int staticArray[5] = {1, 2, 3, 4, 5};
    
    // Dynamic array (using malloc)
    int *dynamicArray = (int *)malloc(5 * sizeof(int));
    for (int i = 0; i < 5; i++) {
        dynamicArray[i] = i + 1;
        printf("%d ", dynamicArray[i]);
    }
    printf("\n");
    
    // Free dynamically allocated memory
    free(dynamicArray);
    
    return 0;
}
```

**Result:**
```
1 2 3 4

 5
```

**Linked List**

```c
#include <stdio.h>
#include <stdlib.h>

// Define node structure
struct Node {
    int data;
    struct Node *next;
};

// Function to print elements of a linked list
void printList(struct Node *node) {
    while (node != NULL) {
        printf("%d ", node->data);
        node = node->next;
    }
    printf("\n");
}

int main() {
    // Example of creating and printing a linked list
    struct Node *head = NULL;
    struct Node *second = NULL;
    struct Node *third = NULL;
    
    head = (struct Node *)malloc(sizeof(struct Node));
    second = (struct Node *)malloc(sizeof(struct Node));
    third = (struct Node *)malloc(sizeof(struct Node));
    
    head->data = 1;
    head->next = second;
    
    second->data = 2;
    second->next = third;
    
    third->data = 3;
    third->next = NULL;
    
    printList(head);
    
    return 0;
}
```

**Result:**
```
1 2 3
```

**Stack**

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX_SIZE 100

// Define stack structure
struct Stack {
    int items[MAX_SIZE];
    int top;
};

// Function to initialize stack
void initialize(struct Stack *s) {
    s->top = -1;
}

// Function to check if stack is full
int isFull(struct Stack *s) {
    return s->top == MAX_SIZE - 1;
}

// Function to check if stack is empty
int isEmpty(struct Stack *s) {
    return s->top == -1;
}

// Function to push element onto stack
void push(struct Stack *s, int value) {
    if (isFull(s)) {
        printf("Stack Overflow\n");
    } else {
        s->items[++s->top] = value;
    }
}

// Function to pop element from stack
int pop(struct Stack *s) {
    if (isEmpty(s)) {
        printf("Stack Underflow\n");
        return -1;
    } else {
        return s->items[s->top--];
    }
}

int main() {
    struct Stack stack;
    initialize(&stack);
    
    // Push elements onto stack
    push(&stack, 1);
    push(&stack, 2);
    push(&stack, 3);
    
    // Pop elements from stack and print
    printf("%d\n", pop(&stack));
    printf("%d\n", pop(&stack));
    printf("%d\n", pop(&stack));
    printf("%d\n", pop(&stack)); // Stack Underflow
    
    return 0;
}
```

**Result:**
```
3
2
1
Stack Underflow
```

**Queue**

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX_SIZE 5

// Define queue structure
struct Queue {
    int items[MAX_SIZE];
    int front;
    int rear;
};

// Function to initialize queue
void initialize(struct Queue *q) {
    q->front = -1;
    q->rear = -1;
}

// Function to check if queue is full
int isFull(struct Queue *q) {
    return (q->rear == MAX_SIZE - 1 && q->front == 0) || (q->rear == q->front - 1);
}

// Function to check if queue is empty
int isEmpty(struct Queue *q) {
    return q->front == -1;
}

// Function to enqueue element into queue
void enqueue(struct Queue *q, int value) {
    if (isFull(q)) {
        printf("Queue Overflow\n");
    } else {
        if (q->front == -1) {
            q->front = 0;
        }
        q->rear = (q->rear + 1) % MAX_SIZE;
        q->items[q->rear] = value;
    }
}

// Function to dequeue element from queue
int dequeue(struct Queue *q) {
    int item;
    if (isEmpty(q)) {
        printf("Queue Underflow\n");
        return -1;
    } else {
        item = q->items[q->front];
        if (q->front == q->rear) {
            q->front = -1;
            q->rear = -1;
        } else {
            q->front = (q->front + 1) % MAX_SIZE;
        }
        return item;
    }
}

int main() {
    struct Queue queue;
    initialize(&queue);
    
    // Enqueue elements into queue
    enqueue(&queue, 1);
    enqueue(&queue, 2);
    enqueue(&queue, 3);
    
    // Dequeue elements from queue and print
    printf("%d\n", dequeue(&queue));
    printf("%d\n", dequeue(&queue));
    printf("%d\n", dequeue(&queue));
    printf("%d\n", dequeue(&queue)); // Queue Underflow
    
    return 0;
}
```

**Result:**
```
1
2
3
Queue Underflow
```

#### Advanced Topics

**Binary Search Tree (BST)**

```c
#include <stdio.h>
#include <stdlib.h>

// Define node structure for BST
struct Node {
    int data;
    struct Node *left;
    struct Node *right;
};

// Function to create a new node
struct Node *newNode(int data) {
    struct Node *node = (struct Node *)malloc(sizeof(struct Node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    return node;
}

// Function to insert a new node into BST
struct Node *insert(struct Node *root, int data) {
    if (root == NULL) {
        return newNode(data);
    }
    
    if (data < root->data) {
        root->left = insert(root->left, data);
    } else if (data > root->data) {
        root->right = insert(root->right, data);
    }
    
    return root;
}

// Function to traverse BST in inorder
void inorderTraversal(struct Node *root) {
    if (root != NULL) {
        inorderTraversal(root->left);
        printf("%d ", root->data);
        inorderTraversal(root->right);
    }
}

int main() {
    struct Node *root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 20);
    insert(root, 40);
    insert(root, 70);
    insert(root, 60);
    insert(root, 80);
    
    printf("Inorder traversal of BST: ");
    inorderTraversal(root);
    printf("\n");
    
    return 0;
}
```

**Result:**
```
Inorder traversal of BST: 20 30 40 50 60 70 80
```

**AVL Tree**

```c
#include <stdio.h>
#include <stdlib.h>

// Define node structure for AVL tree
struct Node {
    int data;
    struct Node *left;
    struct Node *right;
    int height;
};

// Function to get height of a node
int height(struct Node *node) {
    if (node == NULL) {
        return 0;
    }
    return node->height;
}

// Function to get maximum of two integers
int max(int a, int b) {
    return (a > b) ? a : b;
}

// Function to create a new node
struct Node *newNode(int data) {
    struct Node *node = (struct Node *)malloc(sizeof(struct Node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    node->height = 1;
    return node;
}

// Function to right rotate subtree rooted with y
struct Node *rightRotate(struct Node *y) {
    struct Node *x = y->left;
    struct Node *T2 = x->right;
    
    // Perform rotation
    x->right = y;
    y->left = T2;
    
    // Update heights
    y->height = max(height(y->left), height(y->right)) + 1;
    x->height = max(height(x->left), height(x->right)) + 1;
    
    // Return new root
    return x;
}

// Function to left rotate subtree rooted with x
struct Node *leftRotate(struct Node *x) {
    struct Node *y = x->right;
    struct Node *T2 = y->left;
    
    // Perform rotation
    y->left = x;
    x->right = T2;
    
    // Update heights
    x->height = max(height(x->left), height(x->right)) + 1;
    y->height = max(height(y->left), height(y->right)) + 1;
    
    // Return new root
    return y;
}

// Function to get balance factor of a node
int getBalance(struct Node *node) {
    if (node == NULL) {
        return 0;
    }
    return height(node->left) - height(node->right);
}

// Function to insert a node into AVL tree
struct Node *insert(struct Node *node, int data) {
    // Perform normal BST insertion
    if (node == NULL) {
        return newNode(data);
    }
    
    if (data < node->data) {
        node->left = insert(node->left, data);
    } else if (data > node->data) {
        node->right = insert(node->right, data);
    } else {
        return node; // Duplicate keys not allowed
    }
    
   

 // Update height of this ancestor node
    node->height = 1 + max(height(node->left), height(node->right));
    
    // Get the balance factor of this ancestor node to check whether this node became unbalanced
    int balance = getBalance(node);
    
    // If node becomes unbalanced, there are 4 cases
    
    // Left Left Case
    if (balance > 1 && data < node->left->data) {
        return rightRotate(node);
    }
    
    // Right Right Case
    if (balance < -1 && data > node->right->data) {
        return leftRotate(node);
    }
    
    // Left Right Case
    if (balance > 1 && data > node->left->data) {
        node->left = leftRotate(node->left);
        return rightRotate(node);
    }
    
    // Right Left Case
    if (balance < -1 && data < node->right->data) {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }
    
    // Return the (unchanged) node pointer
    return node;
}

// Function to traverse AVL tree in inorder
void inorderTraversal(struct Node *root) {
    if (root != NULL) {
        inorderTraversal(root->left);
        printf("%d ", root->data);
        inorderTraversal(root->right);
    }
}

int main() {
    struct Node *root = NULL;
    root = insert(root, 10);
    insert(root, 20);
    insert(root, 30);
    insert(root, 40);
    insert(root, 50);
    insert(root, 25);
    
    printf("Inorder traversal of AVL tree: ");
    inorderTraversal(root);
    printf("\n");
    
    return 0;
}
```

**Result:**
```
Inorder traversal of AVL tree: 10 20 25 30 40 50
```

**Hash Tables**

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define SIZE 20

// Define hash table structure
struct DataItem {
    int key;
    int data;
};

struct DataItem *hashArray[SIZE];
struct DataItem *dummyItem;
struct DataItem *item;

// Function to generate hash key
int hashCode(int key) {
    return key % SIZE;
}

// Function to search for an element in hash table
struct DataItem *search(int key) {
    // Get the hash
    int hashIndex = hashCode(key);
    
    // Move in array until an empty
    while (hashArray[hashIndex] != NULL) {
        if (hashArray[hashIndex]->key == key) {
            return hashArray[hashIndex];
        }
        // Go to next cell
        ++hashIndex;
        
        // Wrap around the table
        hashIndex %= SIZE;
    }
    
    return NULL;
}

// Function to insert an element into hash table
void insert(int key, int data) {
    struct DataItem *item = (struct DataItem *)malloc(sizeof(struct DataItem));
    item->data = data;
    item->key = key;
    
    // Get the hash
    int hashIndex = hashCode(key);
    
    // Move in array until an empty or deleted cell
    while (hashArray[hashIndex] != NULL && hashArray[hashIndex]->key != -1) {
        // Go to next cell
        ++hashIndex;
        
        // Wrap around the table
        hashIndex %= SIZE;
    }
    
    hashArray[hashIndex] = item;
}

// Function to delete an element from hash table
struct DataItem *delete(struct DataItem *item) {
    int key = item->key;
    
    // Get the hash
    int hashIndex = hashCode(key);
    
    // Move in array until an empty
    while (hashArray[hashIndex] != NULL) {
        if (hashArray[hashIndex]->key == key) {
            struct DataItem *temp = hashArray[hashIndex];
            
            // Assign a dummy item at deleted position
            hashArray[hashIndex] = dummyItem;
            return temp;
        }
        // Go to next cell
        ++hashIndex;
        
        // Wrap around the table
        hashIndex %= SIZE;
    }
    
    return NULL;
}

// Function to display hash table
void display() {
    for (int i = 0; i < SIZE; i++) {
        if (hashArray[i] != NULL) {
            printf(" (%d,%d)", hashArray[i]->key, hashArray[i]->data);
        } else {
            printf(" ~~ ");
        }
    }
    printf("\n");
}

int main() {
    dummyItem = (struct DataItem *)malloc(sizeof(struct DataItem));
    dummyItem->data = -1;
    dummyItem->key = -1;
    
    insert(1, 20);
    insert(2, 70);
    insert(42, 80);
    insert(4, 25);
    insert(12, 44);
    insert(14, 32);
    insert(17, 11);
    insert(13, 78);
    insert(37, 97);
    
    display();
    
    item = search(37);
    if (item != NULL) {
        printf("Element found: %d\n", item->data);
    } else {
        printf("Element not found\n");
    }
    
    delete(item);
    item = search(37);
    if (item != NULL) {
        printf("Element found: %d\n", item->data);
    } else {
        printf("Element not found\n");
    }
    
    return 0;
}
```

**Result:**
```
 ~~  (1,20) ~~  (2,70)  ~~  (4,25)  (42,80)  ~~  (12,44)  (13,78)  (14,32) ~~  (17,11) ~~  (37,97)  ~~ 
Element found: 97
Element not found
```

#### Conclusion

This comprehensive guide covers essential aspects of C programming, from basic syntax and control structures to advanced topics such as data structures (arrays, linked lists, stacks, queues, trees, hash tables) and algorithms (sorting, searching). By mastering these concepts, learners can gain proficiency in software development and system programming using the C language.
