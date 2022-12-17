#include <stdio.h>
#include <stdlib.h>
struct stack
{
    int size;
    int top;
    int *arr;
};
int isempty(struct stack *ptr)
{
    if (ptr->top == -1)
    {
        return 1;
    }
    else
    {
        return 0;
    }
}
int isfull(struct stack *ptr)
{
    if (ptr->top == ptr->size - 1)
    {
        return 1;
    }
    else
    {
        return 0;
    }
}
void push(struct stack *ptr)
{
    int val;
    printf("enter element to insert:\n");
    scanf("%d", &val);
    if (isfull(ptr))
    {
        printf("over flow cant insert %d\n", val);
    }
    else
    {
        ptr->top++;
        ptr->arr[ptr->top] = val;
        printf("\nelement=%d inserted into stack:\n", val);
    }
}
int pop(struct stack *ptr)
{
    if (isempty(ptr))
    {
        printf("stack is already empty,we can't pop:\n");
        return -1;
    }
    else
    {
        int val = ptr->arr[ptr->top];
        ptr->top--;
        printf("\nelement=%d poped from stack:\n", val);
        return val;
    }
}
int peek(struct stack *ptr)
{
    if (isempty(ptr))
    {
        printf("stack is empty,we can't peek:\n");
        return -1;
    }
    else
    {
        printf("The value stored at top of stack is %d\n",ptr->arr[ptr->top]);
    }
}
void dispay(struct stack *ptr)
{
    int val = ptr->arr[ptr->top];
    printf("\nelement in stack are:\n");
    for (int i = 0; i <= ptr->top; i++)
    {
        printf("%d at %d\n",i, ptr->arr[i]);
    }
}
int main()
{
    int s;
    struct stack *sp = (struct stack *)malloc(sizeof(struct stack));
    printf("enter the size of stack\n");
    scanf("%d", &s);
    sp->size = s;
    sp->top = -1;
    sp->arr = (int *)malloc(sp->size * sizeof(int));
    printf("stack has been created\n");
    while (1)
    {
        int choice;
        printf("\nenter your choice\n");
        printf("1.push\n");
        printf("2.pop\n");
        printf("3.peek\n");
        printf("4.display\n");
        printf("5.exit\n");
        scanf("%d", &choice);
        switch (choice)
        {
        case 1:
            push(sp);
            dispay(sp);
            break;
        case 2:
            pop(sp);
            dispay(sp);
            break;
            case 3:
            peek(sp);
            break;
        case 4:
            dispay(sp);
            break;
        case 5:
            exit(0);
            break;

        default:
            break;
        }
    }

    return 0;
    
}
