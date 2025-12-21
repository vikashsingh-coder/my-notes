**Core OOP & JavaScript Concepts** questions (medium → advanced level).

---

## **1. How does JavaScript handle inheritance for primitive vs reference types?**

### **Primitives**

- Primitives: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`
- They are **passed by value**
- They **do NOT participate in inheritance**

```js
let a = 10;
let b = a;
b = 20;

console.log(a); // 10
```

👉 No prototype chain involved.

---

### **Reference Types (Objects, Arrays, Functions)**

- Passed by **reference**
- Inheritance happens via **prototype chain**

```js
function Person(name) {
  this.name = name;
}

Person.prototype.sayHi = function () {
  return `Hi, I'm ${this.name}`;
};

const user = new Person("Vikash");
console.log(user.sayHi());
```

👉 JS inheritance works **only with objects**, using prototypes.

---

### **Key Interview Line**

> JavaScript inheritance applies only to reference types through the prototype chain; primitives are immutable values and cannot be inherited.

---

## **2. Explain method overloading and why JS does not support it natively. How can you simulate it?**

### **What is Method Overloading?**

- Same method name
- Different parameter lists

```java
add(int a, int b)
add(int a, int b, int c)
```

---

### **Why JS Doesn’t Support It**

- JS is **dynamically typed**
- Function parameters are **not type-checked**
- Last function definition overrides previous ones

```js
function add(a, b) {}
function add(a, b, c) {} // overrides previous
```

---

### **Simulating Method Overloading**

#### **1. Using arguments.length**

```js
function add() {
  if (arguments.length === 2) {
    return arguments[0] + arguments[1];
  }
  if (arguments.length === 3) {
    return arguments[0] + arguments[1] + arguments[2];
  }
}
```

---

#### **2. Using default parameters**

```js
function add(a, b, c = 0) {
  return a + b + c;
}
```

---

#### **3. Using options object (best practice)**

```js
function createUser({ name, age, role = "user" }) {
  return { name, age, role };
}
```

---

### **Key Interview Line**

> JavaScript doesn’t support method overloading natively due to dynamic typing, but it can be simulated using argument checks or options objects.

---

## **3. How does dynamic typing affect OOP design in JavaScript?**

### **Pros**

✔ Faster development
✔ Flexible APIs
✔ Easier prototyping

### **Cons**

❌ Runtime errors
❌ Harder to enforce contracts
❌ Large systems become fragile

---

### **Impact on OOP Design**

- Interfaces are **implicit**
- Type safety must be enforced via:

  - Validation
  - Documentation
  - Tests
  - TypeScript (recommended)

```js
function processPayment(payment) {
  if (typeof payment.pay !== "function") {
    throw new Error("Invalid payment object");
  }
  payment.pay();
}
```

---

### **Best Practices**

- Use **composition over inheritance**
- Validate inputs
- Prefer **TypeScript** in large apps

---

### **Key Interview Line**

> Dynamic typing increases flexibility but shifts type safety from compile-time to runtime, making validation and clear contracts essential in OOP design.

---

## **4. What are getter and setter methods in JS classes, and when should you use them?**

### **Getters & Setters**

- Control access to object properties
- Look like properties but behave like methods

```js
class User {
  constructor(email) {
    this._email = email;
  }

  get email() {
    return this._email;
  }

  set email(value) {
    if (!value.includes("@")) {
      throw new Error("Invalid email");
    }
    this._email = value;
  }
}
```

```js
const user = new User("test@mail.com");
user.email = "new@mail.com"; // setter
console.log(user.email); // getter
```

---

### **When to Use**

✔ Validation
✔ Computed properties
✔ Encapsulation
✔ Backward compatibility

---

### **When NOT to Use**

❌ Heavy logic (can confuse readers)

---

### **Key Interview Line**

> Getters and setters provide controlled access to properties while preserving a clean, property-like API.

---

## **5. Explain private fields (#) in JS classes and how they differ from closures**

### **Private Fields (#)**

- Introduced in **ES2022**
- Truly private at language level

```js
class BankAccount {
  #balance = 0;

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}
```

```js
const acc = new BankAccount();
acc.#balance; // ❌ Syntax Error
```

---

### **Closures for Privacy**

```js
function createCounter() {
  let count = 0;

  return {
    increment() {
      count++;
    },
    getCount() {
      return count;
    },
  };
}
```

---

### **Differences**

| Feature       | Private Fields (#) | Closures                          |
| ------------- | ------------------ | --------------------------------- |
| Syntax        | Class-based        | Function-based                    |
| Performance   | Faster             | Slower (new closure per instance) |
| Enforcement   | Language-level     | Convention                        |
| Accessibility | Only inside class  | Via returned functions            |

---

### **Key Interview Line**

> Private fields provide true encapsulation at the language level, while closures offer functional privacy but with higher memory overhead.

---

## 🔥 Interview Summary (Quick Recall)

- JS inheritance → **prototype-based**
- No native overloading → simulate with arguments
- Dynamic typing → flexibility + runtime validation
- Getters/setters → controlled access
- `#private` fields → true encapsulation

---

## **6. How would you implement read-only properties in a JS object or class?**

### **Approach 1: Getter without Setter (Recommended in Classes)**

```js
class User {
  constructor(id) {
    this._id = id;
  }

  get id() {
    return this._id;
  }
}

const user = new User(101);
user.id = 200; // ❌ ignored (no setter)
console.log(user.id); // 101
```

✔ Clean
✔ OOP-friendly
✔ Encapsulated

---

### **Approach 2: Object.defineProperty()**

```js
const user = {};
Object.defineProperty(user, "id", {
  value: 101,
  writable: false,
  configurable: false,
  enumerable: true,
});

user.id = 200; // ❌ no effect
```

