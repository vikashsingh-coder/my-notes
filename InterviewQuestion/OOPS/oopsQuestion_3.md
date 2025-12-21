## **Core OOP & JavaScript Concepts**

---

## 1. How does **prototypal inheritance** differ from class-based inheritance in JS?

### 🔹 Prototypal Inheritance

- Objects inherit **directly from other objects**
- Every object has an internal `[[Prototype]]`
- Property/method lookup happens via the **prototype chain**

```js
const user = {
  greet() {
    console.log("Hello");
  },
};

const admin = Object.create(user);
admin.role = "admin";

admin.greet(); // Hello
```

### 🔹 Class-based Inheritance

- Introduced using `class` and `extends`
- It is **syntactic sugar** over prototypal inheritance

```js
class User {
  greet() {
    console.log("Hello");
  }
}

class Admin extends User {}

const admin = new Admin();
admin.greet(); // Hello
```

### ✅ Key Difference

| Prototypal      | Class-based                 |
| --------------- | --------------------------- |
| Object → Object | Class → Instance            |
| More flexible   | More structured             |
| Native JS model | Abstraction over prototypes |

👉 **Important:** JavaScript is **prototype-based internally**, even when using `class`.

---

## 2. How would you implement **multiple inheritance** in JavaScript?

JavaScript does **not support true multiple inheritance**, but it can be achieved using **mixins or composition**.

### 🔹 Using Mixins (Most Common)

```js
const canFly = {
  fly() {
    console.log("Flying");
  },
};

const canSwim = {
  swim() {
    console.log("Swimming");
  },
};

class Duck {}

Object.assign(Duck.prototype, canFly, canSwim);

const duck = new Duck();
duck.fly();
duck.swim();
```

### ❌ Why not multiple `extends`?

- Diamond problem
- Method name conflicts
- Complex and error-prone

👉 **Interview Answer:**

> Multiple inheritance in JS is handled using **mixins and composition**, not multiple `extends`.

---

## 3. Explain **object composition** in JS and how it compares to inheritance

### 🔹 Object Composition

- Build objects by **combining reusable behaviors**
- Follows a **has-a** relationship

```js
const logger = (state) => ({
  log: () => console.log(state.message),
});

const saver = (state) => ({
  save: () => console.log("Saved:", state.message),
});

const createNote = (message) => {
  const state = { message };
  return Object.assign({}, logger(state), saver(state));
};

const note = createNote("Hello");
note.log();
note.save();
```

### 🔹 Inheritance

- Based on **is-a** relationship

```js
class Note {
  log() {}
}
```

### ✅ Comparison

| Inheritance            | Composition       |
| ---------------------- | ----------------- |
| Tight coupling         | Loose coupling    |
| Hard to modify         | Easy to extend    |
| Deep class hierarchies | Flat and flexible |

👉 **Senior-level principle:**

> Favor composition over inheritance.

---

## 4. How do **closures** help in creating private methods in JS classes?

### 🔹 Closure Basics

A closure allows a function to **remember variables from its outer scope**.

### 🔹 Private State Using Closures

```js
class Counter {
  constructor() {
    let count = 0; // private variable

    this.increment = () => {
      count++;
      console.log(count);
    };

    this.decrement = () => {
      count--;
      console.log(count);
    };
  }
}

const c = new Counter();
c.increment(); // 1
c.increment(); // 2
c.count; // undefined
```

### 🔹 Modern Alternative: Private Fields (`#`)

```js
class Counter {
  #count = 0;

  increment() {
    this.#count++;
  }
}
```

### ✅ Why closures are useful

- True data encapsulation
- Prevents external access
- Enables private methods and state

---

## 🔑 One-line Interview Summary

- JavaScript uses **prototypal inheritance internally**
- **Multiple inheritance** → achieved using mixins/composition
- **Composition** is more flexible and scalable than inheritance
- **Closures** enable private state and encapsulation

If you want, I can also provide:

- 🔹 Short interview answers
- 🔹 Real-world React / Node examples
- 🔹 System-design-oriented explanations

Just tell me 👍

Below are **clear, interview-ready answers in English**, with **definition + example + when to use**.

---

## 5. What are **static methods** in JavaScript classes and when should you use them?

### 🔹 What are Static Methods?

- Static methods belong to the **class itself**, not to instances
- They are called using the **class name**
- They **cannot access instance properties** (`this` refers to the class)

```js
class MathUtils {
  static add(a, b) {
    return a + b;
  }
}

MathUtils.add(2, 3); // 5
```

### 🔹 When to Use Static Methods

- Utility/helper functions
- Factory methods
- Logic that does **not depend on instance state**

```js
class User {
  static createGuest() {
    return new User("Guest");
  }

  constructor(name) {
    this.name = name;
  }
}
```

### ✅ Key Point

> Use static methods when behavior belongs to the **class**, not an object.

---

## 6. How would you implement **abstract classes** in JavaScript?

JavaScript does **not have built-in abstract classes**, but we can simulate them.

---

### 🔹 Approach 1: Throw error in base class (Most common)

```js
class Shape {
  constructor() {
    if (new.target === Shape) {
      throw new Error("Cannot instantiate abstract class");
    }
  }

  area() {
    throw new Error("Method must be implemented");
  }
}

class Rectangle extends Shape {
  area() {
    return 10 * 20;
  }
}

const rect = new Rectangle();
```

---

### 🔹 Approach 2: Interface-like contract check

```js
class BaseService {
  execute() {
    throw new Error("execute() must be implemented");
  }
}
```

### ✅ When to Use Abstract Classes

- Enforce method implementation
- Define a common contract for subclasses
- Base class should not be instantiated

---

## 7. Explain **mixins** in JavaScript and their use cases

### 🔹 What are Mixins?

- Mixins are **reusable pieces of functionality**
- They add behavior to classes or objects **without inheritance**

---

### 🔹 Example (Mixin with `Object.assign`)

```js
const canLog = {
  log() {
    console.log("Logging...");
  },
};

class Service {}

Object.assign(Service.prototype, canLog);

const s = new Service();
s.log();
```

---

### 🔹 Functional Mixin Pattern (Preferred)

```js
const withAuth = (Base) =>
  class extends Base {
    isAuthenticated() {
      return true;
    }
  };

class ApiService {}
class SecureApi extends withAuth(ApiService) {}
```

---

### ✅ Use Cases

- Multiple behaviors (without multiple inheritance)
- Cross-cutting concerns (logging, auth, analytics)
- Cleaner and flexible design

