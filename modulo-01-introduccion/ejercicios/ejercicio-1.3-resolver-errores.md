# Resolving Complicated Errors with AI

## Objectives
- Understand how AI can assist in resolving complicated errors.
- Learn about memory leaks and race conditions as common problems in programming.

## Context
Complicated errors in software development can lead to significant downtime and performance bottlenecks. This exercise explores two specific cases: Memory Leaks in Node.js and Race Conditions in Python.

## Problematic Code Examples

### Memory Leak Case: Node.js with CacheManager Class
```javascript
class CacheManager {
    constructor() {
        this.cache = {};
    }

    addToCache(key, value) {
        this.cache[key] = value;
    }

    getFromCache(key) {
        return this.cache[key];
    }
}

const cacheManager = new CacheManager();
for(let i = 0; i < 100000; i++) {
    cacheManager.addToCache(`key${i}`, `value${i}`);
}
```

In this example, the CacheManager class keeps all entries in memory without any mechanism to evict old data. This can lead to a memory leak if the cache grows indefinitely.

### Race Condition Case: Python with InventoryManager Class
```python
import threading

class InventoryManager:
    def __init__(self):
        self.lock = threading.Lock()
        self.inventory = 0

    def add_stock(self, quantity):
        with self.lock:
            current_stock = self.inventory
            self.inventory = current_stock + quantity

    def get_stock(self):
        return self.inventory

inventory_manager = InventoryManager()
threads = [threading.Thread(target=inventory_manager.add_stock, args=(10,)) for _ in range(100)]
for thread in threads:
    thread.start()
for thread in threads:
    thread.join()
```

In this example, if multiple threads attempt to add stock simultaneously, without proper locking, it can lead to unexpected results and a race condition.

## Mission Instructions
1. Analyze the provided code examples.
2. Identify the issues that can lead to errors in each case.
3. Use AI tools, such as GitHub Copilot, to suggest possible fixes or improvements for the code examples.

## Hints for Using Copilot
- Start writing the function name and key comments about the intended logic to get relevant suggestions from Copilot.
- Review Copilot's suggestions carefully and test them in a local environment before implementing.

## Success Criteria
- Successfully recognize and explain the issues of the code examples.
- Employ AI suggestions to modify the code appropriately to handle the errors.

## Reflection Questions
1. How did AI assist you in identifying the problems in the code?
2. What changes did you implement based on the suggestions received?
3. What unexpected insights did you gain from using AI tools?

## Additional Resources
- [Memory Leak Detection in Node.js](https://nodejs.org/en/docs/guides/)
- [Concurrency in Python: A Historical Perspective](https://realpython.com/python-concurrency/)  
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)