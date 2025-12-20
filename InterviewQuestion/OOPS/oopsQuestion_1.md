Here’s a detailed, **OOP Concepts & Design Questions (Medium–Advanced)** in **JavaScript**:

---

### **1. Explain prototypal inheritance in JavaScript. How is it different from classical inheritance?**

- **Prototypal inheritance:** In JavaScript, objects can inherit directly from other objects via their **prototype chain**. Every object has an internal property `[[Prototype]]` that points to its prototype. Methods and properties are looked up the chain if not found on the object itself.

- **Example:**

```javascript
const parent = {
  greet() {
    console.log(`Hello from ${this.name}`);
  },
};

const child = Object.create(parent);
child.name = "Child";
child.greet(); // Hello from Child
```

- **Difference from classical inheritance (like Java/ C++):**

  1. JS uses **objects** for inheritance, not classes (though ES6 classes are syntactic sugar).
  2. No strict hierarchy—objects can directly inherit from other objects.
  3. More flexible and dynamic; you can change the prototype at runtime.

---

### **2. How do constructor functions, classes, and factory functions differ in JS? When would you use each?**

| Approach                 | Description                                                                                 | When to Use                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Constructor Function** | Old way to create objects using `function` + `new`. Uses prototype for shared methods.      | Legacy codebases or when using prototype methods explicitly.                   |
| **ES6 Class**            | Syntactic sugar over constructor functions. Supports `constructor`, `extends`, and `super`. | Modern JS development; more readable and structured.                           |
| **Factory Function**     | Returns a new object from a function. Can use closures for private variables.               | When you need more flexibility, private variables, or dynamic object creation. |

- **Examples:**

```javascript
// Constructor function
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function () {
  console.log(`Hello ${this.name}`);
};

// ES6 Class
class PersonClass {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hello ${this.name}`);
  }
}

// Factory Function
function createPerson(name) {
  return {
    name,
    greet() {
      console.log(`Hello ${name}`);
    },
  };
}
```

---

### **3. What are closures and how can they be used to emulate private variables in JS classes?**

- **Closure:** A function along with its lexical scope, which allows it to **remember variables from its outer scope** even after the outer function has executed.

- **Use in classes:** Closures can emulate private variables because they are **not accessible outside the function scope**.

- **Example:**

```javascript
function Person(name) {
  let _name = name; // private
  return {
    getName() {
      return _name;
    },
    setName(newName) {
      _name = newName;
    },
  };
}

const p = Person("Vikash");
console.log(p.getName()); // Vikash
p.setName("Rahul");
console.log(p.getName()); // Rahul
```

- ES6 **private class fields** (`#`) is an alternative:

```javascript
class Person {
  #name;
  constructor(name) {
    this.#name = name;
  }
  getName() {
    return this.#name;
  }
}
```

---

### **4. How would you implement encapsulation in JavaScript? Give a code example.**

- **Encapsulation:** Restrict access to certain parts of an object and expose only controlled methods to interact with them.

- **Implementation:** Use **closures** or **private class fields (`#`)**.

- **Example using private class fields:**

```javascript
class BankAccount {
  #balance = 0; // private field

  deposit(amount) {
    if (amount > 0) this.#balance += amount;
  }

  withdraw(amount) {
    if (amount <= this.#balance) this.#balance -= amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();
account.deposit(100);
console.log(account.getBalance()); // 100
account.#balance; // ❌ Error, private field
```

---

### **5. Explain polymorphism in JS. How can you achieve it with method overriding?**

- **Polymorphism:** Ability for different objects to respond differently to the same method call. In JS, this is usually done via **method overriding** or **duck typing**.

- **Example (method overriding in classes):**

```javascript
class Animal {
  speak() {
    console.log("Animal makes a sound");
  }
}

class Dog extends Animal {
  speak() {
    console.log("Dog barks");
  }
}

class Cat extends Animal {
  speak() {
    console.log("Cat meows");
  }
}

const animals = [new Animal(), new Dog(), new Cat()];
animals.forEach((a) => a.speak());
// Output:
// Animal makes a sound
// Dog barks
// Cat meows
```

- JS supports **dynamic polymorphism** because methods can be replaced at runtime:

```javascript
dog.speak = () => console.log("Woof Woof");
dog.speak(); // Woof Woof
```

---

### **6. What is abstraction and how would you design an abstract class or interface in JS?**