---

## 8. How can you prevent **modifying an object’s prototype** accidentally?

### 🔹 Problem

Modifying prototypes can:

- Break other objects
- Cause unexpected behavior
- Lead to security issues

---

### 🔹 Solutions

### ✅ 1. `Object.freeze()`

```js
Object.freeze(MyClass.prototype);
```

Prevents:

- Adding
- Removing
- Modifying methods

---

### ✅ 2. `Object.seal()`

```js
Object.seal(MyClass.prototype);
```

Allows modification of existing properties, but:

- Prevents adding/removing

---

### ✅ 3. Avoid `__proto__`

Use safe APIs only:

```js
Object.getPrototypeOf(obj);
Object.setPrototypeOf(obj, proto);
```

---

### ✅ 4. Use `class` syntax

- Reduces direct prototype manipulation
- Safer and cleaner

---

### 🔹 Interview-Grade Answer

> Prevent prototype modification by freezing or sealing prototypes, avoiding `__proto__`, and using class-based syntax.

---

## 🔑 Quick Interview Summary

- **Static methods** → Class-level behavior
- **Abstract classes** → Enforced contracts
- **Mixins** → Reusable behaviors without inheritance
- **Prototype safety** → `freeze`, `seal`, avoid direct mutation

---

## 9. Difference between **`Object.create()`** and **`new Class()`**

Both are used to create objects, but they work **very differently**.

---

### 🔹 `Object.create()`

- Creates a new object with a **specified prototype**
- Does **not call any constructor**
- More low-level and flexible

```js
const user = {
  greet() {
    console.log("Hello");
  },
};

const admin = Object.create(user);
admin.role = "admin";

admin.greet(); // Hello
```

✅ Key Characteristics:

- No constructor execution
- Direct control over prototype
- Useful for **pure prototypal inheritance**

---

### 🔹 `new Class()`

- Creates an instance from a **class or constructor function**
- Automatically:

  - Creates an object
  - Sets prototype
  - Binds `this`
  - Calls constructor

```js
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log("Hello", this.name);
  }
}

const user = new User("Vikash");
```

✅ Key Characteristics:

- Constructor logic executed
- More structured and readable
- Preferred in **OOP-style code**

---

### 🔹 Side-by-Side Comparison

| Feature          | Object.create()    | new Class()     |
| ---------------- | ------------------ | --------------- |
| Prototype setup  | Manual             | Automatic       |
| Constructor call | ❌ No              | ✅ Yes          |
| Syntax           | Low-level          | High-level      |
| Use case         | Delegation, mixins | Traditional OOP |

👉 **Interview Tip:**

> `Object.create()` is best for delegation; `new` is best for structured OOP.

---

## 10. How would you implement **polymorphic behavior** in JavaScript?

### 🔹 What is Polymorphism?

- Same method name
- Different implementations
- Behavior depends on the object type

---

### 🔹 Example: Method Overriding (Runtime Polymorphism)

```js
class Shape {
  area() {
    throw new Error("Not implemented");
  }
}

class Circle extends Shape {
  area() {
    return Math.PI * 10 * 10;
  }
}

class Rectangle extends Shape {
  area() {
    return 10 * 20;
  }
}

function printArea(shape) {
  console.log(shape.area());
}

printArea(new Circle());
printArea(new Rectangle());
```

✔️ Same method: `area()`
✔️ Different behavior based on object

---

### 🔹 Polymorphism without Classes (Duck Typing)

```js
function printArea(shape) {
  console.log(shape.area());
}

const square = {
  area() {
    return 25;
  },
};

printArea(square);
```

👉 JS cares about **behavior, not type**

---

### 🔹 Function Polymorphism (Same function, different input)

```js
function sum(a, b) {
  if (Array.isArray(a)) {
    return a.reduce((x, y) => x + y, 0);
  }
  return a + b;
}
```

---

### ✅ Key Interview Takeaways

- Achieved via **method overriding**
- Based on **dynamic dispatch**
- Supported naturally via **duck typing**
- No method overloading like Java

---

## 🔑 One-Line Interview Summary

- `Object.create()` → direct prototype delegation, no constructor
- `new Class()` → constructor-based object creation
- **Polymorphism** → same interface, different behavior

---

## 11. Implement a **Singleton Logger** in JavaScript

### 🔹 What is a Singleton?

- Ensures **only one instance** of a class exists
- Provides a **global access point** to that instance
- Common use cases: logging, config, DB connection

---

### 🔹 Implementation (Class-based, Production-friendly)

```js
class Logger {
  static instance;

  constructor() {
    if (Logger.instance) {
      return Logger.instance;
    }
    Logger.instance = this;
  }

  log(message) {
    console.log(`[LOG]: ${message}`);
  }

  error(message) {
    console.error(`[ERROR]: ${message}`);
  }
}

const logger1 = new Logger();
const logger2 = new Logger();

console.log(logger1 === logger2); // true
```

---

### 🔹 Alternative (Closure-based – very clean)

```js
const Logger = (function () {
  let instance;

  function createInstance() {
    return {
      log(msg) {
        console.log(`[LOG]: ${msg}`);
      },
    };
  }

  return {
    getInstance() {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();

const logger = Logger.getInstance();
```

### ✅ Key Takeaway

> Singleton guarantees a **single shared state** across the application.

---

## 12. Explain **Lazy Initialization** and how it improves performance

### 🔹 What is Lazy Initialization?

- Object or resource is created **only when it is needed**
- Avoids unnecessary computation or memory usage

---

### 🔹 Without Lazy Initialization (Eager)

```js
class Report {
  constructor() {
    this.data = this.loadHugeData(); // expensive
  }

  loadHugeData() {
    console.log("Loading data...");
    return new Array(1e6).fill("data");
  }
}
```

⚠️ Data loads even if never used.

---

### 🔹 With Lazy Initialization

```js
class Report {
  constructor() {
    this._data = null;
  }

  get data() {
    if (!this._data) {
      console.log("Loading data...");
      this._data = new Array(1e6).fill("data");
    }
    return this._data;
  }
}

const report = new Report();
// data loads only when accessed
report.data;
```

---

### 🔹 Where Lazy Initialization Helps

- Database connections
- Heavy computations
- Large config files
- UI components (React lazy loading)

### ✅ Key Takeaway

> Lazy initialization improves **startup time, memory usage, and responsiveness**.

---

## 13. How would you implement a **Caching Decorator** in JavaScript?

### 🔹 What is a Decorator?

