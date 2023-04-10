# C - Bit manipulation :file_folder:
## Tests :heavy_check_mark:
* [tests](./tests): Folder of test files
----
## Header File
* [main.h](./main.h): The Prototypes
## The table below illustrates files and it's corresponing prototype.
| File                   | Prototype                                                           |
| ---------------------- | ------------------------------------------------------------------- |
| `0-binary_to_uint.c`   | `unsigned int binary_to_uint(const char *b);`                       |
| `1-print_binary.c`     | `void print_binary(unsigned long int n);`                           |
| `2-get_bit.c`          | `int get_bit(unsigned long int n, unsigned int index);`             |
| `3-set_bit.c`          | `int set_bit(unsigned long int *n, unsigned int index);`            |
| `4-clear_bit.c`        | `int clear_bit(unsigned long int *n, unsigned int index);`          |
| `5-flip_bits.c`        | `unsigned int flip_bits(unsigned long int n, unsigned long int m);` |
| `100-get_endianness.c` | `int get_endianness(void);`                                         |
## Tasks :page_with_curl:
* `0. 0`
* [0-binary_to_uint.c](./0-binary_to_uint.c): C function that converts a binary number
to an `unsigned int`.
* The parameter `b` is a pointer to a string of `0` and `1` characters.
* If `b` is `NULL` or there are one or more characters in `b` that are
not `0` or `1` - returns `0`.
* Otherwise - returns the converted number.
* `1. 1`
* [1-print_binary.c](./1-print_binary.c): C function that prints the binary representation
of a number.
* `2. 10`
* [2-get_bit.c](./2-get_bit.c): C function that returns the value of a bit at a
given index.
* Indices start at `0`.
* If an error occurs - returns `-1`.
* Otherwise - returns the value of the bit at the given index.
* `3. 11`
* [3-set_bit.c](./3-set_bit.c): C function that sets the value of a bit at a given index
to `1`.
* If an error occurs - returns `-1`.
* Otherwise - returns `1`.
* `4. 100`
* [4-clear_bit.c](./4-clear_bit.c): C function that sets the value of a bit at
a given index to `0`.
* If an error occurs - returns `-1`.
* Otherwise - returns `1`.
* `5. 101`
* [5-flip_bits.c](./5-flip_bits.c): C function that returns the number of bits needed
to be flipped to get from one number to another.
* `6. Endianness`
* [100-get_endianness.c](./100-get_endianness.c): C function that checks the endianness.
* If big-endian - returns `0`.
* If little-endian - returns `1`.
* `7. Crackme3`
* [101-password](./101-password): File containing the password for the crackme3 executable.
===========================================
MAIN.H
#ifndef MAIN_H
#define MAIN_H
unsigned int binary_to_uint(const char *b);
void print_binary(unsigned long int n);
int get_bit(unsigned long int n, unsigned int index);
int set_bit(unsigned long int *n, unsigned int index);
int clear_bit(unsigned long int *n, unsigned int index);
unsigned int flip_bits(unsigned long int n, unsigned long int m);
int _atoi(const char *s);
int _putchar(char c);
int get_endianness(void);
#endif
===================================
0-BINARY_TO_UINT.C CODE
#include "main.h"
/**
* binary_to_uint - converts a binary number to unsigned int
* @b: string containing the binary number
*
* Return: the converted number
*/
unsigned int binary_to_uint(const char *b)
{
int i;
unsigned int dec_val = 0;
if (!b)
return (0);
for (i = 0; b[i]; i++)
{
if (b[i] < '0' || b[i] > '1')
return (0);
dec_val = 2 * dec_val + (b[i] - '0');
}
return (dec_val);
}
=========================================
1-PRINT_BINARY.C CODE
#include "main.h"
/**
* print_binary - prints the binary…
[20:59, 06/04/2023] Tochi: Hey
[23:58, 06/04/2023] Tochi: 0x12. C - Singly linked lists
0x12. C - Singly linked lists
README.md
Project:
0x12. C - Singly linked lists
==========================
lists.h
#ifndef LISTS_H
#define LISTS_H
/**
* struct list_s - singly linked list
* @str: string - (malloc'ed string)
* @len: length of the string
* @next: points to the next node
*
* Description: singly linked list node structure
* for Holberton project
*/
typedef struct list_s
{
char *str;
unsigned int len;
struct list_s *next;
} list_t;
size_t print_list(const list_t *h);
size_t list_len(const list_t *h);
list_t *add_node(list_t **head, const char *str);
list_t *add_node_end(list_t **head, const char *str);
void free_list(list_t *head);
#endif
0-print_list.c
#include <stdio.h>
#include "lists.h"
/**
* print_list - prints all the elements of a linked list
* @h: pointer to the list_t list to print
*
* Return: the number of nodes printed
*/
size_t print_list(const list_t *h)
{
size_t s = 0;
while (h)
{
if (!h->str)
printf("[0] (nil)\n");
else
printf("[%u] %s\n", h->len, h->str);
h = h->next;
s++;
}
return (s);
}
1-list_len.c
#include <stdlib.h>
#include "lists.h"
/**
* list_len - returns the number of elements in a linked list
* @h: pointer to the list_t list
*
* Return: number of elements in h
*/
size_t list_len(const list_t *h)
{
size_t n = 0;
while (h)
{
n++;
h = h->next;
}
return (n);
}
2-add_node.c
#include <stdlib.h>
#include <string.h>
#include "lists.h"
/**
* add_node - adds a new node at the beginning of a linked list
* @head: double pointer to the list_t list
* @str: new string to add in the node
*
* Return: the address of the new element, or NULL if it fails
*/
list_t *add_node(list_t **head, const char *str)
{
list_t *new;
unsigned int len = 0;
while (str[len])
len++;
new = malloc(sizeof(list_t));
if (!new)
return (NULL);
new->str = strdup(str);
new->len = len;
new->next = (*head);
(*head) = new;
return (*head);
}
3-add_node_end.c
#include <stdlib.h>
#include <string.h>
#include "lists.h"
/**
* add_node_end - adds a new node at the end of a linked list
* @head: double pointer to the list_t list
* @str: string to put in the new node
*
* Return: address of the new element, or NULL if it failed
*/
list_t *add_node_end(list_t **head, const char *str)
{
list_t *new;
list_t *temp = *head;
unsigned int len = 0;
while (str[len])
len++;
new = malloc(sizeof(list_t));
if (!new)
return (NULL);
new->str = strdup(str);
new->len = len;
new->next = NULL;
if (*head == NULL)
{
*head = new;
return (new);
}
while (temp->next)
temp = temp->next;
temp->next = new;
return (new);
}
4-free_list.c
#include <stdlib.h>
#include "lists.h"
/**
* free_list - frees a linked list
* @head: list_t list to be freed
*/
void free_list(list_t *head)
{
list_t *temp;
while (head)
{
temp = head->next;
free(head->str);
free(head);
head = temp;
}
}
100-first.c
#include <stdio.h>
void first(void) _attribute_ ((constructor));
/**
* first - prints a sentence before the main
* function is executed
*/
void first(void)
{
printf("You're beat! and yet, you must allow,\n");
printf("I bore my house upon my back!\n");
}
101-hello_holberton.asm
global    main
extern    printf
main:
mov   edi, format
xor   eax, eax
call  printf
mov         eax, 0
ret
format: db `Hello, Holberton\n`,0