- **Abstraction:** Hiding the internal implementation details and exposing only the necessary functionality to the user. It allows you to focus on **what an object does**, not **how it does it**.

- **Abstract class in JS:** JS doesn’t have built-in abstract classes, but you can simulate them using **base classes** that throw errors for unimplemented methods.

```javascript
class Vehicle {
  constructor(name) {
    if (new.target === Vehicle) {
      throw new Error("Cannot instantiate abstract class Vehicle directly");
    }
    this.name = name;
  }

  startEngine() {
    throw new Error("Method 'startEngine()' must be implemented.");
  }
}

class Car extends Vehicle {
  startEngine() {
    console.log(`${this.name} engine started`);
  }
}

const car = new Car("Tesla");
car.startEngine(); // Tesla engine started

const vehicle = new Vehicle("Abstract"); // ❌ Error
```

- **Interface-like behavior:** JS does not have interfaces natively, but you can enforce method implementation checks in the constructor or use **TypeScript interfaces** for strong typing.

---

### **7. Explain composition over inheritance. How would you implement it in a JS project?**

- **Composition over inheritance:** Instead of creating deep class hierarchies, you **compose objects with reusable modules/behaviors**. This avoids rigid inheritance chains and promotes **flexibility and code reuse**.

- **Example:** Instead of `Bird extends Animal`, compose behaviors:

```javascript
const canFly = (obj) => ({
  fly: () => console.log(`${obj.name} is flying!`),
});

const canSwim = (obj) => ({
  swim: () => console.log(`${obj.name} is swimming!`),
});

function createDuck(name) {
  let duck = { name };
  return Object.assign(duck, canFly(duck), canSwim(duck));
}

const daffy = createDuck("Daffy");
daffy.fly(); // Daffy is flying!
daffy.swim(); // Daffy is swimming!
```

- **Advantage:** No deep hierarchy, easier to change behavior dynamically, and avoids tight coupling.

---

### **8. How would you implement a singleton pattern in JavaScript? What are its use cases?**

- **Singleton pattern:** Ensures a class has only **one instance** and provides a **global point of access**.

- **Implementation using closures:**

```javascript
const Singleton = (function () {
  let instance;

  function createInstance() {
    return {
      name: "SingletonInstance",
      timestamp: new Date(),
    };
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();

const obj1 = Singleton.getInstance();
const obj2 = Singleton.getInstance();
console.log(obj1 === obj2); // true
```

- **Implementation using ES6 class:**

```javascript
class SingletonClass {
  constructor() {
    if (SingletonClass.instance) {
      return SingletonClass.instance;
    }
    this.name = "SingletonClass";
    SingletonClass.instance = this;
  }
}

const a = new SingletonClass();
const b = new SingletonClass();
console.log(a === b); // true
```

- **Use Cases:**

  1. Database connection pool
  2. Logging service
  3. Configuration manager
  4. Caching service

---

I can continue with **questions 9–10** next, covering **Decorator & Factory patterns in JS**, with code examples.

Do you want me to continue?

Here’s a detailed, interview-ready answer set for **OOP Questions 9–10** in **JavaScript**:

---

### **9. Explain the Decorator pattern and implement a simple decorator in JS**

- **Decorator Pattern:**
  The Decorator pattern allows you to **add or modify behavior** of objects dynamically **without changing their original code**. It’s widely used for logging, authentication, caching, or enhancing functionality.

- **Example:** Decorating a simple `Car` object with extra features:

```javascript
class Car {
  cost() {
    return 20000;
  }
  description() {
    return "Basic Car";
  }
}

// Decorator function
function addSunroof(car) {
  const originalCost = car.cost.bind(car);
  car.cost = () => originalCost() + 2500;
  const originalDesc = car.description.bind(car);
  car.description = () => originalDesc() + " + Sunroof";
  return car;
}

let myCar = new Car();
console.log(myCar.cost(), myCar.description()); // 20000, Basic Car

myCar = addSunroof(myCar);
console.log(myCar.cost(), myCar.description()); // 22500, Basic Car + Sunroof
```

- **Key Point:**
  Decorators **enhance objects dynamically** without subclassing. In JS, functions are used to wrap and extend object behavior.

---

### **10. How would you implement a Factory pattern in JS? Provide an example for creating multiple types of objects.**

- **Factory Pattern:**
  The Factory pattern provides a **common interface for creating objects**, letting the factory decide which object to instantiate based on input parameters. This promotes **loose coupling** and **code reuse**.

- **Example:** Creating multiple types of shapes:

