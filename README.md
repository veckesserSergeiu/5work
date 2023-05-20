public class Hash22 { 
    private int SIZE = 16; 
    private Node[] table = new Node[SIZE]; 
    class Node { 
        int key; 
        Node next; 
 
        Node(int key) { 
            this.key = key; 
            this.next = null; 
        } 
    } 
    public void add(int key) { 
        int hash = key % SIZE; 
 
        Node newNode = new Node(key); 
 
        if (table[hash] == null) { 
            table[hash] = newNode; 
            return; 
        } 
 
        Node current = table[hash]; 
        while (current.next != null && current.key != key) { 
            current = current.next; 
        } 
 
        if (current.key == key) { 
            return; 
        } 
 
        current.next = newNode; 
    } 
    public void remove(int key) { 
        int hash = key % SIZE; 
 
        if (table[hash] == null) { 
            return; 
        } 
 
        Node current = table[hash]; 
        Node prev = null; 
        while (current != null && current.key != key) { 
            prev = current; 
            current = current.next; 
        } 
 
        if (current == null) { 
            return; 
        } 
 
        if (prev == null) { 
            table[hash] = current.next; 
        } else { 
            prev.next = current.next; 
        } 
    } 
    public boolean contains(int key) { 
        int hash = key % SIZE; 
 
        Node current = table[hash]; 
        while (current != null) { 
            if (current.key == key) { 
                return true; 
            } 
            current = current.next; 
        } 
 
        return false; 
    } 
} 

 
