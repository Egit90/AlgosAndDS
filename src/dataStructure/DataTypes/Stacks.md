# Stacks

- Think of books stacked on top of each other. The last book that gets added is the first one to be removed.
- A Stack is a linear data structure that sore a one dimensional list.
- It can store items in a last-in,first-out `LIFO`
- It can store items in a first-in,last-out `FILO`
  `💡 both LIFO and FILO are describing the same thing....`
- operations related to a stack:

  ```
    isEmpty => Returns true if stack is empty.
    push => add a new Element.
    pop => returns the element added most recently and remove it form the stack.
  ```

# Implementations:

## Python

```python
  class Stack:
    def __init__(self):
        self.items = []
    def isEmpty(self):
        return self.items == []
    def push(self , item):
        self.items.append(item)
    def pop(self):
        return self.items.pop()
    def peek(self):
        return self.items[len(self.items) -1 ]
    def size(self):
        return len(self.items)

stack = Stack()
stack.push("Red")
stack.push("White")
stack.push("Blue")

print(stack.peek()) // Blue
print(stack.size()) // 3
print(stack.pop()) // Blue
print(stack.peek()) // White
print(stack.size()) // 2
print(stack.isEmpty()) // false


```

# TS:

```typescript
class Stack<T> {
  private array: T[] = [];

  pop(): T | undefined {
    return this.array.pop();
  }

  push(data: T): void {
    this.array.push(data);
  }

  peek(): T {
    return this.array[this.array.length - 1];
  }
  isEmpty(): boolean {
    return this.array.length === 0;
  }
  size(): number {
    return this.array.length;
  }

const numberStack = new Stack<number>();
console.log("Pushing 5 onto the stack");
numberStack.push(5);
console.log("Pushing 8 onto the stack");
numberStack.push(8);
console.log(`Top element: ${numberStack.peek()}`); // 8
console.log(`Popped element: ${numberStack.pop()}`); // 8
console.log(`Stack size: ${numberStack.size()}`); // 1

}
```

## JS

```javascript
class Stack {
  constructor() {
    this.array = [];
  }

  pop() {
    return this.array.pop();
  }

  push(data) {
    this.array.push(data);
  }

  peek() {
    return this.array[this.array.length - 1];
  }

  isEmpty() {
    return this.array.length === 0;
  }

  size() {
    return this.array.length;
  }
}

const numberStack = new Stack();
console.log("Pushing 5 onto the stack");
numberStack.push(5);
console.log("Pushing 8 onto the stack");
numberStack.push(8);
console.log(`Top element: ${numberStack.peek()}`); // 8
console.log(`Popped element: ${numberStack.pop()}`); // 8
console.log(`Stack size: ${numberStack.size()}`); // 1
```

## GO

```go

package stack

import "sync"

type Item interface

type Stack struct {
    items []item
    mutex sync.Mutex
}

func newEmptyStack() *Stack {
    return &Stack{
        items: nil
    }
}


func (stack *Stack) push (item Item) {
    stack.mutex.Lock()
    defer stack.mutex.Unlock()

    stack.items = append(stack.items , item)
}


func (stack *Stack) pop () Item {
    stack.mutex.Lock()
    defer stack.mutex.Unlock()

    if (len(stack.items) == 0) {
        return nil
    }

    lastItem := stack.items[len(stack.items) -1]
    stack.items = stack.items[:len(stack.items) -1]

    return lastItem
}

func (stack *Stack) IsEmpty() bool {
    stack.mutex.Lock()
    defer stack.mutex.Unlock()

    return len(stack.items) == 0
}

func (stack *Stack) Peek() Item {
    stack.mutex.Lock()
    defer stack.mutex.Unlock()

    if len(stack.items) == 0 {
        return nil
    }

    return stack.items[len(stack.items)-1]
}

func (stack *Stack) Size() int {
    stack.mutex.Lock()
    defer stack.mutex.Unlock()

    return len(stack.items)
}
```

# Time Complexity

- push O(1)
- Pop o(1)