```javascript
class Circle {
  draw() {
    console.log("Drawing a Circle");
  }
}

class Square {
  draw() {
    console.log("Drawing a Square");
  }
}

class Triangle {
  draw() {
    console.log("Drawing a Triangle");
  }
}

// Factory Function
function ShapeFactory() {
  this.createShape = function (type) {
    switch (type) {
      case "circle":
        return new Circle();
      case "square":
        return new Square();
      case "triangle":
        return new Triangle();
      default:
        throw new Error("Unknown shape type");
    }
  };
}

const factory = new ShapeFactory();
const shapes = ["circle", "square", "triangle"].map((t) =>
  factory.createShape(t)
);

shapes.forEach((shape) => shape.draw());
// Output:
// Drawing a Circle
// Drawing a Square
// Drawing a Triangle
```

- **Key Point:**

  - Factory abstracts **object creation** from the client.
  - Makes it easy to **add new object types** without changing existing code.

---

### **11. Explain the Observer pattern. How would you implement it for a real-time notification system in JS?**

- **Observer Pattern:** Allows an object (**subject**) to maintain a list of dependents (**observers**) and automatically notify them of changes. Widely used for **event-driven programming**, real-time updates, and pub/sub systems.

- **Example (real-time notifications):**

```javascript
class NotificationSystem {
  constructor() {
    this.subscribers = [];
  }

  subscribe(fn) {
    this.subscribers.push(fn);
  }

  unsubscribe(fn) {
    this.subscribers = this.subscribers.filter((sub) => sub !== fn);
  }

  notify(data) {
    this.subscribers.forEach((fn) => fn(data));
  }
}

// Usage
const notifier = new NotificationSystem();

const user1 = (data) => console.log(`User1 received: ${data}`);
const user2 = (data) => console.log(`User2 received: ${data}`);

notifier.subscribe(user1);
notifier.subscribe(user2);

notifier.notify("New message received!");
// Output:
// User1 received: New message received!
// User2 received: New message received!
```

- **Key point:** Decouples **subject** from **observers**, making it easy to add/remove listeners dynamically.

---

### **12. What is the Strategy pattern? Implement a simple example in JS.**

- **Strategy Pattern:** Allows selecting an algorithm or behavior at runtime, encapsulating each strategy inside its own class or function.

- **Example:** Payment system with multiple strategies:

```javascript
class Payment {
  constructor(strategy) {
    this.strategy = strategy;
  }
  pay(amount) {
    this.strategy.pay(amount);
  }
}

class CreditCardPayment {
  pay(amount) {
    console.log(`Paid $${amount} using Credit Card`);
  }
}

class PayPalPayment {
  pay(amount) {
    console.log(`Paid $${amount} using PayPal`);
  }
}

// Usage
const payment1 = new Payment(new CreditCardPayment());
payment1.pay(100); // Paid $100 using Credit Card

const payment2 = new Payment(new PayPalPayment());
payment2.pay(200); // Paid $200 using PayPal
```

- **Key point:** Encapsulates algorithms/behaviors, allowing easy **switching at runtime** without changing client code.

---

### **13. Explain the Command pattern and how it can help in undo/redo operations in a JS app.**

- **Command Pattern:** Encapsulates a **request or action as an object**, allowing it to be **stored, queued, or undone**. Useful in **undo/redo functionality, task queues, and logging actions**.

- **Example (undo/redo):**

```javascript
class Command {
  constructor(execute, undo) {
    this.execute = execute;
    this.undo = undo;
  }
}

const commands = [];
let value = 0;

const add10 = new Command(
  () => (value += 10),
  () => (value -= 10)
);

const multiply2 = new Command(
  () => (value *= 2),
  () => (value /= 2)
);

commands.push(add10, multiply2);

// Execute commands
commands.forEach((cmd) => cmd.execute());
console.log(value); // 20

// Undo last command
commands.pop().undo();
console.log(value); // 10
```

- **Key point:** Commands allow **flexible execution, logging, undo/redo, and queuing**.

---

### **14. How do you implement Dependency Injection in JavaScript? Give an example.**

- **Dependency Injection (DI):** Provides objects their **dependencies from the outside**, instead of creating them internally. Improves **testability, flexibility, and decoupling**.

- **Example:**