- Wraps a function
- Adds extra behavior **without modifying original logic**
- Caching is a classic decorator use case

---

### 🔹 Caching Decorator (Function-level)

```js
function cache(fn) {
  const store = new Map();

  return function (...args) {
    const key = JSON.stringify(args);

    if (store.has(key)) {
      console.log("From cache");
      return store.get(key);
    }

    const result = fn.apply(this, args);
    store.set(key, result);
    return result;
  };
}
```

---

### 🔹 Usage Example

```js
function slowAdd(a, b) {
  console.log("Computing...");
  return a + b;
}

const cachedAdd = cache(slowAdd);

cachedAdd(2, 3); // Computing...
cachedAdd(2, 3); // From cache
```

---

### 🔹 Async Caching Decorator (Real-world)

```js
function asyncCache(fn) {
  const store = new Map();

  return async function (...args) {
    const key = JSON.stringify(args);
    if (store.has(key)) return store.get(key);

    const result = await fn(...args);
    store.set(key, result);
    return result;
  };
}
```

---

### ✅ Key Takeaway

> Decorators allow you to add **cross-cutting concerns** like caching, logging, and retry logic cleanly.

---

## 🔑 One-line Interview Summary

- **Singleton** → One instance, shared globally
- **Lazy initialization** → Create resources only when needed
- **Caching decorator** → Add caching without changing core logic

---

## 14. Design a **Retry Mechanism with Exponential Backoff** Using Classes

### 🔹 Concept

- Retry failed operations with **increasing delays**
- Commonly used in network requests, API calls

---

### 🔹 Implementation

```js
class Retry {
  constructor(maxRetries = 5, baseDelay = 500) {
    this.maxRetries = maxRetries;
    this.baseDelay = baseDelay;
  }

  async execute(fn) {
    for (let attempt = 0; attempt < this.maxRetries; attempt++) {
      try {
        return await fn();
      } catch (err) {
        const delay = this.baseDelay * Math.pow(2, attempt);
        console.log(`Retry #${attempt + 1}, waiting ${delay}ms`);
        await this.sleep(delay);
      }
    }
    throw new Error("Max retries reached");
  }

  sleep(ms) {
    return new Promise((resolve) => setTimeout(resolve, ms));
  }
}

// Usage
const retry = new Retry();

retry
  .execute(() => fetch("https://api.example.com/data"))
  .then((res) => console.log("Success"))
  .catch((err) => console.error(err));
```

### ✅ Key Takeaways

- Backoff = **baseDelay × 2^attempt**
- Avoids **spamming servers** on failures
- Can be combined with **jitter** to reduce collisions

---

## 15. Explain the **Observer Pattern** with Multiple Subscribers in JS

### 🔹 Concept

- **Observer (Subscriber)** watches a **Subject**
- Subject notifies all observers on changes
- Widely used in **event handling, UI updates**

---

### 🔹 Implementation

```js
class Subject {
  constructor() {
    this.observers = [];
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  unsubscribe(observer) {
    this.observers = this.observers.filter((obs) => obs !== observer);
  }

  notify(data) {
    this.observers.forEach((obs) => obs.update(data));
  }
}

class Observer {
  constructor(name) {
    this.name = name;
  }

  update(data) {
    console.log(`${this.name} received:`, data);
  }
}

// Usage
const subject = new Subject();
const obs1 = new Observer("Observer 1");
const obs2 = new Observer("Observer 2");

subject.subscribe(obs1);
subject.subscribe(obs2);

subject.notify("Event fired!");
```

### ✅ Key Takeaways

- **Loose coupling** between Subject and Observers
- Supports **dynamic subscription/unsubscription**
- Basis for **reactive programming and events**

---

## 16. Implement a **Publish-Subscribe System** for Chat Notifications

### 🔹 Concept

- Similar to Observer, but **topic-based**
- Subscribers listen to specific topics
- Publishers push messages without knowing subscribers

---

### 🔹 Implementation

```js
class PubSub {
  constructor() {
    this.topics = {};
  }

  subscribe(topic, subscriber) {
    if (!this.topics[topic]) this.topics[topic] = [];
    this.topics[topic].push(subscriber);
  }

  unsubscribe(topic, subscriber) {
    if (!this.topics[topic]) return;
    this.topics[topic] = this.topics[topic].filter((sub) => sub !== subscriber);
  }

  publish(topic, message) {
    if (!this.topics[topic]) return;
    this.topics[topic].forEach((sub) => sub(message));
  }
}

// Usage
const chat = new PubSub();

function user1(msg) {
  console.log("User1:", msg);
}
function user2(msg) {
  console.log("User2:", msg);
}

chat.subscribe("general", user1);
chat.subscribe("general", user2);

chat.publish("general", "Hello everyone!");
```

### ✅ Key Takeaways

- Decouples **senders and receivers**
- Supports **multiple topics**
- Foundation for **real-time systems (chat, notifications, messaging)**

---

### 🔑 Quick Summary

| Pattern/Mechanism      | Key Idea                    | Use Case                    |
| ---------------------- | --------------------------- | --------------------------- |
| **Retry with Backoff** | Retry with increasing delay | API calls, network requests |
| **Observer**           | One-to-many notification    | UI updates, events          |
| **Pub-Sub**            | Topic-based messaging       | Chat systems, notifications |

---

## 17. **Strategy Pattern** Using Payment Methods in JS

### 🔹 Concept

- **Encapsulate algorithms/strategies** and make them interchangeable
- Client uses strategy without knowing internal logic
- Example: Different payment methods (PayPal, Credit Card, Crypto)

---

### 🔹 Implementation

```js
class PaymentContext {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  pay(amount) {
    this.strategy.pay(amount);
  }
}

// Strategies
class PayPalPayment {
  pay(amount) {
    console.log(`Paid $${amount} using PayPal`);
  }
}

class CreditCardPayment {
  pay(amount) {
    console.log(`Paid $${amount} using Credit Card`);
  }
}

// Usage
const payment = new PaymentContext(new PayPalPayment());
payment.pay(100);

payment.setStrategy(new CreditCardPayment());
payment.pay(200);
```

### ✅ Key Takeaways

- Enables **algorithm swapping at runtime**
- Reduces **if/else** blocks for different behaviors
- Widely used in **payment gateways, sorting algorithms, discounts**

---

## 18. **Command Queue System** for Executing Tasks Asynchronously

### 🔹 Concept

- **Queue tasks** for execution in order
- Command pattern encapsulates a request as an object
- Useful for **async jobs, job queues, undo/redo**

---

### 🔹 Implementation

```js
class CommandQueue {
  constructor() {
    this.queue = [];
    this.isProcessing = false;
  }

