# Node-single-linked-
explanation of readings 
reference of codementor (Author's Bio
Kamal Choudhary is a tech geek who writes about c++ programming tutorials on C++ Beginner. He is a student of computer science in University of Gujrat, pakistan. He loves to write about computer programming. You can find his full bio here. Follow him on Twitter at @ikamalchoudhary)

A linked list is a data structure that can store an indefinite amount of items. These items are connected using pointers in a sequential manner.

There are two types of linked list; singly-linked list, and doubly-linked list. In a singly-linked list, every element contains some data and a link to the next element. On the other hand, every node in a doubly-linked list contains some data, a link to the next node and a link to the previous node.

The elements of a linked list are called the nodes. A node has two fields i.e. data and next. The data field contains the data being stored in that specific node. It cannot just be a single variable. There may be many variables presenting the data section of a node. The next field contains the address of the next node. So this is the place where the link between nodes is established.

singly linked list

No matter how many nodes are present in the linked list, the very first node is called head and the last node is called the tail. If there is just one node created then it is called both head and tail.

singly linked list

Implementation of Linked List Using C++
As linked list consists of nodes, we need to declare a structure which defines a single node. Our structure should have at least one variable for data section and a pointer for the next node. In C++, our code would look like this:

  struct node
  {
    int data;
    node *next;
  };	
  
Creation of Linked List Using C++
Now, we need a class which will contain the functions to handle the nodes. This class should have two important pointers, i.e. head and tail. The constructer will make them NULL to avoid any garbage value.

  class list
  {
    Private:
    node *head, *tail;
    public:
    list()
    {
      head=NULL;
      tail=NULL;
    }
  };	
Now, we will write a function for the node creation. The process of creating node is very simple. We need a pointer of a node type (which we defined) and we will insert the value in its data field. The next field of node would be declared as NULL as it would be the last node of linked list.

Now, the function will have a very special case that we want to know what would happen if the linked list is still empty? We will have to check it. Do you remember that the head points to the first node? It means if the head is equal to NULL then we can conclude that the linked list is empty.

I have also told you before that if there is just one node (which we are going to create) in linked lists, then it is called both head and tail.

And if a linked list is created already, then we would insert this node at the end of the linked list. We know that the last node is called a tail. So we are going to create this newly created node next to a tail node.

The creation of a new node at the end of linked list has 2 steps:

Linking the newly created node with tail node. Means passing the address of a new node to the next pointer of a tail node.
The tail pointer should always point to the last node. So we will make our tail pointer equal to a new node.
singly linked list

The C++ code for the creation of new a node would like this:

  void createnode(int value)
    {
      node *temp=new node;
      temp->data=value;
      temp->next=NULL;
      if(head==NULL)
      {
        head=temp;
        tail=temp;
        temp=NULL;
      }
      else
      {	
        tail->next=temp;
        tail=temp;
      }
    }
Displaying Linked List Using C++
Now we have a working linked list which allows creating nodes. If we want to see that what is placed in our linked list then we will have to make a display function. The logic behind this function is that we make a temporary node and pass the address of the head node to it. Now we want to print all the nodes on the screen. So we need a loop which runs as many times as nodes exist. Every node contains the address of the next node so the temporary node walks through the whole linked list. If the temporary node becomes equal to NULL then the loop would be terminated.

singly linked list

The code for displaying nodes of linked list is given below:

  void display()
  {
    node *temp=new node;
    temp=head;
    while(temp!=NULL)
    {
      cout<<temp->data<<"\t";
      temp=temp->next;
    }
  } 
Both createnode() and display() functions would be written under public section of class.

The basic framework of a singly-linked list is ready. Now it is the time to perform some other operations on the list. Basically, two operations are performed on linked lists:

Insertion
Deletion
Insertion
Inserting a new node in the linked list is called insertion.

A new node is created and inserted in the linked list.

There are three cases considered while inserting a node:

Insertion at the start
Insertion at the end
Insertion at a particular position
Insertion at the Start
Insertion of a new node is quite simple. It is just a 2-step algorithm which is performed to insert a node at the start of a singly linked list.