```javascript
class Logger {
  log(msg) {
    console.log("Log:", msg);
  }
}

class UserService {
  constructor(logger) {
    // dependency injected
    this.logger = logger;
  }
  createUser(name) {
    this.logger.log(`Creating user: ${name}`);
  }
}

const logger = new Logger();
const userService = new UserService(logger);
userService.createUser("Vikash"); // Log: Creating user: Vikash
```

- **Key point:** Dependencies are **injected**, making it easier to **mock for testing** or replace implementations.

---

### **15. Explain Prototype pattern and how you could use it to reduce object creation overhead in JS.**

- **Prototype Pattern:** Creates new objects by **cloning existing ones** instead of instantiating from scratch. Reduces object creation cost and improves performance, especially for complex objects.

- **Example:**

```javascript
const carPrototype = {
  init(model, price) {
    this.model = model;
    this.price = price;
  },
  getDetails() {
    console.log(`${this.model} costs $${this.price}`);
  },
};

// Clone prototype
const car1 = Object.create(carPrototype);
car1.init("Tesla Model 3", 50000);
car1.getDetails(); // Tesla Model 3 costs $50000

const car2 = Object.create(carPrototype);
car2.init("BMW X5", 60000);
car2.getDetails(); // BMW X5 costs $60000
```

- **Key point:** Reuse existing objects as prototypes to **avoid expensive object creation**. Useful in **gaming, UI components, or large object structures**.

---

### **16. How would you prevent memory leaks when using OOP in JavaScript?**

- **Memory leaks** occur when objects are no longer needed but still referenced, preventing garbage collection.

- **Prevention strategies in OOP JS:**

  1. **Remove event listeners** when objects are destroyed.
  2. **Nullify unused references** in classes.
  3. Avoid **global variables** inside classes.
  4. Use **WeakMap / WeakSet** for private object storage to avoid memory retention.

- **Example:** Removing event listeners to prevent leaks:

```javascript
class Timer {
  constructor() {
    this.interval = setInterval(() => console.log("Tick"), 1000);
  }
  stop() {
    clearInterval(this.interval); // prevent memory leak
    this.interval = null;
  }
}

const timer = new Timer();
timer.stop();
```

---

### **17. Explain SOLID principles in the context of JS/Node.js applications**

- **S – Single Responsibility Principle (SRP):** A class/module should have **one responsibility**.
- **O – Open/Closed Principle (OCP):** Software entities should be **open for extension, closed for modification**.
- **L – Liskov Substitution Principle (LSP):** Subtypes must be **replaceable for their base types** without breaking the program.
- **I – Interface Segregation Principle (ISP):** No client should be forced to depend on methods it **doesn’t use**.
- **D – Dependency Inversion Principle (DIP):** Depend on **abstractions**, not concrete implementations.

**JS Example (SRP & DIP):**

```javascript
class UserRepository {
  fetchUser(id) {
    /* fetch from DB */
  }
}

class EmailService {
  sendEmail(user, message) {
    /* send email */
  }
}

class UserController {
  constructor(userRepo, emailService) {
    this.userRepo = userRepo;
    this.emailService = emailService;
  }
  notifyUser(id, msg) {
    const user = this.userRepo.fetchUser(id);
    this.emailService.sendEmail(user, msg);
  }
}
```

- Each class has a **single responsibility** and **depends on abstractions**.

---

### **18. How would you refactor a large class that violates SRP?**

- **Problem:** A class handles multiple responsibilities (e.g., User + Email + Logging).
- **Solution:** Split the class into smaller, focused classes. Use **composition** to combine them.

```javascript
// Before (violates SRP)
class UserManager {
  createUser(user) {
    /* save user */
  }
  sendWelcomeEmail(user) {
    /* send email */
  }
  logUserCreation(user) {
    /* log */
  }
}

// After (SRP-compliant)
class UserRepository {
  createUser(user) {
    /* save user */
  }
}
class EmailService {
  sendWelcomeEmail(user) {
    /* send email */
  }
}
class Logger {
  logUserCreation(user) {
    /* log */
  }
}
```

- **Key point:** Each class has **one reason to change**.

---

### **19. Explain Liskov Substitution Principle (LSP) with a practical example in JavaScript**

- **LSP:** Subclasses should be **interchangeable** with their base classes **without breaking behavior**.

- **Example:**

```javascript
class Bird {
  fly() {
    console.log("Flying");
  }
}

class Duck extends Bird {}
class Ostrich extends Bird {
  fly() {
    throw new Error("Cannot fly");
  } // ❌ violates LSP
}

// Correct approach: separate hierarchy
class FlyingBird extends Bird {
  fly() {
    console.log("Flying");
  }
}
class Duck extends FlyingBird {}
class Ostrich extends Bird {} // doesn't implement fly
```