  add(command) {
    this.queue.push(command);
    this.process();
  }

  async process() {
    if (this.isProcessing) return;
    this.isProcessing = true;

    while (this.queue.length > 0) {
      const command = this.queue.shift();
      await command.execute();
    }

    this.isProcessing = false;
  }
}

// Example command
class Task {
  constructor(name) {
    this.name = name;
  }

  async execute() {
    console.log(`Executing ${this.name}`);
    await new Promise((r) => setTimeout(r, 500));
  }
}

// Usage
const queue = new CommandQueue();
queue.add(new Task("Task 1"));
queue.add(new Task("Task 2"));
```

### ✅ Key Takeaways

- Encapsulates requests as **commands**
- Supports **async execution and queuing**
- Can extend for **undo/redo or retry mechanisms**

---

## 19. **Template Method Pattern** in JavaScript

### 🔹 Concept

- Define **skeleton of an algorithm** in a base class
- Subclasses override **specific steps**
- Ensures **reusable workflow with customizable steps**

---

### 🔹 Implementation

```js
class DataParser {
  parse() {
    this.readData();
    this.processData();
    this.saveData();
  }

  readData() {
    throw new Error("readData() must be implemented");
  }

  processData() {
    throw new Error("processData() must be implemented");
  }

  saveData() {
    console.log("Saving data to database");
  }
}

class CSVParser extends DataParser {
  readData() {
    console.log("Reading CSV data");
  }
  processData() {
    console.log("Processing CSV data");
  }
}

// Usage
const parser = new CSVParser();
parser.parse();
```

### ✅ Key Takeaways

- **Base class defines workflow**
- Subclasses **customize steps**
- Avoids **code duplication**

---

## 20. **Facade Pattern** to Simplify Complex API Calls

### 🔹 Concept

- Provide a **simplified interface** to complex subsystems
- Hides internal complexity from client

---

### 🔹 Implementation

```js
class AuthService {
  login(username, password) {
    console.log("Logging in");
  }
}
class NotificationService {
  sendEmail(email) {
    console.log("Sending email");
  }
}
class PaymentService {
  charge(amount) {
    console.log(`Charging $${amount}`);
  }
}

// Facade
class AppFacade {
  constructor() {
    this.auth = new AuthService();
    this.notify = new NotificationService();
    this.payment = new PaymentService();
  }

  registerUser(username, password, email) {
    this.auth.login(username, password);
    this.notify.sendEmail(email);
    this.payment.charge(0);
    console.log("User registration completed via facade");
  }
}

// Usage
const app = new AppFacade();
app.registerUser("Vikash", "1234", "vikash@example.com");
```

### ✅ Key Takeaways

- Reduces **client complexity**
- Provides **single entry point**
- Widely used for **API integration, SDK design, module orchestration**

---

### 🔑 Quick Summary (Q17–Q20)

| Pattern         | Key Idea                              | Example Use       |
| --------------- | ------------------------------------- | ----------------- |
| Strategy        | Swap algorithms dynamically           | Payment methods   |
| Command Queue   | Encapsulate tasks for async execution | Job queues        |
| Template Method | Base workflow, override steps         | Data parsing      |
| Facade          | Simplify complex subsystem            | API orchestration |

---

## 21. Design a **User Management System** with Roles, Permissions, and Access Control

### 🔹 Concept

- Users have **roles**
- Roles define **permissions**
- Access control determines whether a user can perform an action

---

### 🔹 Implementation (OOP + JS)

```js
class Permission {
  constructor(name) {
    this.name = name;
  }
}

class Role {
  constructor(name) {
    this.name = name;
    this.permissions = new Set();
  }

  addPermission(permission) {
    this.permissions.add(permission.name);
  }

  hasPermission(permissionName) {
    return this.permissions.has(permissionName);
  }
}

class User {
  constructor(username) {
    this.username = username;
    this.roles = [];
  }

  addRole(role) {
    this.roles.push(role);
  }

  can(permissionName) {
    return this.roles.some((role) => role.hasPermission(permissionName));
  }
}

// Usage
const read = new Permission("read");
const write = new Permission("write");

const adminRole = new Role("admin");
adminRole.addPermission(read);
adminRole.addPermission(write);

const user = new User("Vikash");
user.addRole(adminRole);

console.log(user.can("write")); // true
```

### ✅ Key Takeaways

- Roles **aggregate permissions**
- Users can have **multiple roles**
- Access control checks **roles → permissions**

---

## 22. Implement a **Multi-Level Undo-Redo System** in a Drawing App

### 🔹 Concept

- Maintain **history stack** for undo
- Maintain **redo stack** for redo
- Each operation is a **command object** (Command Pattern)

---

### 🔹 Implementation

```js
class Command {
  execute() {}
  undo() {}
}

class DrawCommand extends Command {
  constructor(shape, canvas) {
    super();
    this.shape = shape;
    this.canvas = canvas;
  }

  execute() {
    this.canvas.add(this.shape);
  }

  undo() {
    this.canvas.remove(this.shape);
  }
}

class CommandManager {
  constructor() {
    this.undoStack = [];
    this.redoStack = [];
  }

  execute(command) {
    command.execute();
    this.undoStack.push(command);
    this.redoStack = [];
  }

  undo() {
    if (this.undoStack.length === 0) return;
    const command = this.undoStack.pop();
    command.undo();
    this.redoStack.push(command);
  }

  redo() {
    if (this.redoStack.length === 0) return;
    const command = this.redoStack.pop();
    command.execute();
    this.undoStack.push(command);
  }
}

// Usage
const canvas = {
  shapes: [],
  add(shape) {
    this.shapes.push(shape);
    console.log("Added", shape);
  },
  remove(shape) {
    this.shapes = this.shapes.filter((s) => s !== shape);
    console.log("Removed", shape);
  },
};

const manager = new CommandManager();
manager.execute(new DrawCommand("Circle", canvas));
manager.execute(new DrawCommand("Square", canvas));

manager.undo();
manager.redo();
```

### ✅ Key Takeaways

- Command pattern **encapsulates operations**
- Undo/redo stacks allow **multi-level history**
- Works for **drawing apps, text editors, or any reversible actions**

---

## 23. Design a **Shopping Cart System** with Discounts, Taxes, and Promotions

### 🔹 Concept

- Cart contains **items**
- Each item has **price and quantity**
- Discounts, taxes, promotions applied at checkout
- OOP allows **extensible discount strategies**

---

### 🔹 Implementation

```js
class Item {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}

class CartItem {
  constructor(item, quantity) {
    this.item = item;
    this.quantity = quantity;
  }