✔ True immutability at property level

---

### **Approach 3: Private Field + Getter**

```js
class Product {
  #price;
  constructor(price) {
    this.#price = price;
  }

  get price() {
    return this.#price;
  }
}
```

✔ Strong encapsulation
✔ Modern JS

---

### **Interview Line**

> Read-only properties can be implemented using getters, non-writable properties, or private fields to enforce immutability.

---

## **7. How does Object.freeze() relate to immutability in OOP design?**

### **What Object.freeze() Does**

- Prevents:

  - Adding properties
  - Removing properties
  - Modifying existing properties

```js
const user = Object.freeze({
  name: "Vikash",
  age: 25,
});

user.age = 30; // ❌ ignored
```

---

### **Important Caveat: Shallow Immutability**

```js
const obj = Object.freeze({
  address: { city: "Delhi" },
});

obj.address.city = "Mumbai"; // ✅ allowed
```

👉 Nested objects are **still mutable**

---

### **OOP Design Usage**

✔ Prevent accidental mutations
✔ Value objects (DTOs)
✔ Functional-style design

---

### **Alternatives**

- Deep freeze (recursive)
- Immutable libraries (Immer, Immutable.js)

---

### **Interview Line**

> Object.freeze() enforces shallow immutability, useful for protecting object state in OOP but insufficient for deeply nested structures.

---

## **8. Explain duck typing in JavaScript and its pros and cons in OOP**

### **What is Duck Typing?**

> “If it looks like a duck and quacks like a duck, it is a duck.”

JS checks **behavior**, not type.

```js
function makeSound(animal) {
  animal.speak();
}

const dog = {
  speak() {
    console.log("Bark");
  },
};

makeSound(dog); // Bark
```

---

### **Pros**

✔ Flexible APIs
✔ Loose coupling
✔ Better polymorphism

---

### **Cons**

❌ Runtime errors
❌ No compile-time safety
❌ Harder to debug in large apps

---

### **Best Practice**

- Validate behavior
- Use TypeScript interfaces in large systems

---

### **Interview Line**

> Duck typing enables flexible polymorphism by relying on object behavior rather than inheritance, but increases runtime risk.

---

## **9. How do symbols work in JS for encapsulation?**

### **What is a Symbol?**

- A **unique, non-enumerable** primitive
- Often used as hidden object keys

```js
const _id = Symbol("id");

class User {
  constructor(id) {
    this[_id] = id;
  }

  getId() {
    return this[_id];
  }
}
```

```js
const user = new User(10);
console.log(Object.keys(user)); // []
```

---

### **Why Use Symbols?**

✔ Avoid property name collisions
✔ Semi-private fields
✔ Hidden internal metadata

---

### **Limitations**

❌ Not truly private (can be accessed if symbol reference is known)

---

### **Private Fields vs Symbols**

| Feature    | Symbol   | #private   |
| ---------- | -------- | ---------- |
| Privacy    | Soft     | Strong     |
| ES Support | Older    | ES2022     |
| Access     | Possible | Impossible |

---

### **Interview Line**

> Symbols provide soft encapsulation by creating non-colliding, hidden object keys, useful before private fields existed.

---

## **10. What is method chaining and how can you implement it in JS classes?**

### **What is Method Chaining?**

- Calling multiple methods in a single statement
- Each method returns `this`

```js
user.setName("Vikash").setAge(25).save();
```

---

### **Implementation Example**

```js
class QueryBuilder {
  constructor() {
    this.query = "";
  }

  select(fields) {
    this.query += `SELECT ${fields} `;
    return this;
  }

  from(table) {
    this.query += `FROM ${table} `;
    return this;
  }

  where(condition) {
    this.query += `WHERE ${condition}`;
    return this;
  }

  build() {
    return this.query;
  }
}
```

```js
const query = new QueryBuilder()
  .select("*")
  .from("users")
  .where("age > 18")
  .build();

console.log(query);
```

---

### **Why It’s Important**

✔ Fluent APIs
✔ Cleaner code
✔ Widely used (jQuery, Mongoose, Prisma)

---

### **Interview Line**

> Method chaining improves API readability by returning the same object instance from each method.

---

## 🔥 Final Quick Recap

| Concept         | Key Idea                 |
| --------------- | ------------------------ |
| Read-only props | Getters / defineProperty |
| Object.freeze   | Shallow immutability     |
| Duck typing     | Behavior over type       |
| Symbols         | Hidden object keys       |
| Method chaining | Return `this`            |

---

## **11. Explain the Builder Pattern and implement a simple object builder in JS**

### **What is the Builder Pattern?**

The **Builder Pattern** is used to:

- Construct **complex objects step by step**
- Avoid constructors with too many parameters
- Improve **readability and immutability**

👉 Especially useful when many optional fields exist.

---

### **When to Use**

✔ Complex object creation
✔ Optional configurations
✔ Fluent APIs

---

### **JS Implementation (Fluent Builder)**

```js
class User {
  constructor(builder) {
    this.name = builder.name;
    this.email = builder.email;
    this.age = builder.age;
    this.role = builder.role;
  }
}

class UserBuilder {
  setName(name) {
    this.name = name;
    return this;
  }

  setEmail(email) {
    this.email = email;
    return this;
  }

  setAge(age) {
    this.age = age;
    return this;
  }

  setRole(role) {
    this.role = role;
    return this;
  }

  build() {
    return new User(this);
  }
}

// Usage
const user = new UserBuilder()
  .setName("Vikash")
  .setEmail("vikash@mail.com")
  .setRole("Admin")
  .build();

console.log(user);
```

