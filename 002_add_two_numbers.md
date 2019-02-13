#### 题目

给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807


#### 解答

````C
#include <stdio.h>
#include <stdlib.h>

struct ListNode
{
    int value;
    struct ListNode *next;
} listNode;

// add tow list
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2)
{
    int sum = 0, carry = 0, k;
    struct ListNode *l3, *prev, *node, *i, *j;
    i = l1;
    j = l2;
    do {
        if(i != NULL && j != NULL) {
            sum = i->value + j->value + carry;
        }else if (i != NULL) {
            sum = i->value + carry;
        }else {
            sum = j->value + carry;
        }
        carry = sum / 10;
        if(carry > 0) {
            sum -= 10;
        }

        node = malloc(sizeof(struct ListNode));
        node->value = sum;
        node->next = NULL;
        if(i == l1) {
            l3 = node; // head node
        }else{
            prev->next = node;
        }
        prev = node;

        if(i != NULL)
            i = i->next;
        if(j != NULL)
            j = j->next;

    }while(i != NULL || j != NULL);

    return l3;
}

// list initialize
struct ListNode* createList(int* nums, int size)
{
    struct ListNode *ln, *prev, *node; 
    int i;

    for(i=0; i<size; i++)
    {
        node = malloc(sizeof(struct ListNode));
        node->value = nums[i];
        node->next = NULL;
        if(i==0) {
            ln = node; // head node
        } else {
            prev->next = node;
        }
        prev = node;
    }

    return ln;

}

// list print
void printList(struct ListNode* l)
{
    struct ListNode* p;
    p = l;
    do {
        printf("value is %d next is %x\t", p->value, p->next);
        p = p->next;
    } while(p != NULL);
    printf("\n");
}

void main()
{
    int arr1[] = {2,4,3}, arr2[] = {5,6,4};
    struct ListNode* num1 = createList(arr1, 3);
    struct ListNode* num2 = createList(arr2, 3);

    printList(num1);
    printList(num2);

    struct ListNode* num3 = addTwoNumbers(num1, num2);
    printList(num3);
}

```