  get total() {
    return this.item.price * this.quantity;
  }
}

class Discount {
  apply(amount) {
    return amount; // Base: no discount
  }
}

class PercentageDiscount extends Discount {
  constructor(percent) {
    super();
    this.percent = percent;
  }

  apply(amount) {
    return amount - amount * (this.percent / 100);
  }
}

class Cart {
  constructor() {
    this.items = [];
    this.discount = null;
    this.taxPercent = 10;
  }

  addItem(item, quantity) {
    this.items.push(new CartItem(item, quantity));
  }

  setDiscount(discount) {
    this.discount = discount;
  }

  get total() {
    let amount = this.items.reduce((sum, ci) => sum + ci.total, 0);
    if (this.discount) amount = this.discount.apply(amount);
    amount += amount * (this.taxPercent / 100);
    return amount;
  }
}

// Usage
const cart = new Cart();
cart.addItem(new Item("Laptop", 1000), 1);
cart.addItem(new Item("Mouse", 50), 2);

cart.setDiscount(new PercentageDiscount(10));
console.log(cart.total); // 1039 (after 10% discount + 10% tax)
```

### ✅ Key Takeaways

- Use **classes for Items, Cart, Discounts**
- Support multiple discount types with **strategy pattern**
- Easy to extend: promotions, bundles, coupons

---

### 🔑 Quick Summary (Q21–Q23)

| Scenario        | Key Design Principles             | Patterns Used                    |
| --------------- | --------------------------------- | -------------------------------- |
| User Management | Roles → Permissions → Users       | RBAC (Role-Based Access Control) |
| Undo-Redo       | Command pattern, undo/redo stacks | Command Pattern                  |
| Shopping Cart   | Cart → Items → Discounts → Taxes  | Strategy pattern for discounts   |

---

## 24. Implement **Dynamic Feature Toggles** in a Node.js App

### 🔹 Concept

- Enable/disable features at runtime without redeploying
- Useful for **A/B testing, gradual rollout**

---

### 🔹 Implementation (Class-based)

```js
class FeatureToggle {
  constructor() {
    this.features = new Map();
  }

  enable(feature) {
    this.features.set(feature, true);
  }

  disable(feature) {
    this.features.set(feature, false);
  }

  isEnabled(feature) {
    return this.features.get(feature) || false;
  }
}

// Usage
const features = new FeatureToggle();
features.enable("newDashboard");

if (features.isEnabled("newDashboard")) {
  console.log("Show new dashboard");
} else {
  console.log("Show old dashboard");
}
```

### ✅ Key Takeaways

- Centralized **feature control**
- Can integrate with **DB or remote config**
- Supports **dynamic toggling at runtime**

---

## 25. Real-Time Collaborative Document Editor Using OOP Principles

### 🔹 Concept

- Multiple users edit a document simultaneously
- Maintain **shared document state**
- Notify all users about changes (Observer pattern)
- Track changes for **undo/redo** (Command pattern)

---

### 🔹 Implementation (Simplified)

```js
class Document {
  constructor() {
    this.content = "";
    this.subscribers = [];
  }

  subscribe(user) {
    this.subscribers.push(user);
  }

  notify() {
    this.subscribers.forEach((sub) => sub.update(this.content));
  }

  applyChange(change) {
    this.content += change;
    this.notify();
  }
}

class User {
  constructor(name) {
    this.name = name;
  }

  update(content) {
    console.log(`${this.name} sees content: ${content}`);
  }

  edit(doc, change) {
    doc.applyChange(change);
  }
}

// Usage
const doc = new Document();
const user1 = new User("Alice");
const user2 = new User("Bob");

doc.subscribe(user1);
doc.subscribe(user2);

user1.edit(doc, "Hello ");
user2.edit(doc, "World!");
```

### ✅ Key Takeaways

- **Observer pattern** for real-time updates
- **Command pattern** can manage undo/redo
- Supports multiple users concurrently

---

## 26. Message Queue Processor with Retry and Failure Handling

### 🔹 Concept

- Process messages asynchronously
- Retry failed messages
- Move permanently failed messages to **dead-letter queue**

---

### 🔹 Implementation

```js
class QueueProcessor {
  constructor(maxRetries = 3) {
    this.queue = [];
    this.maxRetries = maxRetries;
  }

  addMessage(msg) {
    this.queue.push({ msg, retries: 0 });
    this.process();
  }

  async process() {
    while (this.queue.length) {
      const { msg, retries } = this.queue.shift();
      try {
        await this.handleMessage(msg);
        console.log("Processed:", msg);
      } catch (err) {
        if (retries < this.maxRetries) {
          console.log("Retrying:", msg);
          this.queue.push({ msg, retries: retries + 1 });
        } else {
          console.error("Failed permanently:", msg);
        }
      }
    }
  }

  async handleMessage(msg) {
    // Simulate processing with 50% failure chance
    if (Math.random() > 0.5) throw new Error("Failed");
  }
}

// Usage
const processor = new QueueProcessor();
processor.addMessage("Task 1");
processor.addMessage("Task 2");
```

### ✅ Key Takeaways

- Supports **retries, failure handling**
- Can extend with **dead-letter queues or backoff**
- Useful for **job queues, email delivery, API calls**

---

## 27. Real-Time Notification Dispatcher with Multiple Delivery Channels

### 🔹 Concept

- Deliver notifications via **email, SMS, push**
- Dynamically add/remove channels
- Fallback mechanism if a channel fails

---

### 🔹 Implementation

```js
class NotificationDispatcher {
  constructor() {
    this.channels = [];
  }

  addChannel(channel) {
    this.channels.push(channel);
  }