---

### **Why This Is Better Than Constructor**

❌ `new User(name, email, age, role)` → unreadable
✔ Step-by-step, self-documenting

---

### **Interview Line**

> The Builder pattern separates object construction from representation and is ideal for complex, configurable objects.

---

## **12. How would you implement a Prototype-based cloning system in JS?**

### **What is the Prototype Pattern?**

- Create objects by **cloning existing ones**
- Avoid costly object creation
- Common in performance-sensitive systems

---

### **JS Native Support**

JavaScript is **prototype-based by design**.

---

### **Implementation Using `Object.create()`**

```js
const baseConfig = {
  theme: "dark",
  language: "en",
  clone() {
    return Object.create(this);
  },
};

const userConfig = baseConfig.clone();
userConfig.language = "fr";

console.log(userConfig.theme); // dark (inherited)
console.log(userConfig.language); // fr
```

---

### **Deep Clone Variant**

```js
function clone(obj) {
  return structuredClone(obj); // modern & safe
}
```

---

### **Use Cases**

✔ Game objects
✔ Configuration templates
✔ Performance-critical systems

---

### **Interview Line**

> The Prototype pattern creates new objects by cloning existing ones, leveraging JavaScript’s prototype chain for efficient object creation.

---

## **13. How would you design a state machine using OOP in JS?**

### **What is a State Machine?**

- Object behavior changes based on **internal state**
- Avoids large `if/else` or `switch` blocks

---

### **Example: Order State Machine**

#### **State Interface**

```js
class OrderState {
  next(order) {}
  getStatus() {}
}
```

---

#### **Concrete States**

```js
class PendingState extends OrderState {
  next(order) {
    order.setState(new ShippedState());
  }
  getStatus() {
    return "Pending";
  }
}

class ShippedState extends OrderState {
  next(order) {
    order.setState(new DeliveredState());
  }
  getStatus() {
    return "Shipped";
  }
}

class DeliveredState extends OrderState {
  next() {
    throw new Error("Order already delivered");
  }
  getStatus() {
    return "Delivered";
  }
}
```

---

#### **Context**

```js
class Order {
  constructor() {
    this.state = new PendingState();
  }

  setState(state) {
    this.state = state;
  }

  next() {
    this.state.next(this);
  }

  status() {
    return this.state.getStatus();
  }
}
```

---

#### **Usage**

```js
const order = new Order();

console.log(order.status()); // Pending
order.next();
console.log(order.status()); // Shipped
order.next();
console.log(order.status()); // Delivered
```

---

### **Benefits**

✔ Open/Closed Principle
✔ Cleaner logic
✔ Easy to add new states

---

### **Interview Line**

> A state machine encapsulates state-specific behavior into separate classes, eliminating conditional logic and improving scalability.

---

## 🔥 Quick Interview Summary

| Pattern   | Key Benefit               |
| --------- | ------------------------- |
| Builder   | Clean object construction |
| Prototype | Efficient cloning         |
| State     | Behavior based on state   |

---

## **14. Mediator Pattern – Coordinating Multiple JS Objects**

### **What is the Mediator Pattern?**

The **Mediator pattern**:

- Centralizes communication between objects
- Objects don’t talk to each other directly
- Reduces tight coupling

👉 Think **chat room**, **form validation**, **UI components coordination**

---

### **When to Use**

✔ Complex object interactions
✔ Avoid circular dependencies
✔ UI state coordination

---

### **Example: Chat Room Mediator**

```js
class ChatMediator {
  constructor() {
    this.users = [];
  }

  register(user) {
    this.users.push(user);
    user.mediator = this;
  }

  send(message, fromUser) {
    this.users.forEach((user) => {
      if (user !== fromUser) {
        user.receive(message);
      }
    });
  }
}

class User {
  constructor(name) {
    this.name = name;
  }

  send(message) {
    this.mediator.send(message, this);
  }

  receive(message) {
    console.log(`${this.name} received: ${message}`);
  }
}

// Usage
const mediator = new ChatMediator();
const alice = new User("Alice");
const bob = new User("Bob");

mediator.register(alice);
mediator.register(bob);

alice.send("Hello Bob!");
```

---

### **Interview Line**

> The Mediator pattern reduces coupling by centralizing communication logic in a mediator object.

---

## **15. Chain of Responsibility Pattern in JS**

### **What is Chain of Responsibility?**

- Pass a request along a chain of handlers
- Each handler decides to process or pass it forward

👉 Common in **middlewares, logging, validation, auth**

---

### **Example: Logging Levels**

```js
class Logger {
  setNext(next) {
    this.next = next;
    return next;
  }

  log(level, message) {
    if (this.next) {
      this.next.log(level, message);
    }
  }
}

class InfoLogger extends Logger {
  log(level, message) {
    if (level === "info") {
      console.log("INFO:", message);
    } else {
      super.log(level, message);
    }
  }
}

class ErrorLogger extends Logger {
  log(level, message) {
    if (level === "error") {
      console.log("ERROR:", message);
    } else {
      super.log(level, message);
    }
  }
}
```

```js
// Usage
const info = new InfoLogger();
const error = new ErrorLogger();

info.setNext(error);

info.log("info", "App started");
info.log("error", "Something broke");
```

---

### **Interview Line**

> Chain of Responsibility decouples request senders from handlers by allowing multiple handlers to process a request sequentially.

---

## **16. Adapter Pattern – Integrating Incompatible APIs**

### **What is the Adapter Pattern?**

- Converts one interface into another
- Allows incompatible systems to work together

👉 Very common in **third-party integrations**

---

### **Example: Payment Gateway Adapter**

#### **Existing API**

