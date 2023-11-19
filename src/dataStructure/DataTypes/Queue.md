# Queue

- A queue stores a n elements in a single-dimensional structure.
- First in first out manner (FIFO).
- One end is called rear and the other is called a front.
- Dequeue: When element is removed from the front.
- Enqueue: When element is added to the rear.

## Implementations

# Python

```python
class Queue():
    def __init__(self):
        self.items = []
    def isEmpty(self):
        return self.items == 0
    def enqueue(self,item):
        #adding the end ==> the end is rear
        self.items.append(item)
    def dequeue(self):
        # remove the oldest item in list [0]
        t = self.items[0]
        self.items = self.items.pop(0)
        return t
    def size(self):
        return len(self.items)

q = Queue()

q.enqueue("elie")
q.enqueue("green")
q.enqueue("blue")

print(q.dequeue())
print(q.isEmpty())
print(q.size())
```

## TS

```typescript
class Queue<T> {
  private array: T[] = [];

  pop(): T | undefined {
    return this.array.pop();
  }

  enqueue(data: T): void {
    // add the item to the end
    this.array.push(data);
  }
  dequeue(): T | undefined {
    // remove the oldest item in the list [0]
    return this.array.shift();
  }
  isEmpty(): boolean {
    return this.array.length === 0;
  }
  size(): number {
    return this.array.length;
  }
}
```

## JS

```javascript
class Queue {
  constructor() {
    this.items = [];
  }
  enqueue(data) {
    // add the new element to the rear
    this.items.push(data);
  }

  dequeue() {
    // remove the oldest item in the list [0]
    return this.items.shift();
  }

  size() {
    return this.items.length;
  }

  isEmpty() {
    return this.items.length === 0;
  }
}
```

## Go

```go
package main

import "sync"

type Item interface{}

type Queue struct {
	items []Item
	mutex sync.Mutex
}

// NewQueue creates a new instance of Queue with zero elements.
func NewQueue() *Queue {
	return &Queue{
		items: nil,
	}
}

// Push adds a new item to the end of the queue.
func (Q *Queue) Push(item Item) {
	Q.mutex.Lock()
	defer Q.mutex.Unlock()

	Q.items = append(Q.items, item)
}

// Pop removes and returns the first item from the queue.
func (Q *Queue) Pop() Item {
	Q.mutex.Lock()
	defer Q.mutex.Unlock()

	if len(Q.items) == 0 {
		return nil
	}

	tmp := Q.items[0]
	Q.items = Q.items[1:]
	return tmp
}

// Size returns the number of items currently in the queue.
func (Q *Queue) Size() int {
	Q.mutex.Lock()
	defer Q.mutex.Unlock()
	return len(Q.items)
}

// IsEmpty returns whether the queue is empty or not (boolean result).
func (Q *Queue) IsEmpty() bool {
	Q.mutex.Lock()
	defer Q.mutex.Unlock()
	return len(Q.items) == 0
}

```

# Time Complexity

- Enqueue => O(1)
- Dequeue => O(1)