  async notify(message) {
    for (const channel of this.channels) {
      try {
        await channel.send(message);
      } catch (err) {
        console.error(`Channel failed: ${err.message}`);
      }
    }
  }
}

// Example channels
class EmailChannel {
  async send(message) {
    console.log("Email:", message);
  }
}

class SMSChannel {
  async send(message) {
    console.log("SMS:", message);
  }
}

// Usage
const dispatcher = new NotificationDispatcher();
dispatcher.addChannel(new EmailChannel());
dispatcher.addChannel(new SMSChannel());

dispatcher.notify("Hello Users!");
```

### ✅ Key Takeaways

- Supports multiple **delivery channels**
- Channels are **interchangeable and pluggable**
- Can add **retry or fallback per channel**

---

### 🔑 Quick Summary (Q24–Q27)

| Scenario                | Key Design Principles             | Patterns Used        |
| ----------------------- | --------------------------------- | -------------------- |
| Feature Toggles         | Dynamic control at runtime        | Singleton / Config   |
| Collaborative Editor    | Shared state + real-time updates  | Observer, Command    |
| Message Queue           | Async processing + retries        | Queue pattern, Retry |
| Notification Dispatcher | Multi-channel delivery + fallback | Strategy, Facade     |

---

## 28. Implement a **Plugin Architecture** for Extending App Functionality

### 🔹 Concept

- Allow the app to be **extended dynamically** with plugins
- Plugins follow a **defined interface**
- Main app **loads and executes plugins** without knowing internal details

---

### 🔹 Implementation

```js
class App {
  constructor() {
    this.plugins = [];
  }

  registerPlugin(plugin) {
    if (plugin.init && typeof plugin.init === "function") {
      this.plugins.push(plugin);
      plugin.init(this); // optional setup
    }
  }

  run() {
    this.plugins.forEach((plugin) => plugin.execute());
  }
}

// Example plugin
class LoggerPlugin {
  init(app) {
    console.log("Logger plugin initialized");
  }

  execute() {
    console.log("Logging action performed");
  }
}

// Usage
const app = new App();
app.registerPlugin(new LoggerPlugin());
app.run();
```

### ✅ Key Takeaways

- Promotes **modularity and extensibility**
- Plugins are **loosely coupled**
- Useful for **CMS, IDEs, or modular apps**

---

## 29. Design a **Rate-Limiting System** for APIs Using OOP

### 🔹 Concept

- Limit number of requests per **user/IP/time window**
- Prevents abuse and protects resources

---

### 🔹 Implementation

```js
class RateLimiter {
  constructor(limit = 5, windowMs = 60000) {
    this.limit = limit;
    this.windowMs = windowMs;
    this.requests = new Map(); // user -> timestamps
  }

  isAllowed(userId) {
    const now = Date.now();
    if (!this.requests.has(userId)) this.requests.set(userId, []);
    const timestamps = this.requests.get(userId);

    // Remove timestamps outside window
    while (timestamps.length && now - timestamps[0] > this.windowMs) {
      timestamps.shift();
    }

    if (timestamps.length < this.limit) {
      timestamps.push(now);
      return true;
    }

    return false;
  }
}

// Usage
const limiter = new RateLimiter(3, 10000); // 3 requests per 10 sec

const userId = "user1";
console.log(limiter.isAllowed(userId)); // true
console.log(limiter.isAllowed(userId)); // true
console.log(limiter.isAllowed(userId)); // true
console.log(limiter.isAllowed(userId)); // false (rate limited)
```

### ✅ Key Takeaways

- Track requests per **user/IP**
- Sliding window or fixed window strategies
- Can extend to **distributed caches** (Redis) in production

---

## 30. Implement **Multi-Tenancy** in a Node.js App Using OOP Patterns

### 🔹 Concept

- Support **multiple tenants (clients)** in a single app
- Each tenant has **isolated data and config**
- Patterns: Factory for tenant-specific services, Repository for data access

---

### 🔹 Implementation (Simplified)

```js
class Tenant {
  constructor(id, name, config) {
    this.id = id;
    this.name = name;
    this.config = config;
  }
}

class TenantServiceFactory {
  constructor() {
    this.tenants = new Map();
  }

  registerTenant(id, name, config) {
    this.tenants.set(id, new Tenant(id, name, config));
  }

  getServiceForTenant(id) {
    const tenant = this.tenants.get(id);
    if (!tenant) throw new Error("Tenant not found");

    // Return tenant-specific service instance
    return new TenantService(tenant);
  }
}

class TenantService {
  constructor(tenant) {
    this.tenant = tenant;
  }

  getConfig() {
    return this.tenant.config;
  }

  // Add tenant-specific methods
}

// Usage
const factory = new TenantServiceFactory();
factory.registerTenant("t1", "Tenant1", { db: "db1" });
factory.registerTenant("t2", "Tenant2", { db: "db2" });

const service1 = factory.getServiceForTenant("t1");
console.log(service1.getConfig()); // { db: "db1" }
```

### ✅ Key Takeaways

- Use **factory or repository pattern** to create tenant-specific services
- Isolate data, configs, and features per tenant
- Can extend to **multi-DB or schema-per-tenant strategies**

---

### 🔑 Quick Summary (Q28–Q30)

| Scenario            | Key Design Principles               | Patterns Used             |
| ------------------- | ----------------------------------- | ------------------------- |
| Plugin Architecture | Extensible, modular                 | Plugin pattern, Interface |
| Rate Limiting       | Request control per user/IP         | Strategy, Sliding window  |
| Multi-Tenancy       | Tenant isolation + dynamic services | Factory, Repository       |

---

## 31. Implement **Deep Cloning** of Complex Objects in JS

### 🔹 Concept

- Deep cloning creates a **new object with copies of all nested objects**
- Changes to clone **don’t affect the original**
- Required for **state management, undo-redo, immutable updates**

---

### 🔹 Implementation

```js
// Using recursion
function deepClone(obj, hash = new WeakMap()) {
  if (obj === null || typeof obj !== "object") return obj;
  if (hash.has(obj)) return hash.get(obj); // Handle circular refs

  const clone = Array.isArray(obj) ? [] : {};
  hash.set(obj, clone);

  for (const key in obj) {
    if (obj.hasOwnProperty(key)) {
      clone[key] = deepClone(obj[key], hash);
    }
  }

  return clone;
}

// Usage
const original = { a: 1, b: { c: 2 } };
const clone = deepClone(original);
clone.b.c = 99;
console.log(original.b.c); // 2
```

### ✅ Key Takeaways

- Avoid `JSON.parse(JSON.stringify())` for:

  - Functions
  - Dates
  - Circular references

- Recursion + WeakMap handles **nested and circular objects**

---

## 32. **Memory Management** in JS Objects & Preventing Leaks in OOP

### 🔹 Concept

- JS uses **automatic garbage collection**
- Memory leaks occur when objects are **still referenced** but no longer needed

---

### 🔹 Common Causes in OOP

1. **Global references** – objects held in global scope unnecessarily
2. **Closures** – keeping references alive unintentionally
3. **Event listeners** – not removed on object destruction
4. **Caches/Maps** – references never cleared

---

### 🔹 Best Practices

```js
class MyClass {
  constructor() {
    this.data = [];
    this.handler = () => console.log("Event triggered");
    document.addEventListener("click", this.handler);
  }