- **Key point:** Avoid overriding base class methods in a way that **breaks expected behavior**.

---

### **20. How would you implement Mixin pattern in JS to add reusable functionality to multiple classes?**

- **Mixin Pattern:** Adds **shared behavior** to multiple classes **without inheritance**.

- **Example:**

```javascript
const canFly = {
  fly() {
    console.log(`${this.name} is flying!`);
  },
};

const canSwim = {
  swim() {
    console.log(`${this.name} is swimming!`);
  },
};

class Bird {
  constructor(name) {
    this.name = name;
  }
}

class Fish {
  constructor(name) {
    this.name = name;
  }
}

// Apply mixins
Object.assign(Bird.prototype, canFly);
Object.assign(Fish.prototype, canSwim);

const duck = new Bird("Duck");
duck.fly(); // Duck is flying!

const salmon = new Fish("Salmon");
salmon.swim(); // Salmon is swimming!
```

- **Key point:** Mixins allow **code reuse without deep inheritance**, perfect for **behavioral composition**.

---

### **21. Designing a chat application with OOP principles**

**Goal:** Create classes for **User, Message, and ChatRoom** that are modular, reusable, and maintainable.

**Design:**

```javascript
// User class
class User {
  constructor(id, name) {
    this.id = id;
    this.name = name;
  }
}

// Message class
class Message {
  constructor(sender, content, timestamp = new Date()) {
    this.sender = sender; // User object
    this.content = content;
    this.timestamp = timestamp;
  }
}

// ChatRoom class
class ChatRoom {
  constructor(id, name) {
    this.id = id;
    this.name = name;
    this.users = new Set(); // Users in the room
    this.messages = [];
  }

  addUser(user) {
    this.users.add(user);
  }

  removeUser(user) {
    this.users.delete(user);
  }

  sendMessage(sender, content) {
    if (!this.users.has(sender)) throw new Error("User not in chat room");
    const message = new Message(sender, content);
    this.messages.push(message);
    return message;
  }

  getMessages() {
    return this.messages;
  }
}

// Usage
const user1 = new User(1, "Alice");
const user2 = new User(2, "Bob");

const room = new ChatRoom(1, "General");
room.addUser(user1);
room.addUser(user2);

room.sendMessage(user1, "Hello Bob!");
console.log(room.getMessages());
```

**Key OOP Concepts Used:**

- **Encapsulation:** ChatRoom manages users/messages internally.
- **Single Responsibility Principle:** Each class has a distinct responsibility.
- **Composition:** ChatRoom contains Users and Messages instead of inheriting them.

---

### **22. Implementing Role-Based Access Control (RBAC) using OOP in Node.js**

**Goal:** Define roles and permissions for users in a modular way.

**Design:**

```javascript
// Role class
class Role {
  constructor(name, permissions = []) {
    this.name = name;
    this.permissions = new Set(permissions);
  }

  addPermission(permission) {
    this.permissions.add(permission);
  }

  hasPermission(permission) {
    return this.permissions.has(permission);
  }
}

// User class
class User {
  constructor(id, name) {
    this.id = id;
    this.name = name;
    this.roles = new Set();
  }

  assignRole(role) {
    this.roles.add(role);
  }

  can(permission) {
    for (let role of this.roles) {
      if (role.hasPermission(permission)) return true;
    }
    return false;
  }
}

// Usage
const adminRole = new Role("admin", ["read", "write", "delete"]);
const editorRole = new Role("editor", ["read", "write"]);

const user1 = new User(1, "Alice");
user1.assignRole(editorRole);

const user2 = new User(2, "Bob");
user2.assignRole(adminRole);

console.log(user1.can("delete")); // false
console.log(user2.can("delete")); // true
```

**Key OOP Concepts Used:**

- **Encapsulation:** Roles manage their permissions internally.
- **Composition:** Users contain roles; roles contain permissions.
- **Extensibility:** New roles and permissions can be added without modifying existing classes.

---

### **23. Designing a Payment System with Multiple Payment Methods**

**Goal:** Allow multiple payment methods while keeping the system **extensible** and **maintainable**.

**Solution:** Use **Strategy Pattern** to encapsulate each payment method.

