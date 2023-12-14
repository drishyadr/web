#include <stdio.h>
#include <stdlib.h>

struct node
{
	int data;
	struct node*left;
	struct node*right;
}*root;

struct node *create()
{
	struct node *newnode;
	int x;

	printf("Enter the data or Enter -1: ");
	scanf("%d",&x);

	if(x == -1)
		return NULL;

	newnode = (struct node*)malloc(sizeof(struct node));

	newnode->data = x;

	printf("left child of (%d)---> ",x);
	newnode->left = create();

	printf("right child of (%d)--> ",x);
	newnode->right = create();

	return newnode;
}

void inorder(struct node *ptr)
{
	if(ptr!=NULL)
	{
		inorder(ptr->left);
		printf("%d  ",ptr->data);
		inorder(ptr->right);
	}
}

void preorder(struct node *ptr)
{
	if(ptr!=NULL)
	{
		printf("%d  ",ptr->data);
		preorder(ptr->left);
		preorder(ptr->right);
	}
}

void postorder(struct node *ptr)
{
	if(ptr!=NULL)
	{
		postorder(ptr->left);
		postorder(ptr->right);
		printf("%d  ",ptr->data);
	}
}

void main()
{
	root = create();
	printf("\nINORDER   :");
	inorder(root);
	printf("\nPREORDER  :");
	preorder(root);
	printf("\nPOSTORDER :");
	postorder(root);
	printf("\n");
}