  destroy() {
    // Remove references & listeners
    this.data = null;
    document.removeEventListener("click", this.handler);
    this.handler = null;
  }
}
```

✅ Key Takeaways:

- Remove event listeners
- Nullify references in caches
- Use **WeakMap/WeakSet** for temporary storage
- Avoid global variables in OOP design

---

## 33. **WeakMap & WeakSet** in OOP Designs

### 🔹 Concept

- WeakMap: key = **object**, value = anything; keys **do not prevent GC**
- WeakSet: stores objects; **does not prevent garbage collection**
- Useful for **private data storage without memory leaks**

---

### 🔹 Example: Private Fields in Classes

```js
const privateData = new WeakMap();

class Person {
  constructor(name) {
    privateData.set(this, { name });
  }

  getName() {
    return privateData.get(this).name;
  }
}

const p = new Person("Vikash");
console.log(p.getName()); // Vikash
```

✅ Key Takeaways:

- Provides **true privacy** without exposing fields
- Prevents memory leaks when objects are deleted
- Ideal for **temporary or internal object metadata**

---

## 34. Implement **Immutable Objects** Using JS Classes

### 🔹 Concept

- Immutable objects cannot be **modified after creation**
- Helps in **state management, functional programming, Redux**

---

### 🔹 Implementation

```js
class ImmutablePoint {
  constructor(x, y) {
    Object.defineProperty(this, "x", { value: x, writable: false });
    Object.defineProperty(this, "y", { value: y, writable: false });
    Object.freeze(this); // deep freeze if needed
  }

  move(dx, dy) {
    // return new object instead of modifying
    return new ImmutablePoint(this.x + dx, this.y + dy);
  }
}

// Usage
const point1 = new ImmutablePoint(1, 2);
const point2 = point1.move(3, 4);
console.log(point1); // {x: 1, y: 2}
console.log(point2); // {x: 4, y: 6}
```

✅ Key Takeaways:

- Use `Object.freeze()` for shallow immutability
- Return **new objects** instead of modifying existing ones
- Reduces side-effects and improves predictability

---

### 🔑 Quick Summary (Q31–Q34)

| Topic             | Key Idea                        | JS Features / Pattern                                    |
| ----------------- | ------------------------------- | -------------------------------------------------------- |
| Deep Cloning      | Copy object + nested structures | Recursion + WeakMap                                      |
| Memory Management | Prevent leaks in OOP            | Remove references, listeners, WeakMap/WeakSet            |
| WeakMap / WeakSet | Private data + GC-safe storage  | WeakMap for private fields, WeakSet for tracking objects |
| Immutable Objects | Unchangeable state              | Object.freeze(), return new objects                      |

---

## 35. Design a **Plugin/Event System** with Dynamic Registration

### 🔹 Concept

- Support **registering/unregistering plugins at runtime**
- Plugins can **react to events emitted by the main app**
- Useful for **modular apps, CMS, or IDEs**

---

### 🔹 Implementation

```js
class EventSystem {
  constructor() {
    this.plugins = new Set();
    this.events = new Map(); // eventName -> listeners
  }

  registerPlugin(plugin) {
    this.plugins.add(plugin);
    if (plugin.init) plugin.init(this);
  }

  unregisterPlugin(plugin) {
    this.plugins.delete(plugin);
    if (plugin.destroy) plugin.destroy(this);
  }

  on(event, listener) {
    if (!this.events.has(event)) this.events.set(event, []);
    this.events.get(event).push(listener);
  }

  emit(event, payload) {
    if (!this.events.has(event)) return;
    this.events.get(event).forEach((listener) => listener(payload));
  }
}

// Example plugin
class LoggerPlugin {
  init(eventSystem) {
    eventSystem.on("data", (payload) => console.log("LoggerPlugin:", payload));
  }
}

// Usage
const app = new EventSystem();
const logger = new LoggerPlugin();

app.registerPlugin(logger);
app.emit("data", { message: "Hello World" });

app.unregisterPlugin(logger);
app.emit("data", { message: "Won’t be logged" });
```

### ✅ Key Takeaways

- Plugins are **loosely coupled**
- Supports **dynamic registration/unregistration**
- Event-driven design ensures **scalability and modularity**

---

## 36. Implement **Lazy-Loaded Modules** with Class-Based Design in JS

### 🔹 Concept

- Load **heavy modules only when needed**
- Improves **startup performance**
- Often combined with **singleton pattern** for module instances

---

### 🔹 Implementation (Class-Based Lazy Loader)

```js
class LazyModuleLoader {
  constructor() {
    this.modules = new Map();
  }

  async loadModule(name, importFunc) {
    if (!this.modules.has(name)) {
      const module = await importFunc();
      this.modules.set(name, module);
    }
    return this.modules.get(name);
  }
}

// Usage
const loader = new LazyModuleLoader();

// Lazy load a module only when needed
async function useFeature() {
  const mathModule = await loader.loadModule(
    "math",
    async () => await import("./math.js")
  );
  console.log(mathModule.add(2, 3));
}
```

### 🔹 Benefits

- Reduces **initial load time**
- Modules are **loaded once and cached**
- Works well in **large apps and microfrontends**

### ✅ Key Takeaways

- Use **Map** to store loaded modules
- Use **dynamic `import()`** for lazy loading
- Integrate with **singleton or factory pattern** if needed

---

### 🔑 Quick Summary (Q35–Q36)

| Topic               | Key Idea                             | Pattern / Feature                    |
| ------------------- | ------------------------------------ | ------------------------------------ |
| Plugin/Event System | Dynamic plugin registration + events | Observer / EventEmitter              |
| Lazy-Loaded Modules | Load modules only when needed        | Singleton + dynamic import + caching |

---

## 37. **Dependency Injection** in a Node.js Class-Based System

### 🔹 Concept

- **Dependencies are “injected”** into a class instead of creating them inside
- Promotes **loose coupling, testability, and flexibility**
- Common in **services, controllers, and repositories**

---

### 🔹 Implementation

```js
// Service dependency
class Logger {
  log(message) {
    console.log(`[LOG]: ${message}`);
  }
}

// Class that depends on Logger
class UserService {
  constructor(logger) {
    this.logger = logger; // Injected dependency
  }