```js
class PayPal {
  makePayment(amount) {
    console.log(`Paid ${amount} using PayPal`);
  }
}
```

#### **Expected Interface**

```js
class PaymentProcessor {
  pay(amount) {}
}
```

---

#### **Adapter**

```js
class PayPalAdapter extends PaymentProcessor {
  constructor(paypal) {
    super();
    this.paypal = paypal;
  }

  pay(amount) {
    this.paypal.makePayment(amount);
  }
}
```

---

#### **Usage**

```js
function checkout(paymentProcessor) {
  paymentProcessor.pay(100);
}

const paypal = new PayPal();
const adapter = new PayPalAdapter(paypal);

checkout(adapter);
```

---

### **Interview Line**

> Adapter enables interoperability by translating one interface into another without modifying existing code.

---

## **17. Observer Pattern with Multiple Event Types**

### **What is Observer Pattern?**

- Observers subscribe to events
- Notified when state changes

👉 Backbone of **event-driven systems**

---

### **Implementation with Event Types**

```js
class EventBus {
  constructor() {
    this.events = {};
  }

  subscribe(eventType, callback) {
    if (!this.events[eventType]) {
      this.events[eventType] = [];
    }
    this.events[eventType].push(callback);
  }

  unsubscribe(eventType, callback) {
    this.events[eventType] = this.events[eventType]?.filter(
      (cb) => cb !== callback
    );
  }

  publish(eventType, data) {
    this.events[eventType]?.forEach((cb) => cb(data));
  }
}
```

---

### **Usage**

```js
const eventBus = new EventBus();

eventBus.subscribe("ORDER_CREATED", (order) =>
  console.log("Order created:", order)
);

eventBus.subscribe("PAYMENT_SUCCESS", (payment) =>
  console.log("Payment success:", payment)
);

eventBus.publish("ORDER_CREATED", { id: 1 });
eventBus.publish("PAYMENT_SUCCESS", { amount: 500 });
```

---

### **Interview Line**

> Observer pattern enables loose coupling by allowing multiple subscribers to react to different event types independently.

---

## 🔥 Quick Pattern Comparison (Very Interview-Useful)

| Pattern                 | Purpose                     |
| ----------------------- | --------------------------- |
| Mediator                | Centralized communication   |
| Chain of Responsibility | Sequential request handling |
| Adapter                 | Interface compatibility     |
| Observer                | Event-driven communication  |

---

## **18. Facade Pattern – Simplifying a Complex Library API**

### **What is the Facade Pattern?**

The **Facade pattern** provides a **simple, unified interface** over a complex subsystem.

👉 Clients interact with **one simple API** instead of many internal classes.

---

### **When to Use**

✔ Hide complexity
✔ Reduce coupling
✔ Improve readability & maintainability

---

### **Example: Video Processing Library**

#### **Complex Subsystem**

```js
class VideoLoader {
  load(file) {
    console.log("Loading video:", file);
  }
}

class VideoDecoder {
  decode() {
    console.log("Decoding video");
  }
}

class VideoEncoder {
  encode(format) {
    console.log("Encoding video to", format);
  }
}
```

---

### **Facade**

```js
class VideoProcessorFacade {
  constructor() {
    this.loader = new VideoLoader();
    this.decoder = new VideoDecoder();
    this.encoder = new VideoEncoder();
  }

  process(file, format) {
    this.loader.load(file);
    this.decoder.decode();
    this.encoder.encode(format);
  }
}
```

---

### **Usage**

```js
const videoProcessor = new VideoProcessorFacade();
videoProcessor.process("movie.mp4", "H264");
```

---

### **Interview Line**

> Facade simplifies usage by exposing a high-level API while hiding subsystem complexity.

---

## **19. Retry Strategy Using OOP in JavaScript**

### **Problem**

Network requests can fail due to:

- Temporary outages
- Rate limits
- Timeouts

👉 Retrying intelligently improves reliability.

---

### **Solution**

Use **Strategy Pattern** for pluggable retry logic.

---

### **Retry Strategy Interface**

```js
class RetryStrategy {
  async execute(fn) {
    throw new Error("execute() must be implemented");
  }
}
```

---

### **Concrete Strategies**

#### **Fixed Retry**

```js
class FixedRetry extends RetryStrategy {
  constructor(retries) {
    super();
    this.retries = retries;
  }

  async execute(fn) {
    for (let i = 0; i < this.retries; i++) {
      try {
        return await fn();
      } catch (err) {
        if (i === this.retries - 1) throw err;
      }
    }
  }
}
```

---

#### **Exponential Backoff**

```js
class ExponentialBackoff extends RetryStrategy {
  constructor(retries, delay) {
    super();
    this.retries = retries;
    this.delay = delay;
  }

  async execute(fn) {
    let wait = this.delay;
    for (let i = 0; i < this.retries; i++) {
      try {
        return await fn();
      } catch {
        await new Promise((res) => setTimeout(res, wait));
        wait *= 2;
      }
    }
    throw new Error("All retries failed");
  }
}
```

---

### **Usage**

```js
const retry = new ExponentialBackoff(3, 500);

retry
  .execute(() => fetch("https://api.example.com"))
  .then((res) => console.log("Success"))
  .catch((err) => console.error("Failed after retries"));
```

---

### **Interview Line**

> Retry strategies encapsulate failure-handling logic and improve system resilience without modifying core business logic.

---

## **20. Strategy Pattern for Dynamic Sorting Algorithms**

### **What is the Strategy Pattern?**

- Encapsulates algorithms
- Allows runtime switching

👉 Perfect for **sorting**, **pricing**, **validation**, **payment methods**

---

### **Sorting Strategy Interface**

