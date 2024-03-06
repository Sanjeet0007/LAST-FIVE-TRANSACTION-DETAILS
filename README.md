import java.util.Scanner;

// A class to represent a queue
class Queue {
    int front, rear, size;
    int capacity;
    int[] array;

    // Constructor
    public Queue(int capacity) {
        this.capacity = capacity;
        this.front = this.size = 0;
        this.rear = capacity - 1;
        this.array = new int[this.capacity];
    }

    // Function to check if the queue is full
    boolean isFull() {
        return (this.size == this.capacity);
    }

    // Function to check if the queue is empty
    boolean isEmpty() {
        return (this.size == 0);
    }

    // Function to add an item to the queue
    void enqueue(int item) {
        if (isFull()) {
            return;
        }
        this.rear = (this.rear + 1) % this.capacity;
        this.array[this.rear] = item;
        this.size = this.size + 1;
        System.out.println(item + " deposited to your account");
    }

    // Function to remove an item from the queue
    int dequeue() {
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }
        int item = this.array[this.front];
        this.front = (this.front + 1) % this.capacity;
        this.size = this.size - 1;
        return item;
    }

    // Function to get the front of the queue
    int front() {
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return this.array[this.front];
    }

    // Function to get the rear of the queue
    int rear() {
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return this.array[this.rear];
    }
}

// Main class for bank transactions
public class BankTransaction {

    public static void main(String[] args) {
        intro();
        int accountType = accountValidation();

        if (accountType == 1) {
            sanjeetTransaction();
        } else if (accountType == 2) {
            kumarTransaction();
        }
    }

    // Transaction for Sanjeet's account
    private static void sanjeetTransaction() {
        Queue queue = new Queue(3);
        int balance = 50000;

        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the options");
        System.out.println("1. Check Balance");
        System.out.println("2. Transaction History");

        int option = scanner.nextInt();

        if (option == 1) {
            System.out.println("Your current Balance is: Rs. " + balance);
        } else if (option == 2) {
            System.out.println("Your account transactions are:");
            queue.enqueue(10);
            queue.enqueue(20);
            queue.enqueue(30);
            queue.enqueue(40);

            System.out.println(queue.dequeue() + " debited from your account");
        }
    }

    // Transaction for Kumar's account
    private static void kumarTransaction() {
        Queue kumarQueue = new Queue(3);
        int balance = 100000;

        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the options");
        System.out.println("1. Check Balance");
        System.out.println("2. Transaction History");

        int option = scanner.nextInt();

        if (option == 1) {
            System.out.println("Your current Balance is: Rs. " + balance);
        } else if (option == 2) {
            System.out.println("Your account transactions are:");
            kumarQueue.enqueue(1000);
            kumarQueue.enqueue(2000);
            kumarQueue.enqueue(3000);
            kumarQueue.enqueue(4400);

            System.out.println(kumarQueue.dequeue() + " Debited from Your Account");
        }
    }

    // Account validation
    private static int accountValidation() {
        System.out.println("Please Enter your account number: ");
        Scanner scanner = new Scanner(System.in);
        int accountNumber = scanner.nextInt();

        if (accountNumber == 1234) {
            System.out.println("Welcome Sanjeet ");
            return 1;
        } else if (accountNumber == 2012) {
            System.out.println("Welcome Kumar ");
            return 2;
        } else {
            System.out.println("You have entered the wrong account number");
            return accountValidation();
        }
    }

    // Introduction
    private static void intro() {
        System.out.println("\n\n\n\t  LAST 5");
        System.out.println("\n\n\tTRANSACTION");
        System.out.println("\n\n\t  MANAGEMENT");
        System.out.println("\n\n\n\nMADE BY : Sanjeet Kumar");
        System.out.println("\n\nSCHOOL : SURESH GYAN VIHAR UNIVERSITY");
    }
}