```javascript
// Payment Strategy Interface
class PaymentMethod {
  pay(amount) {
    throw new Error("pay() must be implemented");
  }
}

// Concrete Payment Methods
class CreditCardPayment extends PaymentMethod {
  pay(amount) {
    console.log(`Paid $${amount} using Credit Card`);
  }
}

class PayPalPayment extends PaymentMethod {
  pay(amount) {
    console.log(`Paid $${amount} using PayPal`);
  }
}

class UPIPayment extends PaymentMethod {
  pay(amount) {
    console.log(`Paid $${amount} using UPI`);
  }
}

// Payment Processor
class PaymentProcessor {
  constructor(method) {
    this.method = method;
  }

  setMethod(method) {
    this.method = method;
  }

  process(amount) {
    this.method.pay(amount);
  }
}

// Usage
const processor = new PaymentProcessor(new CreditCardPayment());
processor.process(100); // Paid $100 using Credit Card

processor.setMethod(new PayPalPayment());
processor.process(200); // Paid $200 using PayPal
```

**Key OOP Concepts Used:**

- **Encapsulation:** Each payment method encapsulates its behavior.
- **Polymorphism:** All payment methods follow the same interface (`pay`).
- **Open/Closed Principle:** Add new payment methods without modifying existing code.

---

### **24. Designing a Notification System (Email, Push, SMS)**

**Goal:** Send different types of notifications in a modular and extensible way.

**Solution:** Use **Strategy Pattern** or **Observer Pattern** depending on the design. Here’s a **Strategy Pattern** approach:

```javascript
// Notification Interface
class Notification {
  send(message) {
    throw new Error("send() must be implemented");
  }
}

// Concrete Notifications
class EmailNotification extends Notification {
  send(message) {
    console.log(`Sending Email: ${message}`);
  }
}

class PushNotification extends Notification {
  send(message) {
    console.log(`Sending Push: ${message}`);
  }
}

class SMSNotification extends Notification {
  send(message) {
    console.log(`Sending SMS: ${message}`);
  }
}

// Notification Service
class NotificationService {
  constructor(method) {
    this.method = method;
  }

  setMethod(method) {
    this.method = method;
  }

  notify(message) {
    this.method.send(message);
  }
}

// Usage
const notifier = new NotificationService(new EmailNotification());
notifier.notify("Welcome to our platform!"); // Sending Email: Welcome to our platform!

notifier.setMethod(new SMSNotification());
notifier.notify("Your OTP is 1234"); // Sending SMS: Your OTP is 1234
```

**Key OOP Concepts Used:**

- **Encapsulation:** Each notification type handles its sending logic internally.
- **Polymorphism:** All notifications implement the same interface.
- **Extensibility:** Add new notification channels (WhatsApp, Slack) without changing the service.

---

### **25. Handling Dynamic Features (Adding New Notification Types) Without Modifying Existing Classes**

**Goal:** Make the system **extensible** so new features (e.g., notification types) can be added without touching existing classes.

**Solution:** Use **Open/Closed Principle** and **Strategy Pattern** or **Factory Pattern**.

```javascript
// Notification Interface
class Notification {
  send(message) {
    throw new Error("send() must be implemented");
  }
}

// Existing Notifications
class EmailNotification extends Notification {
  send(message) {
    console.log(`Email: ${message}`);
  }
}

class SMSNotification extends Notification {
  send(message) {
    console.log(`SMS: ${message}`);
  }
}

// Factory for dynamic creation
class NotificationFactory {
  static create(type) {
    const mapping = {
      email: EmailNotification,
      sms: SMSNotification,
      // Add new types dynamically without modifying existing classes
    };
    const NotificationClass = mapping[type.toLowerCase()];
    if (!NotificationClass) throw new Error("Notification type not supported");
    return new NotificationClass();
  }
}

// Usage
const emailNotifier = NotificationFactory.create("email");
emailNotifier.send("Welcome!");

const smsNotifier = NotificationFactory.create("sms");
smsNotifier.send("Your OTP is 1234");

// Adding a new notification type
class PushNotification extends Notification {
  send(message) {
    console.log(`Push: ${message}`);
  }
}
NotificationFactory.mapping = {
  ...NotificationFactory.mapping,
  push: PushNotification,
};
```

**Key Points:**

- Open/Closed Principle → system is **open for extension** but **closed for modification**.
- Adding new features doesn't touch existing classes.

---

### **26. Logger Class with Multiple Log Levels and Outputs**

**Goal:** Design a flexible logging system that supports **console, file, and remote logging** with multiple log levels.