```js
class SortStrategy {
  sort(data) {
    throw new Error("sort() must be implemented");
  }
}
```

---

### **Concrete Sorting Strategies**

```js
class BubbleSort extends SortStrategy {
  sort(data) {
    return [...data].sort((a, b) => a - b);
  }
}

class QuickSort extends SortStrategy {
  sort(data) {
    return [...data].sort((a, b) => a - b); // simplified
  }
}
```

---

### **Context**

```js
class Sorter {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  sort(data) {
    return this.strategy.sort(data);
  }
}
```

---

### **Usage**

```js
const sorter = new Sorter(new BubbleSort());
console.log(sorter.sort([3, 1, 2]));

sorter.setStrategy(new QuickSort());
console.log(sorter.sort([5, 4, 6]));
```

---

### **Interview Line**

> Strategy pattern allows selecting algorithms at runtime without changing the client code.

---

## 🔥 Key Pattern Differences (Interview Gold)

| Pattern  | Purpose                       |
| -------- | ----------------------------- |
| Facade   | Simplifies complex subsystems |
| Strategy | Swaps algorithms dynamically  |
| Adapter  | Makes incompatible APIs work  |
| Chain    | Sequential request processing |

---

## **21. File System Hierarchy (Folders, Files, Permissions) – OOP Design**

### **Requirements**

- Files & folders
- Nested hierarchy
- Permissions (read / write / execute)
- Common operations: add, remove, list

---

### **OOP Design**

We use:

- **Composite Pattern** → file & folder treated uniformly
- **Encapsulation** → permission logic inside classes
- **Polymorphism** → file & folder share interface

---

### **Base Class**

```js
class FileSystemNode {
  constructor(
    name,
    permissions = { read: true, write: false, execute: false }
  ) {
    this.name = name;
    this.permissions = permissions;
  }

  canRead() {
    return this.permissions.read;
  }
  canWrite() {
    return this.permissions.write;
  }

  display(indent = 0) {
    throw new Error("display() must be implemented");
  }
}
```

---

### **File**

```js
class File extends FileSystemNode {
  constructor(name, size, permissions) {
    super(name, permissions);
    this.size = size;
  }

  display(indent = 0) {
    console.log(`${" ".repeat(indent)}📄 ${this.name}`);
  }
}
```

---

### **Folder**

```js
class Folder extends FileSystemNode {
  constructor(name, permissions) {
    super(name, permissions);
    this.children = [];
  }

  add(node) {
    if (!this.canWrite()) throw new Error("Write permission denied");
    this.children.push(node);
  }

  display(indent = 0) {
    console.log(`${" ".repeat(indent)}📁 ${this.name}`);
    this.children.forEach((child) => child.display(indent + 2));
  }
}
```

---

### **Usage**

```js
const root = new Folder("root", { read: true, write: true });
const docs = new Folder("docs", { read: true, write: true });
const file1 = new File("resume.pdf", "1MB");

docs.add(file1);
root.add(docs);
root.display();
```

---

### **Interview Explanation**

> This design uses the Composite pattern so files and folders are treated uniformly. Permissions are encapsulated, and hierarchy is easily extensible.

---

## **22. Real-Time Leaderboard System – OOP Design**

### **Requirements**

- Track user scores
- Real-time updates
- Sorted leaderboard
- Extensible scoring logic

---

### **OOP Design**

We use:

- **Strategy Pattern** → scoring logic
- **Observer Pattern** → real-time updates
- **Encapsulation** → leaderboard logic isolated

---

### **Player**

```js
class Player {
  constructor(id, name) {
    this.id = id;
    this.name = name;
    this.score = 0;
  }

  updateScore(points) {
    this.score += points;
  }
}
```

---

### **Scoring Strategy**

```js
class ScoreStrategy {
  calculate(points) {
    throw new Error("calculate() must be implemented");
  }
}

class SimpleScore extends ScoreStrategy {
  calculate(points) {
    return points;
  }
}
```

---

### **Leaderboard (Subject)**

```js
class Leaderboard {
  constructor(strategy) {
    this.players = new Map();
    this.strategy = strategy;
    this.observers = [];
  }

  addPlayer(player) {
    this.players.set(player.id, player);
  }

  updateScore(playerId, points) {
    const player = this.players.get(playerId);
    const finalPoints = this.strategy.calculate(points);
    player.updateScore(finalPoints);
    this.notify();
  }

  getTopPlayers(limit = 10) {
    return [...this.players.values()]
      .sort((a, b) => b.score - a.score)
      .slice(0, limit);
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  notify() {
    this.observers.forEach((obs) => obs.update(this.getTopPlayers()));
  }
}
```

---

### **Observer (UI / WebSocket Layer)**

```js
class LeaderboardUI {
  update(players) {
    console.log("Leaderboard Updated:");
    players.forEach((p) => console.log(`${p.name}: ${p.score}`));
  }
}
```

---

### **Usage**

```js
const leaderboard = new Leaderboard(new SimpleScore());
const ui = new LeaderboardUI();

leaderboard.subscribe(ui);

leaderboard.addPlayer(new Player(1, "Alice"));
leaderboard.addPlayer(new Player(2, "Bob"));

leaderboard.updateScore(1, 50);
leaderboard.updateScore(2, 70);
```

---

### **How This Scales (Interview Bonus)**

- WebSockets for push updates
- Redis sorted sets for fast ranking
- Horizontal scaling via sharding

---

### **Interview Explanation**

> The leaderboard uses Strategy for scoring logic and Observer for real-time updates. It’s extensible, testable, and scalable.

---

## 🔥 Interview Takeaway Summary

