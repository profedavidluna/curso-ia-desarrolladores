Title: 🐛 Ejercicio 1.3: Resolver Errores Complicados con IA

Duration: 30 minutes
Difficulty: Media-Alta
Tool: GitHub Copilot / ChatGPT / Claude

Objectives:
- Use AI assistants to diagnose complex errors
- Learn to ask effective questions to AI
- Understand root causes of hard-to-detect bugs
- Apply AI-suggested solutions

Case 1: Memory Leak in Node.js Cache System

Context: A Node.js application is experiencing constant memory growth until it crashes. The team suspects a memory leak in the cache system.

Problematic Code in JavaScript:
```javascript
class CacheManager {
    constructor() {
        this.cache = new Map();
        this.subscribers = new Map();
        this.cleanupInterval = setInterval(() => {
            this.cleanup();
        }, 60000);
    }

    set(key, value, ttl = 3600000) {
        const entry = { value, expires: Date.now() + ttl, listeners: [] };
        this.cache.set(key, entry);
        if (this.subscribers.has(key)) {
            this.subscribers.get(key).forEach(callback => callback(value));
        }
        return true;
    }

    subscribe(key, callback) {
        if (!this.subscribers.has(key)) {
            this.subscribers.set(key, []);
        }
        this.subscribers.get(key).push(callback);
    }

    cleanup() {
        const now = Date.now();
        for (const [key, entry] of this.cache.entries()) {
            if (entry.expires < now) {
                this.cache.delete(key);
            }
        }
    }

    destroy() {
        this.cache.clear();
    }
}

const cache = new CacheManager();
function handleUserRequest(userId) {
    const userHandler = (data) => console.log('User data updated:', data);
    cache.subscribe('user:' + userId, userHandler);
    return cache.get('user:' + userId);
}
setInterval(() => {
    const randomUserId = Math.floor(Math.random() * 1000);
    handleUserRequest(randomUserId);
}, 100);
```

Your Mission:
1. Identify the memory leaks in the code
2. Explain why they are occurring
3. Fix the code using Copilot's help
4. Validate that the solution resolves the problem

Hints for using Copilot:
- Comment the code line by line asking about potential problems
- Ask: "Does this code have memory leaks? Where?"
- Write: "Fix memory leak:" and let Copilot suggest
- Ask: "What resources are not being freed correctly?"

Success Criteria:
- Identified at least 3 memory leaks
- Subscribers are cleaned up correctly
- Interval is cleaned when cache is destroyed
- No orphaned references remain
- Code includes explanatory comments

Case 2: Race Condition in Python Inventory Update

Context: An e-commerce system has problems where sometimes more inventory is sold than available. The bug only occurs under high concurrency and is hard to reproduce.

Problematic Python Code:
```python
import threading
import time
from typing import Dict

class InventoryManager:
    def __init__(self):
        self.inventory: Dict[str, int] = {}
        self.reserved: Dict[str, int] = {}
        self.lock = threading.Lock()
    
    def add_product(self, product_id: str, quantity: int):
        if product_id not in self.inventory:
            self.inventory[product_id] = 0
            self.reserved[product_id] = 0
        self.inventory[product_id] += quantity
    
    def get_available(self, product_id: str) -> int:
        if product_id not in self.inventory:
            return 0
        return self.inventory[product_id] - self.reserved.get(product_id, 0)
    
    def reserve_product(self, product_id: str, quantity: int, order_id: str) -> bool:
        available = self.get_available(product_id)
        if available < quantity:
            return False
        time.sleep(0.01)  # Simulates external validation
        with self.lock:
            self.reserved[product_id] = self.reserved.get(product_id, 0) + quantity
        return True
```

Your Mission:
1. Run the code several times and observe inconsistent behavior
2. Identify where the race condition is
3. Explain why the problem occurs
4. Fix the code with Copilot's help
5. Test that it now works correctly under concurrency

Hints for using Copilot:
- Ask: "Is this code thread-safe? Where is the race condition?"
- Comment: "FIX: Protect this critical section correctly"
- Write: "TODO: Implement atomic reservation"

Success Criteria:
- Race condition is identified and documented
- Code uses locks correctly
- Cannot sell more inventory than available
- Solution is performant (no unnecessary locks)
- Code includes concurrency validation tests

Reflection Questions:
1. How did Copilot help you identify the errors?
2. What questions or comments were most effective?
3. Did AI suggest solutions you hadn't considered?
4. How much time did you save compared to traditional debugging?

Additional Resources:
- Debugging with GitHub Copilot guide
- Common Memory Leaks in Node.js documentation
- Python Threading Best Practices