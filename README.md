# Ex9 Check for Balanced Parentheses Using Stack
## DATE: 26.02.2026
## Developed by: VIJAY K
## RegisterNumber: 212223040236
## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1. Start the program.
2. Read an input string containing parentheses/brackets.
3. Create a stack to store opening brackets.
4. Traverse each character of the string:
   1. If the character is an opening bracket `(`, `{`, `[`, push it onto the stack.
   2. If it is a closing bracket `)`, `}`, `]`:
      - Check if the stack is empty: If yes, the string is unbalanced.
      - Otherwise, pop the top element from the stack and verify if it matches the current closing bracket.
      - If the brackets do not match, the string is unbalanced.
5. After traversal:
   - If the stack is empty, the string is balanced; otherwise, it's unbalanced.
6. Display the result.
7. End the program.

## Program:
```java
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
*/

import java.util.Scanner;

public class ParenChecker {
    static class ArrayStack
    {
        private char[] data;
        private int top;
        public ArrayStack(int capacity)
        {
            data=new char[capacity];
            top=-1;
        }
        public boolean isEmpty()
        {
            return top==-1;
        }
        
        public boolean isFull()
        {
            return top==data.length-1;
        }
        public void push(char c)
        {
            if(isFull())
            {
                System.out.println("Stack overflow");
            }
            data[++top]=c;
        }
        public char pop()
        {
            if(isEmpty())
            {
                System.out.println("Stack underflow");
            }
            return data[top--];
            
            
        }
        public char peek()
        {
            if(isEmpty())
            {
                System.out.println("Stack underflow");
            }
            return data[top];
        }
    }


    public static boolean isBalanced(String expr) {
        ArrayStack st = new ArrayStack(expr.length());
        for (char ch : expr.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (st.isEmpty()) return false;
                char top = st.pop();
                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }
        return st.isEmpty();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String expr = sc.nextLine();
        boolean ok = isBalanced(expr);
        System.out.println(ok);
        sc.close();
    }
}

```

## Output:
<img width="363" height="130" alt="image" src="https://github.com/user-attachments/assets/196a6228-ef4b-4a78-8d15-a64f4b35a907" />



## Result:
Thus,the program correctly checks whether an input string has balanced parentheses using a stack.



# Ex17 Reversing a String Using Stack Data Structure

## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1. Start the program.
2. Read the input string from the user.
3. Create an empty stack of characters.
4. Traverse the string and push each character onto the stack.
5. Pop each character from the stack and append it to a new string — this gives the reversed string.
6. Display the reversed string.
7. Stop the program.

## Program:
```java
/*
Program to reverses an input string using a stack
*/

import java.util.Scanner;
import java.util.Stack;

public class ReverseStringWithStack {

    public static String reverseString(String input) {
         Stack<Character> stack=new Stack<>();
        for(char ch:input.toCharArray())
        {
            stack.push(ch);
        }
        StringBuilder rev=new StringBuilder();
        while(!stack.isEmpty())
        {
            rev.append(stack.pop());
        }
        return rev.toString();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        String reversed = reverseString(input);
        System.out.println(reversed);

        scanner.close();
    }
}

```

## Output:
<img width="365" height="132" alt="image" src="https://github.com/user-attachments/assets/8ed4aa0c-0a74-4c41-bb99-e382b72198d7" />



## Result:
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.



# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)
## AIM:
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.

## Algorithm
1. Start the program.
2. Create a Queue using the LinkedList class.
3. Enqueue (add) customers to the queue as they arrive.
4. Display the current queue of customers.
5. Dequeue (remove) customers from the queue one by one as they are served.
6. Display which customer is being served and the remaining queue.
7. Repeat until all customers are served.  