| Scenario          | Pattern Used        |
| ----------------- | ------------------- |
| File System       | Composite           |
| Permissions       | Encapsulation       |
| Leaderboard       | Strategy + Observer |
| Real-time Updates | Observer            |

---

## **23. Task Management System with Task Dependencies (OOP Design)**

### **Requirements**

- Tasks may depend on other tasks
- A task can start only after dependencies are completed
- Track task status
- Prevent circular dependencies

---

### **OOP Design**

Patterns used:

- **Directed Graph concept** (dependencies)
- **Encapsulation** for task state
- **Single Responsibility Principle**
- **Topological-style dependency validation**

---

### **Task Class**

```js
class Task {
  constructor(id, name) {
    this.id = id;
    this.name = name;
    this.dependencies = new Set();
    this.completed = false;
  }

  addDependency(task) {
    if (task === this) {
      throw new Error("Task cannot depend on itself");
    }
    this.dependencies.add(task);
  }

  canStart() {
    return [...this.dependencies].every((t) => t.completed);
  }

  complete() {
    if (!this.canStart()) {
      throw new Error("Dependencies not completed");
    }
    this.completed = true;
  }
}
```

---

### **Task Manager**

```js
class TaskManager {
  constructor() {
    this.tasks = new Map();
  }

  addTask(task) {
    this.tasks.set(task.id, task);
  }

  addDependency(taskId, dependencyId) {
    const task = this.tasks.get(taskId);
    const dep = this.tasks.get(dependencyId);
    task.addDependency(dep);
  }

  completeTask(taskId) {
    const task = this.tasks.get(taskId);
    task.complete();
  }
}
```

---

### **Usage**

```js
const manager = new TaskManager();

const taskA = new Task(1, "Design");
const taskB = new Task(2, "Develop");
const taskC = new Task(3, "Test");

manager.addTask(taskA);
manager.addTask(taskB);
manager.addTask(taskC);

manager.addDependency(2, 1); // Develop depends on Design
manager.addDependency(3, 2); // Test depends on Develop

taskA.complete();
taskB.complete();
taskC.complete();
```

---

### **Interview Explanation**

> Tasks are modeled as nodes in a dependency graph. Each task encapsulates its own state and validates whether it can start based on completed dependencies.

---

## **24. Undo–Redo in a Drawing App Using OOP**

### **Requirements**

- Actions like draw, erase, move
- Undo and redo support
- Scalable for new actions

---

### **OOP Design**

Patterns used:

- **Command Pattern** → encapsulate actions
- **Stack-based history**
- **Encapsulation of execution logic**

---

### **Command Interface**

```js
class Command {
  execute() {
    throw new Error("execute() must be implemented");
  }
  undo() {
    throw new Error("undo() must be implemented");
  }
}
```

---

### **Concrete Command**

```js
class DrawCommand extends Command {
  constructor(canvas, shape) {
    super();
    this.canvas = canvas;
    this.shape = shape;
  }

  execute() {
    this.canvas.add(this.shape);
  }

  undo() {
    this.canvas.remove(this.shape);
  }
}
```

---

### **Canvas**

```js
class Canvas {
  constructor() {
    this.shapes = [];
  }

  add(shape) {
    this.shapes.push(shape);
    console.log("Added:", shape);
  }

  remove(shape) {
    this.shapes = this.shapes.filter((s) => s !== shape);
    console.log("Removed:", shape);
  }
}
```

---

### **Undo-Redo Manager**

```js
class HistoryManager {
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
    const cmd = this.undoStack.pop();
    if (!cmd) return;
    cmd.undo();
    this.redoStack.push(cmd);
  }

  redo() {
    const cmd = this.redoStack.pop();
    if (!cmd) return;
    cmd.execute();
    this.undoStack.push(cmd);
  }
}
```

---

### **Usage**

```js
const canvas = new Canvas();
const history = new HistoryManager();

history.execute(new DrawCommand(canvas, "Circle"));
history.execute(new DrawCommand(canvas, "Square"));

history.undo(); // removes Square
history.redo(); // adds Square again
```

---

### **Interview Explanation**

> The Command pattern encapsulates each drawing action, making undo and redo operations simple, scalable, and independent of UI logic.

---

## 🔥 Key Interview Takeaways

| Scenario          | Pattern Used          |
| ----------------- | --------------------- |
| Task dependencies | Graph + Encapsulation |
| Task validation   | SRP                   |
| Undo/Redo         | Command               |
| Action history    | Stack                 |

---

## **25. Notification Dispatcher with Multiple Channels & Fallback**

### **Problem**

- Send notifications via **Email, SMS, Push**
- If one channel fails → fallback to next
- Easily add new channels later
- Clean, extensible OOP design

---

### **OOP Principles Used**

- **Strategy Pattern** → different notification channels
- **Chain of Responsibility** → fallback mechanism
- **Open/Closed Principle** → add new channels without modifying existing logic

---

### **Notification Channel Interface**

```js
class NotificationChannel {
  send(message, user) {
    throw new Error("send() must be implemented");
  }
}
```

---

### **Concrete Channels**

```js
class EmailChannel extends NotificationChannel {
  send(message, user) {
    console.log(`Email sent to ${user.email}: ${message}`);
    return true;
  }
}

class SMSChannel extends NotificationChannel {
  send(message, user) {
    console.log(`SMS sent to ${user.phone}: ${message}`);
    return true;
  }
}

class PushChannel extends NotificationChannel {
  send(message, user) {
    throw new Error("Push service down"); // simulate failure
  }
}
```

---

### **Dispatcher with Fallback (Chain of Responsibility)**