**Solution:** Use **Strategy Pattern** for outputs and **Singleton Pattern** for a single logger instance.

```javascript
// Logger Output Strategies
class ConsoleLogger {
  log(level, message) {
    console.log(`[${level}] ${message}`);
  }
}

class FileLogger {
  log(level, message) {
    // Simulate writing to a file
    console.log(`[File][${level}] ${message}`);
  }
}

class RemoteLogger {
  log(level, message) {
    // Simulate sending to remote server
    console.log(`[Remote][${level}] ${message}`);
  }
}

// Logger Singleton
class Logger {
  constructor(output) {
    if (Logger.instance) return Logger.instance;
    this.output = output || new ConsoleLogger();
    Logger.instance = this;
  }

  setOutput(output) {
    this.output = output;
  }

  info(message) {
    this.output.log("INFO", message);
  }
  warn(message) {
    this.output.log("WARN", message);
  }
  error(message) {
    this.output.log("ERROR", message);
  }
}

// Usage
const logger = new Logger();
logger.info("Server started");
logger.setOutput(new FileLogger());
logger.warn("Disk space low");
logger.setOutput(new RemoteLogger());
logger.error("Payment failed");
```

**Key OOP Concepts Used:**

- **Strategy Pattern:** Output strategies can be swapped dynamically.
- **Singleton Pattern:** Single instance of logger.
- **Encapsulation & Polymorphism:** Loggers hide implementation details and provide uniform interface.

---

### **27. Implementing Undo-Redo Functionality in a JS Text Editor**

**Goal:** Allow users to undo and redo actions in a text editor.

**Solution:** Use **Command Pattern** to encapsulate actions as objects.

```javascript
// Command Interface
class Command {
  execute() {
    throw new Error("execute() must be implemented");
  }
  undo() {
    throw new Error("undo() must be implemented");
  }
}

// Concrete Commands
class InsertTextCommand extends Command {
  constructor(editor, text) {
    super();
    this.editor = editor;
    this.text = text;
  }

  execute() {
    this.editor.content += this.text;
  }

  undo() {
    this.editor.content = this.editor.content.slice(0, -this.text.length);
  }
}

// Editor
class TextEditor {
  constructor() {
    this.content = "";
    this.undoStack = [];
    this.redoStack = [];
  }

  executeCommand(command) {
    command.execute();
    this.undoStack.push(command);
    this.redoStack = []; // clear redo stack on new action
  }

  undo() {
    const command = this.undoStack.pop();
    if (command) {
      command.undo();
      this.redoStack.push(command);
    }
  }

  redo() {
    const command = this.redoStack.pop();
    if (command) {
      command.execute();
      this.undoStack.push(command);
    }
  }
}

// Usage
const editor = new TextEditor();
const cmd1 = new InsertTextCommand(editor, "Hello ");
const cmd2 = new InsertTextCommand(editor, "World!");

editor.executeCommand(cmd1);
editor.executeCommand(cmd2);
console.log(editor.content); // Hello World!

editor.undo();
console.log(editor.content); // Hello

editor.redo();
console.log(editor.content); // Hello World!
```

**Key OOP Concepts Used:**

- **Command Pattern:** Encapsulates actions (execute/undo) as objects.
- **Encapsulation:** TextEditor doesn’t need to know details of commands.
- **Undo/Redo Stacks:** Maintain history of executed commands.

---

### **28. Designing a Task Scheduler with Priorities, Pause, and Resume**

**Goal:** Schedule tasks with **different priorities** and allow **pausing/resuming** tasks.

**Solution:** Use **OOP principles and Priority Queue** concept.

```javascript
class Task {
  constructor(id, priority, action) {
    this.id = id;
    this.priority = priority; // higher number = higher priority
    this.action = action;
    this.isPaused = false;
  }

  execute() {
    if (!this.isPaused) this.action();
  }

  pause() {
    this.isPaused = true;
  }
  resume() {
    this.isPaused = false;
    this.execute();
  }
}

class TaskScheduler {
  constructor() {
    this.tasks = [];
  }

  addTask(task) {
    this.tasks.push(task);
    this.tasks.sort((a, b) => b.priority - a.priority); // sort by priority
  }

  run() {
    for (const task of this.tasks) {
      if (!task.isPaused) task.execute();
    }
  }

  pauseTask(taskId) {
    const task = this.tasks.find((t) => t.id === taskId);
    if (task) task.pause();
  }

  resumeTask(taskId) {
    const task = this.tasks.find((t) => t.id === taskId);
    if (task) task.resume();
  }
}

// Usage
const scheduler = new TaskScheduler();

const task1 = new Task(1, 2, () => console.log("Task 1 executed"));
const task2 = new Task(2, 5, () => console.log("Task 2 executed"));

scheduler.addTask(task1);
scheduler.addTask(task2);

scheduler.run();
// Output:
// Task 2 executed
// Task 1 executed

scheduler.pauseTask(2);
scheduler.run();
// Output:
// Task 1 executed (Task 2 paused)

scheduler.resumeTask(2);
// Output:
// Task 2 executed
```

