# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)
## DATE:26.02.26
## AIM:.
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.
## Algorithm
1. Start program.
2. Queue Initialization.
3. Queue Operations.
4. DISPLAY Operation.
5. Main Simulation.
6. End the program. 

## Program:
```
/*
Program to functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
Developed by: VIJAY K
RegisterNumber:  212223040236
*/
```
```
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

        if (front == null) {
            front = rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
    }

    public void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty. No customer to serve.");
            return;
        }

        System.out.println("Serving customer: " + front.customerName);
        front = front.next;

        if (front == null) rear = null;
    }

    public void displayQueue() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }

        Node temp = front;
        System.out.print("Queue: ");
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

        while (scanner.hasNextLine()) {
            String command = scanner.nextLine().trim();
            if (command.isEmpty()) continue;

            String[] parts = command.split(" ");

            if (parts[0].equals("enqueue")) {
                if (parts.length >= 2) queue.enqueue(parts[1]);
            }
            else if (parts[0].equals("dequeue")) {
                queue.dequeue();
            }
            else if (parts[0].equals("display")) {
                queue.displayQueue();
            }
            else if (parts[0].equals("exit")) {
                System.out.println("Exiting simulation.");
                break;
            }
        }

        scanner.close();
    }
}
```

## Output:
<img width="1104" height="808" alt="image" src="https://github.com/user-attachments/assets/fe70263b-931a-47b1-adc1-c528c50f5de7" />

## Result:
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.
