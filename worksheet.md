Feedback: Please edit your work directyly to github files, avoid uploading unecessary files. You still need to answer 2-3 in the challenge section. You may revise and resubmit by 10/05

# 9/11 Worksheet: ArrayLists and LinkedLists
## Initial due date: *09/18 @11:59pm*

Collaborators:

Answer the below questions, and make sure that you commit to your own branch.
When done, make a pull request and tag @AnhThuongVo.
Respond to my comments by making new commits to the same branch.

## Review
1. In your own words, explain what an ArrayList is. 

2. In your own words, explain what a LinkedList is. How is it different from an ArrayList?

## Exploration

1. In this question, you will recreate the Java code to build an ArrayList. The intention is that, after watching the live-coding videos, you should be able to *independently* think through how an ArrayList works, and to write the code from scratch. I encourage you to do this section of the worksheet *without* referring to the videos.

    You can download the starter code in `MyArrayList.java` and work in Eclipse. I recommend using Github Desktop (or commandline git, if you're comfortable with it) to make updating your repo easier.

    Remember to test and save often. The `main()` in `MyArrayList.java` already has some tests, although you will not pass all of them in this section (resizing the list is left for the Challenge section below). 
a. First, we need to be able to create an MyArrayList. Find the public constructor method. What member variables will it need to set? Add those member variables at the first `FIXME`, above the method declaration.    
_Note_: Java does not allow us to instantiate generic arrays. We can get around this by creating an `Object` array and [casting](https://www.geeksforgeeks.org/class-type-casting-in-java/) it to the generic type. For example: `T[] arr = (T[]) new Object [len];`  
b. Fill in the missing code inside the constructor, making sure to set the member variables you just added.  
c. This is an easy one - we should be able to quickly check the current size of our MyArrayList. Fix the `size()` method to return the current actual size.  
d. Now that we can create an MyArrayList and check its size, let's start putting elements in there. Fill in the `add()` method, which adds a given element to the end of an MyArrayList. You do *not* need to worry about resizing for now; that is left for the Challenge section below.  
e. Once we have put a few variables inside our MyArrayList, we should be able view them. Fix the` get()` method, which takes an index and returns the element that is at index in the MyArrayList.

2. In this question, you will recreate the Java code to build a LinkedList. The intention is that, after watching the live-coding videos, you should be able to *independently* think through how a LinkedList works, and to write the code from scratch. I encourage you to do this section of the worksheet *without* referring to the videos.

    You can download the starter code in `MyLinkedList.java` and work in Eclipse. I recommend using Github Desktop (or commandline git, if you're comfortable with it) to make updating your repo easier.        
a. First, we need to create the inner Node class. What member variables does it need? What information is stored in each of these member variables? Write the code for these member variables, and initialize them in the Node constructor.  
b. What are the member variables of the MyLinkedList class? What information is stored in each of these member variables? What should they be initialized to? Write the code for these member variables, and initialize them in the MyLinkedList constructor. Consider where the `head` and `tail` pointers, in particular, should point.   
c. Another easy one - fill out the code for `size()`, which should return the current number of elements in our MyLinkedList.  
d. For a singly-linked list, there are two cases we have to think about for `add()`. What are those cases? What should be done in each case? Write the code for `add()` when you understand what should happen in each case.    
e. The next method, `get()` requires looping through the nodes to get to the correct index. Fill in the code for `get()`.  

## Challenge


1. To complete our ArrayList implementation, we need to add two more methods: `remove()` and `resize()`.    
a. Implement the `remove()` method, which removes the element at a given index in an MyArrayList.  
b. The `resize()` method is a bit more complicated. The memory diagrams, below, show what we want to happen step-by-step. Implement the `resize()` method, referring to the diagrams. Note that this is a private method that does not take any arguments and does not return anything.

    ![Challenge Q2](stage-1.png)
    ![Challenge Q2](stage-2.png)
    ![Challenge Q2](stage-3.png)
  
    c. Finally, update your `add()` method to make use of `resize()`. Your implementation of MyArrayList is now complete.

2. To complete our MyLinkedList implementation, we only need to add one method: `remove()`.    
a. Why do we _not_ need a `resize()` method for MyLinkedList?
        A linked list can grow and resize itself as a pre requirement since it doesn't waste any memory.
b. The code for the `remove()` method can be broken down into four cases. What are they? What should the code do in each case?
       If the size of the list is 1, we assign both the head and the tail to the first element. If we have to remove the first element, we got to reassign the head to the next elemen.
       If we have to remove the last element, we loop through the list until we get to the last element, set it to null, adn assign the tail to the element right before it.
       Last case if index is in the middle of the list, we go trhough the list, remove the element by reassigning the other elements one by one, one after the other.
c. Write the code for `remove()`.  Your implementation of MyLinkedList is now complete.
        Wrote that
3. Sections 4.6-4.8 of Zybooks describe a data structure called the doubly-linked list. in short, the main distinguishing feature of a doubly-linked list is that nodes have both `next` and `prev` pointers, that point to the next node and the previous node respectively. This means that the code for a doubly-linked list is almost exactly the same as that for a singly-linked lists, except for the node pointers that you have to change when adding and removing elements.    
a. Without writing any code, explain how you would need to modify your MyLinkedList `add()` method to turn your implementation into a doubly-linked list.
        When adding an element to a double linked list, you would have to create a new node for the element, point the current node towards the new node, and ALSO point the new node backwards towards the current node (since linked list nodes point both to the next and previous nodes). You would have to manipulate both next and previous pointers for each node.
b. Without writing any code, explain how you would need to modify your MyLinkedList `remove()` method to turn your implementation into a doubly-linked list. How would each of the four cases change?
        To remove an element from the list, you would have to have the previous node skip the ndoe that's being taken out and point to the node after. You would also have to change the node after the one that is being removed to point at the previous node. You would also have to manipulate BOTH previous and next pointers and go around the node that is being removed.

