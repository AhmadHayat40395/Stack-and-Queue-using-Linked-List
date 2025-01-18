using System;

class Program
{
    static void Main()
    {
        // Stack Demonstration
        Console.WriteLine("Stack Operations:");
        Stack stack = new Stack();
        stack.Push(10);
        stack.Push(20);
        stack.Push(30);
        stack.Display();
        Console.WriteLine("Popped from stack: " + stack.Pop());
        stack.Display();

        // Queue Demonstration
        Console.WriteLine("\nQueue Operations:");
        Queue queue = new Queue();
        queue.Enqueue(10);
        queue.Enqueue(20);
        queue.Enqueue(30);
        queue.Display();
        Console.WriteLine("Dequeued from queue: " + queue.Dequeue());
        queue.Display();
    }
}

public class Queue
{
    private LinkedListNode front, rear;

    public void Enqueue(int data)
    {
        var newNode = new LinkedListNode(data);
        if (rear != null)
        {
            rear.Next = newNode;
        }
        else
        {
            front = newNode;
        }
        rear = newNode;
    }

    public int Dequeue()
    {
        if (front == null) throw new InvalidOperationException("Queue is empty.");
        int value = front.Data;
        front = front.Next;
        if (front == null) rear = null;
        return value;
    }

    public void Display()
    {
        var current = front;
        while (current != null)
        {
            Console.Write(current.Data + " ");
            current = current.Next;
        }
        Console.WriteLine();
    }
}

public class Stack
{
    private LinkedListNode top;

    public void Push(int data)
    {
        var newNode = new LinkedListNode(data);
        newNode.Next = top;
        top = newNode;
    }

    public int Pop()
    {
        if (top == null) throw new InvalidOperationException("Stack is empty.");
        int value = top.Data;
        top = top.Next;
        return value;
    }

    public void Display()
    {
        var current = top;
        while (current != null)
        {
            Console.Write(current.Data + " ");
            current = current.Next;
        }
        Console.WriteLine();
    }
}

public class LinkedListNode
{
    public int Data;
    public LinkedListNode Next;

    public LinkedListNode(int data)
    {
        Data = data;
    }
}