  createUser(name) {
    this.logger.log(`Creating user: ${name}`);
    return { id: Date.now(), name };
  }
}

// Usage
const logger = new Logger();
const userService = new UserService(logger);

userService.createUser("Vikash");
```

### 🔹 Benefits

- Easier to **mock dependencies** in tests
- Classes are **not tightly coupled** to specific implementations
- Can **swap implementations** at runtime

---

### ✅ Key Takeaways

- Pass dependencies via **constructor or setter**
- Improves **testability, flexibility, and modularity**
- Common in **Node.js backend architectures (services, controllers)**

---

## 38. Implement **Role-Based Access Control (RBAC) Dynamically** in a JS Backend

### 🔹 Concept

- Assign **roles** to users
- Roles define **permissions**
- Check permissions **at runtime**, dynamically

---

### 🔹 Implementation

```js
class Role {
  constructor(name) {
    this.name = name;
    this.permissions = new Set();
  }

  addPermission(permission) {
    this.permissions.add(permission);
  }

  hasPermission(permission) {
    return this.permissions.has(permission);
  }
}

class User {
  constructor(username) {
    this.username = username;
    this.roles = [];
  }

  addRole(role) {
    this.roles.push(role);
  }

  can(permission) {
    return this.roles.some((role) => role.hasPermission(permission));
  }
}

// Dynamic RBAC Example
const admin = new Role("admin");
admin.addPermission("read");
admin.addPermission("write");

const editor = new Role("editor");
editor.addPermission("read");

const user1 = new User("Vikash");
user1.addRole(admin);

const user2 = new User("Alice");
user2.addRole(editor);

console.log(user1.can("write")); // true
console.log(user2.can("write")); // false
```

### ✅ Key Takeaways

- Roles can be **added/modified dynamically**
- Users can have **multiple roles**
- RBAC checks **permissions at runtime**, suitable for **backend APIs**

---

### 🔑 Quick Summary (Q37–Q38)

| Topic                | Key Idea                                   | Implementation Pattern                        |
| -------------------- | ------------------------------------------ | --------------------------------------------- |
| Dependency Injection | Pass dependencies instead of creating them | Constructor injection, setter injection       |
| Dynamic RBAC         | Assign roles + permissions at runtime      | Role & User classes, dynamic permission check |

---

## 39. Design a **File Upload Manager** with Chunking and Retries

### 🔹 Concept

- Split **large files** into chunks and upload sequentially or in parallel
- Retry failed chunks automatically
- Useful for **robust file upload in unreliable networks**

---

### 🔹 Implementation

```js
class FileUploadManager {
  constructor(maxRetries = 3, chunkSize = 1024 * 1024) {
    this.maxRetries = maxRetries;
    this.chunkSize = chunkSize;
  }

  async upload(file) {
    const chunks = this.splitFile(file);
    for (let i = 0; i < chunks.length; i++) {
      await this.uploadChunkWithRetry(chunks[i], i);
    }
    console.log("File uploaded successfully!");
  }

  splitFile(file) {
    const chunks = [];
    for (let i = 0; i < file.size; i += this.chunkSize) {
      chunks.push(file.slice(i, i + this.chunkSize));
    }
    return chunks;
  }

  async uploadChunkWithRetry(chunk, index) {
    let attempts = 0;
    while (attempts < this.maxRetries) {
      try {
        await this.uploadChunk(chunk, index);
        return;
      } catch (err) {
        attempts++;
        console.log(`Retry ${attempts} for chunk ${index}`);
      }
    }
    throw new Error(
      `Failed to upload chunk ${index} after ${this.maxRetries} retries`
    );
  }

  async uploadChunk(chunk, index) {
    // Simulate upload API call
    if (Math.random() < 0.2) throw new Error("Network Error");
    console.log(`Uploaded chunk ${index}`);
  }
}

// Usage
const file = { size: 5 * 1024 * 1024, slice: (start, end) => ({ start, end }) }; // 5 MB dummy file
const uploader = new FileUploadManager();
uploader.upload(file);
```

### ✅ Key Takeaways

- **Chunking** allows resuming failed uploads
- **Retries per chunk** improve reliability
- Can be extended with **parallel uploads, progress tracking, and cancelation**

---

## 40. Implement **Circuit Breaker Pattern** for API Calls in Node.js

### 🔹 Concept

- Protects services from repeated failures
- Circuit has **3 states**:

  1. **Closed** – normal requests
  2. **Open** – stop requests temporarily
  3. **Half-Open** – test if service recovered

- Useful for **resilient microservices**

---

### 🔹 Implementation

```js
class CircuitBreaker {
  constructor(requestFunc, failureThreshold = 3, cooldownTime = 5000) {
    this.requestFunc = requestFunc;
    this.failureThreshold = failureThreshold;
    this.cooldownTime = cooldownTime;

    this.failures = 0;
    this.state = "CLOSED";
    this.nextAttempt = Date.now();
  }

  async call(...args) {
    if (this.state === "OPEN") {
      if (Date.now() > this.nextAttempt) {
        this.state = "HALF-OPEN";
      } else {
        throw new Error("Circuit is OPEN");
      }
    }

    try {
      const result = await this.requestFunc(...args);
      this.reset();
      return result;
    } catch (err) {
      this.failures++;
      if (this.failures >= this.failureThreshold) {
        this.state = "OPEN";
        this.nextAttempt = Date.now() + this.cooldownTime;
        console.log("Circuit opened!");
      }
      throw err;
    }
  }

  reset() {
    this.failures = 0;
    this.state = "CLOSED";
  }
}

// Usage
async function unstableAPI() {
  if (Math.random() < 0.5) throw new Error("API failed");
  return "Success";
}

const breaker = new CircuitBreaker(unstableAPI, 2, 3000);

(async () => {
  for (let i = 0; i < 10; i++) {
    try {
      const res = await breaker.call();
      console.log(res);
    } catch (err) {
      console.error(err.message);
    }
    await new Promise((r) => setTimeout(r, 500));
  }
})();
```

### ✅ Key Takeaways

- Prevents **cascading failures**
- **Tracks failures** and opens circuit automatically
- Supports **half-open state** to test service recovery

---

### 🔑 Quick Summary (Q39–Q40)

| Scenario            | Key Idea                           | Pattern / Feature          |
| ------------------- | ---------------------------------- | -------------------------- |
| File Upload Manager | Chunked + retry upload             | Retry mechanism + chunking |
| Circuit Breaker     | Stop failing API calls temporarily | Circuit Breaker pattern    |

---