```js
class NotificationDispatcher {
  constructor(channels) {
    this.channels = channels;
  }

  notify(message, user) {
    for (const channel of this.channels) {
      try {
        if (channel.send(message, user)) {
          console.log("Notification delivered");
          return;
        }
      } catch (err) {
        console.log("Channel failed, trying next...");
      }
    }
    console.log("All channels failed");
  }
}
```

---

### **Usage**

```js
const dispatcher = new NotificationDispatcher([
  new PushChannel(),
  new EmailChannel(),
  new SMSChannel(),
]);

dispatcher.notify("Order Confirmed", {
  email: "user@test.com",
  phone: "9999999999",
});
```

---

### **Interview Explanation**

> Each notification channel is a strategy, and the dispatcher applies a chain of responsibility to provide automatic fallback without tight coupling.

---

## **26. Plugin System for a Web Application Using OOP**

### **Problem**

- App should support plugins (analytics, auth, themes, etc.)
- Plugins can be added/removed at runtime
- Core app should not change when new plugins are added

---

### **OOP Principles Used**

- **Inversion of Control**
- **Open/Closed Principle**
- **Plugin / Extension Architecture**
- **Dependency Injection**

---

### **Plugin Interface**

```js
class Plugin {
  init(appContext) {
    throw new Error("init() must be implemented");
  }
}
```

---

### **Core Application**

```js
class Application {
  constructor() {
    this.plugins = [];
    this.context = {
      routes: [],
      hooks: {},
    };
  }

  registerPlugin(plugin) {
    plugin.init(this.context);
    this.plugins.push(plugin);
  }
}
```

---

### **Concrete Plugins**

#### **Analytics Plugin**

```js
class AnalyticsPlugin extends Plugin {
  init(context) {
    context.hooks.trackEvent = (event) => {
      console.log("Tracking event:", event);
    };
  }
}
```

#### **Auth Plugin**

```js
class AuthPlugin extends Plugin {
  init(context) {
    context.routes.push("/login", "/signup");
  }
}
```

---

### **Usage**

```js
const app = new Application();

app.registerPlugin(new AnalyticsPlugin());
app.registerPlugin(new AuthPlugin());

app.context.hooks.trackEvent("USER_LOGIN");
console.log(app.context.routes);
```

---

### **Interview Explanation**

> The plugin system uses inversion of control. Plugins depend on a shared app context and extend functionality without modifying core application code.

---

## 🔥 Interview Summary (Very Important)

| Scenario                | Pattern / Principle                |
| ----------------------- | ---------------------------------- |
| Notification dispatcher | Strategy + Chain of Responsibility |
| Channel fallback        | Failover design                    |
| Plugin system           | Open/Closed + IoC                  |
| Extensibility           | Dependency Injection               |

---

### 💡 Bonus (If interviewer asks “How would this scale?”)

- Notification dispatcher → Kafka / SQS
- Plugin system → dynamic imports, feature flags
- Observability → plugin lifecycle hooks

---

## **27. Multi-Level Caching System for a Node.js App**

### **Problem**

- Reduce DB load
- Serve data fast
- Support multiple cache layers:

  - **L1** → In-memory (process level)
  - **L2** → Distributed cache (Redis)
  - **Fallback** → Database

---

### **Design Approach**

Patterns used:

- **Chain of Responsibility** → cache lookup order
- **Strategy Pattern** → interchangeable cache layers
- **Encapsulation** → cache logic hidden

---

### **Cache Interface**

```js
class Cache {
  async get(key) {
    throw new Error("get() must be implemented");
  }
  async set(key, value) {
    throw new Error("set() must be implemented");
  }
}
```

---

### **L1 Cache (In-Memory)**

```js
class MemoryCache extends Cache {
  constructor() {
    super();
    this.store = new Map();
  }

  async get(key) {
    return this.store.get(key) || null;
  }

  async set(key, value) {
    this.store.set(key, value);
  }
}
```

---

### **L2 Cache (Redis – Simulated)**

```js
class RedisCache extends Cache {
  constructor() {
    super();
    this.store = new Map(); // simulate Redis
  }

  async get(key) {
    console.log("Redis lookup");
    return this.store.get(key) || null;
  }

  async set(key, value) {
    this.store.set(key, value);
  }
}
```

---

### **Database Layer**

```js
class Database {
  async fetch(key) {
    console.log("DB fetch");
    return `Value for ${key}`;
  }
}
```

---

### **Cache Manager (Chain)**

```js
class CacheManager {
  constructor(caches, database) {
    this.caches = caches;
    this.database = database;
  }

  async get(key) {
    for (const cache of this.caches) {
      const value = await cache.get(key);
      if (value) return value;
    }

    const value = await this.database.fetch(key);
    for (const cache of this.caches) {
      await cache.set(key, value);
    }
    return value;
  }
}
```

---

### **Usage**

```js
const cacheManager = new CacheManager(
  [new MemoryCache(), new RedisCache()],
  new Database()
);

await cacheManager.get("user:1"); // DB
await cacheManager.get("user:1"); // Memory
```

---

### **Interview Explanation**

> Multi-level caching reduces latency and DB load. CacheManager applies the Chain of Responsibility to check L1, then L2, then DB.

---

## **28. Resource Pool (Database Connection Pool) Using OOP**

### **Problem**

- Creating DB connections is expensive
- Need reuse & concurrency control
- Limit max connections

---

### **Design Approach**

Patterns used:

- **Object Pool Pattern**
- **Singleton (optional)**
- **Encapsulation**

---

### **Connection Class**

```js
class DBConnection {
  constructor(id) {
    this.id = id;
  }

  query(sql) {
    console.log(`Executing query on connection ${this.id}`);
  }
}
```

---

### **Connection Pool**