## Program:
```java
/*
Program to functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
*/

import java.util.Scanner;

class Node {
    String customerName;
    Node next;

    public Node(String name) {
        this.customerName = name;
        this.next = null;
    }
}

class TicketQueue {
    private Node front;
    private Node rear;

    public TicketQueue() {
        this.front = this.rear = null;
    }

    public void enqueue(String customerName) {
        Node newNode = new Node(customerName);
        if (rear == null) {
            front = rear = newNode;
            return;
        }
        rear.next = newNode;
        rear = newNode;
    }

    public void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty. No customer to serve.");
            return;
        }
        System.out.println("Serving customer: " + front.customerName);
        front = front.next;
        if (front == null) {
            rear = null;
        }
    }

    public void displayQueue() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        System.out.print("Queue: ");
        Node temp = front;
        while (temp != null) {
            System.out.print(temp.customerName);
            if (temp.next != null) System.out.print(" -> ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class TicketCounter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        TicketQueue queue = new TicketQueue();
        String command;

        //System.out.println("Ticket Counter Simulation");
        //System.out.println("Commands: enqueue <name>, dequeue, display, exit");

        while (true) {
            //System.out.print("Enter command: ");

            // Fix for NoSuchElementException
            if (!scanner.hasNextLine()) {
                //System.out.println("No more input. Exiting simulation.");
                break;
            }

            command = scanner.nextLine().trim();
            if (command.isEmpty()) continue;

            String[] parts = command.split(" ");

            switch (parts[0]) {
                case "enqueue":
                    if (parts.length >= 2) {
                        queue.enqueue(parts[1]);
                    } else {
                        System.out.println("Please provide a customer name.");
                    }
                    break;
                case "dequeue":
                    queue.dequeue();
                    break;
                case "display":
                    queue.displayQueue();
                    break;
                case "exit":
                    System.out.println("Exiting simulation.");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid command.");
            }
        }

        scanner.close(); // Safe close
    }
}

```

## Output:
<img width="1106" height="719" alt="image" src="https://github.com/user-attachments/assets/c78629aa-af80-4fcd-b8bc-b8a29aad63c6" />



## Result:
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.



# Ex19 Palindrome Check Using Deque
## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.


## Algorithm
1. Start the program.
2. Read an input string from the user.
3. Remove all non-alphanumeric characters from the string.
4. Convert all characters to lowercase for uniform comparison.
5. Create a deque (double-ended queue).
6. Insert each character of the cleaned string into the deque.
7. While the deque has more than one element:
   - Remove one character from the front and one from the rear.
   - Compare both characters.
   - If they are not equal, the string is not a palindrome.
8. If all pairs match, the string is a palindrome.
9. Display the result.

## Program:
```java
/*
Program to checks whether a given message is a palindrome by removing all non-alphanumeric characters.
*/

import java.util.*;

public class PalindromeChecker {
    
    public static boolean isPalindrome(String message) {
        // Convert to lowercase and remove non-alphanumeric characters
        message = message.toLowerCase().replaceAll("[^a-z0-9]", "");
        
        Deque<Character> deque = new ArrayDeque<>();
        
        // Add all characters to the deque
        for (char c : message.toCharArray()) {
            deque.addLast(c);
        }
        
        // Compare characters from both ends
        while (deque.size() > 1) {
            if (deque.pollFirst() != deque.pollLast()) {
                return false;  // Mismatch found
            }
        }
        
        return true;  // All characters matched
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        //System.out.println("Enter a message:");
        String input = scanner.nextLine();

        if (isPalindrome(input)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not a palindrome");
        }

        scanner.close();
    }
}

```

## Output:
<img width="384" height="136" alt="image" src="https://github.com/user-attachments/assets/ff3377d2-a5f8-40c7-944d-274f491e7222" />



## Result:
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.



# Ex20 Sorting an Array using Merge Sort Algorithm

## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.

## Algorithm
1. Start the program.
2. Define a method `mergeSort()` that divides the array into two halves recursively until single elements remain.
3. Define a method `merge()` that merges two sorted halves into a single sorted array.
4. In the `main()` method:
   - Initialize an array of integers.
   - Display the original (unsorted) array.
   - Call the `mergeSort()` method to sort the array.
   - Display the sorted array.
5. Stop the program.  

## Program:
```java
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
*/

import java.util.*;

public class Solution {
    
    private void swap(int[] arr, int index1, int index2) {
        int temp = arr[index1];
        arr[index1] = arr[index2];
        arr[index2] = temp;
    }

    private void heapify(int[] arr, int n, int i) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && arr[left] > arr[largest]) {
            largest = left;
        }

        if (right < n && arr[right] > arr[largest]) {
            largest = right;
        }

        if (largest != i) {
            swap(arr, i, largest);
            heapify(arr, n, largest);
        }
    }

    private void heapSort(int[] arr) {
        int n = arr.length;
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(arr, n, i);
        }

        for (int i = n - 1; i >= 0; i--) {
            swap(arr, 0, i);
            heapify(arr, i, 0);
        }
    }

    public int[] sortArray(int[] nums) {
        heapSort(nums);
        return nums;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution solution = new Solution();

        int n = sc.nextInt();
        
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int[] sorted = solution.sortArray(nums);
        System.out.println("Sorted array:");
        System.out.println(Arrays.toString(sorted));

        sc.close();
    }
}
```

## Output:
<img width="561" height="182" alt="image" src="https://github.com/user-attachments/assets/8909207f-3220-4841-8649-20fd9285092e" />
## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.
