# 0x1D. C - Binary trees

## Resources

<b>Read or watch:</b>

* [Binary tree (note the first line: Not to be confused with B-tree.)](https://en.wikipedia.org/wiki/Binary_tree)
* [Data Structure and Algorithms - Tree](https://www.tutorialspoint.com/data_structures_algorithms/tree_data_structure.htm)
* [Tree Traversal](https://www.programiz.com/dsa/tree-traversal)
* [Binary Search Tree](https://en.wikipedia.org/wiki/Binary_search_tree)
* [Data structures: Binary Tree](https://www.youtube.com/watch?v=H5JubkIy_p8)


## General
* What is a binary tree
* What is the difference between a binary tree and a Binary Search Tree
* What is the possible gain in terms of time complexity compared to linked lists
* What are the depth, the height, the size of a binary tree
* What are the different traversal methods to go through a binary tree
* What is a complete, a full, a perfect, a balanced binary tree

## Data structures

<b>Basic Binary Tree</b>
```
/**
 * struct binary_tree_s - Binary tree node
 *
 * @n: Integer stored in the node
 * @parent: Pointer to the parent node
 * @left: Pointer to the left child node
 * @right: Pointer to the right child node
 */
struct binary_tree_s
{
    int n;
    struct binary_tree_s *parent;
    struct binary_tree_s *left;
    struct binary_tree_s *right;
};

typedef struct binary_tree_s binary_tree_t;
```
## Binary Search Tree
```
typedef struct binary_tree_s bst_t;
```
## AVL Tree
```
typedef struct binary_tree_s avl_t;
```
## Max Binary Heap
```
typedef struct binary_tree_s heap_t;
```

## Print function

To match the examples in the tasks, you are given [this function](https://github.com/alx-tools/0x1C.c)

This function is used only for visualization purposes. You don’t have to push it to your repo. It may not be used during the correction

##  Tasks

### 0. New node

#### Files: [0-binary_tree_node.c](0-binary_tree_node.c) | [0-main.c](0-main.c)

<b>Write a function that creates a binary tree node</b>

* Prototype: `binary_tree_t *binary_tree_node(binary_tree_t *parent, int value);`
* Where `parent` is a pointer to the parent node of the node to create
* And `value` is the value to put in the new node
* When created, a node does not have any child
* Your function must return a pointer to the new node, or `NULL` on failure

```
alex@/tmp/binary_trees$ cat 0-main.c 
#include <stdlib.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);

    root->left = binary_tree_node(root, 12);
    root->left->left = binary_tree_node(root->left, 6);
    root->left->right = binary_tree_node(root->left, 16);

    root->right = binary_tree_node(root, 402);
    root->right->left = binary_tree_node(root->right, 256);
    root->right->right = binary_tree_node(root->right, 512);

    binary_tree_print(root);
    return (0);
}
alex@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 0-main.c 0-binary_tree_node.c -o 0-node
alex@/tmp/binary_trees$ ./0-node
       .-------(098)-------.
  .--(012)--.         .--(402)--.
(006)     (016)     (256)     (512)
alex@/tmp/binary_trees$
```

### 1. Insert left

#### Files: [1-binary_tree_insert_left.c](1-binary_tree_insert_left.c) | [1-main.c](1-main.c)

<b>Write a function that inserts a node as the left-child of another node</b>

* Prototype: `binary_tree_t *binary_tree_insert_left(binary_tree_t *parent, int value);`
* Where parent is a pointer to the node to insert the left-child in
* And `value` is the value to store in the new node
* Your function must return a pointer to the created node, or `NULL` on failure or if `parent` is `NULL`
* If `parent` already has a left-child, the new node must take its place, and the old left-child must be set as the left-child of the new node.
```
alex@/tmp/binary_trees$ cat 2-main.c 
#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_print(root);
    printf("\n");
    binary_tree_insert_right(root->left, 54);
    binary_tree_insert_right(root, 128);
    binary_tree_print(root);
    return (0);
}
alex@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 2-main.c 2-binary_tree_insert_right.c 0-binary_tree_node.c -o 2-right
alex@/tmp/binary_trees$ ./2-right 
  .--(098)--.
(012)     (402)

  .-------(098)--.
(012)--.       (128)--.
     (054)          (402)
alex@/tmp/binary_trees$
```