**Key OOP Concepts Used:**

- **Encapsulation:** Task logic is self-contained.
- **Polymorphism:** All tasks implement `execute()`, pause, resume.
- **Extensibility:** Add new task types or priorities without changing the scheduler.

---

### **29. Implementing Versioning and Backward Compatibility for a Class**

**Goal:** Allow a class to evolve over time without breaking existing consumers.

**Solution:** Use **versioned classes or adapters** to maintain backward compatibility.

```javascript
// Version 1 of User class
class UserV1 {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  getInfo() {
    return `Name: ${this.name}, Email: ${this.email}`;
  }
}

// Version 2 adds phone number
class UserV2 {
  constructor(name, email, phone = null) {
    this.name = name;
    this.email = email;
    this.phone = phone;
  }

  getInfo() {
    return `Name: ${this.name}, Email: ${this.email}, Phone: ${
      this.phone ?? "N/A"
    }`;
  }
}

// Adapter for backward compatibility
class UserAdapter {
  static create(userData, version = 1) {
    if (version === 1) return new UserV1(userData.name, userData.email);
    if (version === 2)
      return new UserV2(userData.name, userData.email, userData.phone);
    throw new Error("Unsupported version");
  }
}

// Usage
const oldUser = UserAdapter.create(
  { name: "Alice", email: "alice@test.com" },
  1
);
console.log(oldUser.getInfo()); // Name: Alice, Email: alice@test.com

const newUser = UserAdapter.create(
  { name: "Bob", email: "bob@test.com", phone: "123456" },
  2
);
console.log(newUser.getInfo()); // Name: Bob, Email: bob@test.com, Phone: 123456
```

**Key OOP Concepts Used:**

- **Encapsulation:** Each class handles its own version logic.
- **Adapter Pattern:** Bridges new and old versions for backward compatibility.
- **Open/Closed Principle:** Add new versions without modifying existing ones.

---

### **30. Designing an E-Commerce Product System**

**Goal:** Support multiple types of products (**Physical, Digital, Subscription**) while keeping code modular and extensible.

**Solution:** Use **inheritance or composition** with a **base Product class**.

```javascript
// Base Product class
class Product {
  constructor(id, name, price) {
    this.id = id;
    this.name = name;
    this.price = price;
  }

  getInfo() {
    return `${this.name} - $${this.price}`;
  }

  getDeliveryMethod() {
    throw new Error("getDeliveryMethod() must be implemented");
  }
}

// Physical Product
class PhysicalProduct extends Product {
  getDeliveryMethod() {
    return "Ships via courier";
  }
}

// Digital Product
class DigitalProduct extends Product {
  getDeliveryMethod() {
    return "Delivered via download link";
  }
}

// Subscription Product
class SubscriptionProduct extends Product {
  constructor(id, name, price, duration) {
    super(id, name, price);
    this.duration = duration; // e.g., 1 month, 1 year
  }

  getDeliveryMethod() {
    return "Access granted online for " + this.duration;
  }
}

// Usage
const products = [
  new PhysicalProduct(1, "Laptop", 1200),
  new DigitalProduct(2, "Ebook", 15),
  new SubscriptionProduct(3, "Premium Membership", 50, "1 year"),
];

products.forEach((p) => {
  console.log(`${p.getInfo()} → ${p.getDeliveryMethod()}`);
});
// Output:
// Laptop - $1200 → Ships via courier
// Ebook - $15 → Delivered via download link
// Premium Membership - $50 → Access granted online for 1 year
```

**Key OOP Concepts Used:**

- **Inheritance:** Physical, Digital, and Subscription products extend Product.
- **Polymorphism:** Each product implements `getDeliveryMethod()` differently.
- **Open/Closed Principle:** Add new product types without modifying existing classes.

---