New node should be connected to the first node, which means the head. This can be achieved by putting the address of the head in the next field of the new node.
New node should be considered as a head. It can be achieved by declaring head equals to a new node.
The diagrammatic demonstration of this process is given below:

singly linked list

The code for this process is:

  void insert_start(int value)
  {
    node *temp=new node;
    temp->data=value;
    temp->next=head;
    head=temp;
  }
Insertion at the End
The insertion of a node at the end of a linked list is the same as we have done in node creation function. If you noticed then, we inserted the newly created node at the end of the linked list. So this process is the same.

Insertion at Particular Position
The insertion of a new node at a particular position is a bit difficult to understand. In this case, we don’t disturb the head and tail nodes. Rather, a new node is inserted between two consecutive nodes. So, these two nodes should be accessible by our code. We call one node as current and the other as previous, and the new node is placed between them. This process is shown in a diagram below:

singly linked list

Now the new node can be inserted between the previous and current node by just performing two steps:

Pass the address of the new node in the next field of the previous node.
Pass the address of the current node in the next field of the new node.
We will access these nodes by asking the user at what position he wants to insert the new node. Now, we will start a loop to reach those specific nodes. We initialized our current node by the head and move through the linked list. At the end, we would find two consecutive nodes.

C++ code for insertion of node would be as follows:

  void insert_position(int pos, int value)
  {
    node *pre=new node;
    node *cur=new node;
    node *temp=new node;
    cur=head;
    for(int i=1;i<pos;i++)
    {
      pre=cur;
      cur=cur->next;
    }
    temp->data=value;
    pre->next=temp;	
    temp->next=cur;
  }
Deletion:
So, you have become familiar with linked list creation. Now, it’s time to do some manipulation on the linked list created. Linked lists provide us the great feature of deleting a node. The process of deletion is also easy to implement. The basic structure is to declare a temporary pointer which points the node to be deleted. Then a little bit of working on links of nodes. There are also three cases in which a node can be deleted:

Deletion at the start
Deletion at the end
Deletion at a particular position
Deletion at the Start
In this case, the first node of the linked list is deleted. I know, you remember that the first node is called the head. So, we are going to delete the head node. The process of deletion includes:

Declare a temp pointer and pass the address of the first node, i.e. head to this pointer.
Declare the second node of the list as head as it will be the first node of linked list after deletion.
Delete the temp node.
singly linked list

The C++ code for this process is given below:

  void delete_first()
  {
    node *temp=new node;
    temp=head;
    head=head->next;
    delete temp;
  }
Deletion at the End
Deletion of the last node is a bit difficult to understand than the first node. In the case of the first node, you just need access to the head and you can delete it. But in the case of the last node, you also need access to the second to the last node of the linked list as you will delete the last node and make the previous node as the tail of linked list.

singly linked list

Our algorithm should be capable of finding a node that comes before the last node. This can be achieved by traversing the linked list. We would make two temporary pointers and let them move through the whole linked list. At the end, the previous node will point to the second to the last node and the current node will point to the last node, i.e. node to be deleted. We would delete this node and make the previous node as the tail.

  void delete_last()
  {
    node *current=new node;
    node *previous=new node;
    current=head;
    while(current->next!=NULL)
    {
      previous=current;
      current=current->next;	
    }
    tail=previous;
    previous->next=NULL;
    delete current;
  }
Deletion at a Particular Position
In linked list, we can delete a specific node. The process of deletion is simple. Here we don’t use the head and tail nodes. We ask the user to input the position of the node to be deleted. After that, we just move two temporary pointers through the linked list until we reach our specific node. Now, we delete our current node and pass the address of the node after it to the previous pointer. This way, the current node is removed from the linked list and the link is established between its previous and next node.

singly linked list

The deletion can be done in C++ by using code given below:

  void delete_position(int pos)
  {
    node *current=new node;
    node *previous=new node;
    current=head;
    for(int i=1;i<pos;i++)
    {
      previous=current;
      current=current->next;
    }
    previous->next=current->next;
  }
I have made a complete project of a linked list for you. It performs all the functions described above. You can download it from this Github. Here is a screenshot of its output:

singly linked list

I hope you liked reading this article. Please consider sharing it on Facebook and Twitter. If you have any question then you can ask me in comments.
