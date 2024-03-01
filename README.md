// COM/B/01-00107/2022 NOEL KIPNGETICH
//COM/B/01-00114/2022 ABRAHAM YEGON
//SIT/B/01-02887/2022 EDWIN KIMUTAI
// COM/B/01-00109/2022 NAHASHION

#include <iostream>
#include <queue>


using namespace std;


template <typename T>
struct Node {
    T data;
    Node* next;

    Node(T value) : data(value), next(NULL) {}
};



template <typename type, int MAX_SIZE>

class ArrayStack {
private:
    type array[MAX_SIZE];
    int top;

public:
    ArrayStack() {
            top=-1;
        }


    void push(type value) {
        if (top < MAX_SIZE - 1) {
            array[++top] = value;
        } else {
           cout << "Stack is full." << endl;
        }
    }

    void pop() {
        if (top >= 0) {
            --top;
        } else {
            cout << "Stack is empty." <<endl;
        }
    }

    bool isEmpty() {
        return top == -1;
    }
        void display() {
        if(top==-1){
                cout<<"Stack is empty \n";
                return;
        }
        else{
                cout<<"stack array : ";
                for(int n=top;n>=0;n--){
                        cout<<array[n]<<" ";

                }
                cout<<endl;

}



    }
};


template <typename T>
class LinkedStack {
private:
    Node<T>* top;

public:
    LinkedStack(){ top=NULL; }

    void push(T value) {
        Node<T>* newNode = new Node<T>(value);
        newNode->next = top;
        top = newNode;
    }

    void pop() {
        if (top != NULL) {
            Node<T>* temp = top;
            top = top->next;
            delete temp;
        }
    }

     void display() {
        cout << "Linked Stack: ";
        Node<T>* current = top;
        while (current != NULL) {
            std::cout << current->data << " ";
            current = current->next;
        }
        cout << endl;
    }

    bool isEmpty() {
        return top == NULL;
    }
};


template <typename T, int MAX_SIZE>
class ArrayCircularQueue {
private:
    T array[MAX_SIZE];
    int front, rear;

public:
    ArrayCircularQueue() {
    front=-1;        
    rear=-1;
        }

    void enqueue(T value) {
        if ((rear + 1) % MAX_SIZE == front) {
           cout << "Queue is full." << endl;
            return;
        }

        if (isEmpty()) {
            front = 0;
        }

        rear = (rear + 1) % MAX_SIZE;
        array[rear] = value;
    }

    void dequeue() {
        if (isEmpty()) {
         cout << "Queue is empty." << endl;
            return;
        }

        if (front == rear) {

            front = rear = -1;
        } else {
            front = (front + 1) % MAX_SIZE;
        }
    }

  void display() {
        if (isEmpty()) {
            cout << "Array Circular Queue is empty." << endl;
            return;
        }

    cout << "Array Circular Queue: ";
        int i = front;
        do {
            cout << array[i] << " ";
            i = (i + 1) % MAX_SIZE;
        } while (i != (rear + 1) % MAX_SIZE);

       cout << endl;
    }

    bool isEmpty() {
        return front == -1 && rear == -1;
    }
};


template <typename T>
class LinkedCircularQueue {
private:
    Node<T>* front;
    Node<T>* rear;

public:
    LinkedCircularQueue() {
         front=NULL;
          rear=NULL; }

    void enqueue(T value) {
        Node<T>* newNode = new Node<T>(value);
        if (isEmpty()) {
            front = rear = newNode;
        } else {
            rear->next = newNode;
            rear = newNode;
        }
    }

    void dequeue() {
        if (isEmpty()) {
           cout << "Queue is empty" << endl;
            return;
        }

        Node<T>* temp = front;
        front = front->next;
        delete temp;

        if (front == NULL) {

            rear = NULL;
        }
    }

    void display() {
        if (isEmpty()) {
           cout << "Linked Circular Queue is empty." << endl;
            return;
        }

     cout << "Linked Circular Queue: ";
        Node<T>* current = front;
        do {
           cout << current->data << " ";
            current = current->next;
        } while (current != NULL);

       cout <<endl;
    }

    bool isEmpty() {
        return front == NULL;
    }
};

template <typename T>
class LinkedPriorityQueue {
private:
   priority_queue<T> pq;

public:
    void insert(T value) {
        pq.push(value);
    }

    void remove() {
        if (!pq.empty()) {
            pq.pop();
        }
    }

     void display() {
        if (isEmpty()) {
          cout << "Array Priority Queue is empty." << endl;
            return;
        }

cout << "Array Priority Queue: ";
        priority_queue<T> tempPQ = pq;
        while (!tempPQ.empty()) {
        cout << tempPQ.top() << " ";
            tempPQ.pop();
        }
  cout << endl;
    }

    bool isEmpty() {
        return pq.empty();
    }
};

template <typename T, int MAX_SIZE>
class ArrayPriorityQueue {
private:
    priority_queue<T> pq;

public:
    void insert(T value) {
        pq.push(value);
    }

    void remove() {
        if (!pq.empty()) {
            pq.pop();
        }
    }

     void display() {
        if (isEmpty()) {
         cout << "Linked Priority Queue is empty." << endl;
            return;
        }

       cout << "Linked Priority Queue: ";
      priority_queue<T> tempPQ = pq;
        while (!tempPQ.empty()) {
          cout << tempPQ.top() << " ";
            tempPQ.pop();
        }
      cout <<endl;
    }

    bool isEmpty() {
        return pq.empty();
    }
};


int main() {

    ArrayStack<int, 8> arrayStack;
    LinkedStack<int> linkedStack;

    ArrayCircularQueue<int, 8> arrayCircularQueue;
    LinkedCircularQueue<int> linkedCircularQueue;

    ArrayPriorityQueue<int, 8> arrayPriorityQueue;
    LinkedPriorityQueue<int> linkedPriorityQueue;


    arrayStack.push(10);
    arrayStack.push(20);
    arrayStack.push(30);

    linkedStack.push(40);
    linkedStack.push(50);
    linkedStack.push(60);


    arrayCircularQueue.enqueue(70);
    arrayCircularQueue.enqueue(80);
    arrayCircularQueue.enqueue(90);


    linkedCircularQueue.enqueue(5);
    linkedCircularQueue.enqueue(45);
    linkedCircularQueue.enqueue(85);


    arrayPriorityQueue.insert(100);
    arrayPriorityQueue.insert(910);
    arrayPriorityQueue.insert(840);


    linkedPriorityQueue.insert(50);
    linkedPriorityQueue.insert(88);
    linkedPriorityQueue.insert(90);


    arrayStack.pop();


    linkedStack.pop();


    arrayCircularQueue.dequeue();

    linkedCircularQueue.dequeue();


    arrayPriorityQueue.remove();


    linkedPriorityQueue.remove();


   arrayStack.display();
    linkedStack.display();

    arrayCircularQueue.display();
   linkedCircularQueue.display();

   arrayPriorityQueue.display();
    linkedPriorityQueue.display();


    return 0;
}