```js
class ConnectionPool {
  constructor(max) {
    this.max = max;
    this.available = [];
    this.inUse = new Set();

    for (let i = 1; i <= max; i++) {
      this.available.push(new DBConnection(i));
    }
  }

  acquire() {
    if (this.available.length === 0) {
      throw new Error("No connections available");
    }
    const conn = this.available.pop();
    this.inUse.add(conn);
    return conn;
  }

  release(conn) {
    if (this.inUse.has(conn)) {
      this.inUse.delete(conn);
      this.available.push(conn);
    }
  }
}
```

---

### **Usage**

```js
const pool = new ConnectionPool(2);

const conn1 = pool.acquire();
conn1.query("SELECT * FROM users");

const conn2 = pool.acquire();
conn2.query("SELECT * FROM orders");

pool.release(conn1);
pool.release(conn2);
```

---

### **Interview Explanation**

> Object Pool pattern manages limited resources efficiently by reusing expensive objects like DB connections.

---

## 🔥 Interview Cheat Sheet

| Scenario           | Pattern Used            |
| ------------------ | ----------------------- |
| Multi-level cache  | Chain of Responsibility |
| Cache layers       | Strategy                |
| DB connection pool | Object Pool             |
| Resource reuse     | Singleton (optional)    |

---

### 💡 Bonus (Production Talk)

- L1 → Node.js memory
- L2 → Redis
- DB → PostgreSQL / MongoDB
- Pool → node-pg / mongoose pool
- Metrics → cache hit ratio

---

## **29. E-Commerce Discount System (Combinable Discounts)**

### **Requirements**

- Multiple discounts can apply together
  (Coupon + Seasonal + Loyalty + Bulk)
- Easy to **add new discount types**
- Avoid modifying existing code

---

### **Design Principles Used**

- **Open/Closed Principle**
- **Strategy Pattern**
- **Composition over Inheritance**
- **Decorator Pattern (conceptually)**

---

### **Discount Interface**

```js
class Discount {
  apply(price, context) {
    throw new Error("apply() must be implemented");
  }
}
```

---

### **Concrete Discounts**

#### Percentage Discount

```js
class PercentageDiscount extends Discount {
  constructor(percent) {
    super();
    this.percent = percent;
  }

  apply(price) {
    return price - (price * this.percent) / 100;
  }
}
```

#### Flat Discount

```js
class FlatDiscount extends Discount {
  constructor(amount) {
    super();
    this.amount = amount;
  }

  apply(price) {
    return Math.max(price - this.amount, 0);
  }
}
```

#### Loyalty Discount

```js
class LoyaltyDiscount extends Discount {
  apply(price, context) {
    if (context.user.isPremium) {
      return price * 0.9;
    }
    return price;
  }
}
```

---

### **Discount Engine (Combiner)**

```js
class DiscountEngine {
  constructor(discounts = []) {
    this.discounts = discounts;
  }

  calculate(price, context) {
    return this.discounts.reduce(
      (currentPrice, discount) => discount.apply(currentPrice, context),
      price
    );
  }
}
```

---

### **Usage**

```js
const engine = new DiscountEngine([
  new PercentageDiscount(10),
  new FlatDiscount(100),
  new LoyaltyDiscount(),
]);

const finalPrice = engine.calculate(1000, {
  user: { isPremium: true },
});

console.log(finalPrice);
```

---

### **Why This Is Interview-Ready**

- Discounts are **composable**
- New discount = new class (no modification)
- Clean separation of responsibilities

> This is how Amazon/Flipkart-style pricing engines are designed.

---

## **30. Role-Based Dynamic Permissions (RBAC with OOP)**

### **Requirements**

- Users can have **multiple roles**
- Roles can change at runtime
- Permissions are reusable and scalable

---

### **Design Principles**

- **Single Responsibility**
- **Open/Closed**
- **Composition**
- **Policy-based Authorization**

---

### **Permission**

```js
class Permission {
  constructor(name) {
    this.name = name;
  }
}
```

---

### **Role**

```js
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
```

---

### **User**

```js
class User {
  constructor(name) {
    this.name = name;
    this.roles = new Set();
  }

  addRole(role) {
    this.roles.add(role);
  }

  hasPermission(permissionName) {
    for (const role of this.roles) {
      if (role.hasPermission(permissionName)) {
        return true;
      }
    }
    return false;
  }
}
```

---

### **Permissions Setup**

```js
const READ = new Permission("READ");
const WRITE = new Permission("WRITE");
const DELETE = new Permission("DELETE");

const admin = new Role("ADMIN");
admin.addPermission(READ);
admin.addPermission(WRITE);
admin.addPermission(DELETE);

const editor = new Role("EDITOR");
editor.addPermission(READ);
editor.addPermission(WRITE);
```

---

### **Usage**

```js
const user = new User("Vikash");
user.addRole(editor);

console.log(user.hasPermission("WRITE")); // true
console.log(user.hasPermission("DELETE")); // false
```

---

### **How This Scales in Production**

- Roles stored in DB
- Permissions cached (Redis)
- Policies applied in middleware
- Supports **multi-tenant apps**

---

## 🔥 Interview Comparison Table

| Problem               | Pattern Used           |
| --------------------- | ---------------------- |
| Discount combinations | Strategy + Composition |
| Extensible pricing    | Open/Closed            |
| Permissions           | RBAC                   |
| Dynamic roles         | Policy-based design    |

---

## 🧠 How to Explain in Interviews (1-liner)

- **Discount System**:
  “I use Strategy + composition so discounts can be combined without modifying existing code.”
- **RBAC**:
  “Users aggregate roles, roles aggregate permissions — clean, scalable, and dynamic.”

---
