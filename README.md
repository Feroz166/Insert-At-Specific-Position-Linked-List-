

<blr>

  ~Author Mohammed Feroz

  <blr>
    
# Insert-At-Specific-Position-Linked-List-
A linked list is a linear data structure where elements (called nodes) are connected using pointers. Each node contains:  Data Reference (pointer) to the next node

#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node* next;
};

void insertAtSpecific(struct node** head, int pos, int val) {
    struct node* newnode = (struct node*)malloc(sizeof(struct node));
    newnode->data = val;
    newnode->next = NULL;

    if (pos == 1) {
        newnode->next = *head;
        *head = newnode;
        return;
    }

    struct node* temp = *head;
    for (int i = 1; i < pos - 1 && temp; i++) {
        temp = temp->next;
    }

    if (!temp)
        return;

    newnode->next = temp->next;
    temp->next = newnode;
}

void display(struct node* head) {
    while (head) {
        printf("%d->", head->data);
        head = head->next;
    }
    printf("NULL\n");
}

int main() {
    int n, pos, val;
    struct node* head = NULL;

    scanf("%d", &n);
    for (int i = 1; i <= n; i++) {
        scanf("%d", &val);
        insertAtSpecific(&head, i, val); // insert at the end
    }

    scanf("%d %d", &pos, &val);
    insertAtSpecific(&head, pos, val);

    display(head);

    return 0;
}


