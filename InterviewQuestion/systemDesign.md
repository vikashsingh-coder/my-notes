### **System Design Q&A for MERN Stack Interviews**

**1. What is client-server architecture?**

- **Answer:** It’s a model where the client (browser or app) requests data, and the server processes requests and responds. Communication happens over the internet using IP addresses mapped via domain names and DNS.

---

**2. What is the difference between a proxy and a reverse proxy?**

- **Answer:**

  - **Proxy:** Acts as a middleman between client and internet, hiding client IP.
  - **Reverse Proxy:** Routes client requests to backend servers, improving scalability, security, and load distribution.

---

**3. What is latency, and how can it be reduced?**

- **Answer:** Latency is the delay between request and response, often caused by physical distance.
- **Solution:** Deploy services in multiple **data centers worldwide** so users connect to the nearest server.

---

**4. Explain HTTP vs HTTPS.**

- **Answer:**

  - **HTTP:** Protocol for client-server communication, sends data in plain text.
  - **HTTPS:** Secures data using **SSL/TLS encryption** to prevent interception or tampering.

---

**5. What is an API and why is it used?**

- **Answer:** API (Application Programming Interface) allows clients to communicate with servers without worrying about low-level details.
- **Formats:** JSON or XML
- **Popular styles:** REST (simple, stateless) and GraphQL (fetch exactly the needed data).

---

**6. When should you use REST vs GraphQL?**

- **REST:** Simple, scalable, uses standard HTTP methods. Best for straightforward CRUD operations.
- **GraphQL:** Lets clients fetch only required data in a single query. Useful for complex queries, but heavier server-side processing.

---

**7. What is the difference between SQL and NoSQL databases?**

- **Answer:**

  - **SQL:** Relational, structured, ACID-compliant; great for consistency (e.g., banking apps).
  - **NoSQL:** Non-relational, flexible schema, horizontally scalable; optimized for large distributed data (e.g., social media apps).

---

**8. How do you scale an application server?**

- **Vertical Scaling:** Upgrade CPU, RAM, storage of a single server.
- **Horizontal Scaling:** Add multiple servers; improves capacity, reliability, and fault tolerance.

---

**9. What is a load balancer, and how does it work?**

- **Answer:** Distributes traffic across multiple servers using algorithms like **round-robin**, **least connections**, or **IP hashing**, ensuring no server is overloaded.

---

**10. How do you optimize database performance?**

- **Answer:**

  - **Indexing:** Speeds up read queries.
  - **Replication:** Read replicas for load distribution.
  - **Sharding:** Horizontal partitioning to split data across servers.
  - **Vertical Partitioning:** Split columns for faster queries.
  - **Caching:** Store frequently accessed data in memory.
  - **Denormalization:** Reduce joins by combining related tables.

---

**11. What is CAP theorem?**

- **Answer:** In a distributed system, you can only guarantee **two** out of:

  - Consistency
  - Availability
  - Partition tolerance

Network failures force trade-offs between these properties.

---

**12. How do you handle large files in web applications?**

- **Answer:** Use **blob storage** (e.g., AWS S3) for images, videos, PDFs. Serve data faster globally via a **CDN**.

---

**13. How do you implement real-time communication in MERN apps?**

- **Answer:**

  - **WebSockets:** Persistent two-way connection for live updates (chat, dashboards).
  - **Webhooks:** Server-to-server notifications triggered by events, reducing polling.

---

**14. What is the difference between monolithic and microservices architecture?**

- **Answer:**

  - **Monolith:** Single large codebase; hard to scale and deploy.
  - **Microservices:** Independent services for each functionality; scale and deploy independently; communicate via APIs or message queues.

---

**15. What is a message queue, and why use it?**

- **Answer:** Allows asynchronous communication between services.
- **Producer:** Sends a message
- **Consumer:** Receives and processes it
- **Benefit:** Decouples services, prevents overload, improves scalability.

---

**16. How do you prevent server overload or abuse?**

- **Answer:** Implement **rate limiting**: restrict requests per user/IP (e.g., 100 requests/minute).
- **API Gateway:** Centralized entry point that manages authentication, rate limiting, routing, and logging.

---

**17. What is idempotency, and why is it important?**

- **Answer:** Ensures repeated requests produce the same result (e.g., multiple payment submissions).
- **Implementation:** Assign unique IDs to requests and ignore duplicates.

---

Perfect! Let’s focus entirely on **system design questions and answers** relevant for a **MERN stack or full-stack developer interview**. I’ll make it concise but cover the **most commonly asked concepts**.

---

## **System Design Q&A for MERN Stack Interviews**

**1. What is system design?**

- **Answer:** System design is the process of defining the architecture, components, modules, interfaces, and data flow for a software system to meet functional and non-functional requirements like scalability, reliability, and performance.

---

**2. What is client-server architecture?**

- **Answer:** Clients (web/mobile apps) send requests to servers, which process them and return responses. Communication uses IP addresses mapped by DNS.

---

**3. What is latency, and why is it important?**

- **Answer:** Latency is the delay between request and response. High latency can make applications feel slow. Reduce it by using **CDNs, caching, and geographically distributed servers**.

---

**4. What is a proxy server vs reverse proxy?**

- **Answer:**

  - **Proxy:** Hides client IP, forwards requests to servers.
  - **Reverse Proxy:** Sits in front of servers, routes requests, handles load balancing, SSL termination, and caching.

---

**5. What is load balancing?**

- **Answer:** Distributes incoming traffic across multiple servers to improve **scalability, availability, and fault tolerance**. Algorithms: **round-robin, least connections, IP hash**.

---

**6. How do you scale web applications?**

- **Answer:**

  - **Vertical scaling:** Upgrade server resources (CPU, RAM). Limited and expensive.
  - **Horizontal scaling:** Add more servers; more reliable and scalable.

---

**7. What is caching and why is it used?**

- **Answer:** Storing frequently accessed data in memory (e.g., Redis, in-memory cache) to reduce database queries and improve response time.

---

**8. Explain database types and their use cases**

- **SQL:** Structured, ACID-compliant, good for transactions (banking apps).
- **NoSQL:** Flexible schema, scalable, good for high-volume data (social media, real-time apps).

---

**9. How do you scale databases?**

- **Answer:**

  - **Vertical scaling:** Upgrade server resources.
  - **Replication:** Multiple read replicas for distributing queries.
  - **Sharding:** Horizontal partitioning to split large data sets across servers.
  - **Indexing:** Speeds up queries.
  - **Caching:** Store frequent queries in memory.

---

**10. What is denormalization, and when is it used?**

- **Answer:** Combining related tables into one to reduce joins, improving read performance. Often used in **read-heavy applications**.

---

**11. Explain CAP theorem.**

- **Answer:** A distributed system can guarantee **only two** of these three at a time:

  - **Consistency** – all nodes see the same data.
  - **Availability** – system responds to every request.
  - **Partition tolerance** – system works despite network failures.

---

**12. What are microservices, and why use them?**

- **Answer:** Breaking applications into **small, independent services** that handle a single responsibility. Benefits: independent scaling, deployment, and fault isolation.

---

**13. How do microservices communicate?**

- **Answer:**

  - **Synchronous:** REST APIs, GraphQL.
  - **Asynchronous:** Message queues (RabbitMQ, Kafka) for decoupled communication and scalability.

---

**14. What is a CDN, and why is it important?**

- **Answer:** Content Delivery Network stores static assets globally. Users fetch content from the nearest server, reducing latency and improving speed.

---

**15. How do you implement real-time features?**

- **Answer:**

  - **WebSockets:** Persistent two-way connection for chat, live dashboards.
  - **Webhooks:** Server-to-server notifications triggered by events, reducing polling.

---

**16. What is API gateway?**

- **Answer:** A centralized entry point that manages authentication, rate limiting, routing, logging, and monitoring for microservices.

---

**17. What is rate limiting, and why is it used?**

- **Answer:** Restricts the number of requests a user/IP can make in a time frame to prevent abuse and server overload.

---

**18. What is idempotency?**

- **Answer:** Ensures repeated requests produce the **same result**, preventing issues like duplicate payments. Achieved using **unique request IDs**.

---

**19. How do you handle large file storage?**

- **Answer:** Use **blob storage** (AWS S3) with unique URLs. For performance, serve files via **CDN** to reduce latency.

---

**20. What is sharding vs vertical partitioning?**

- **Answer:**

  - **Sharding (horizontal):** Split database rows across servers.
  - **Vertical partitioning:** Split table columns into multiple tables to optimize queries.

---

**21. Difference between REST and GraphQL**

- **Answer:**

  - **REST:** Multiple endpoints, returns full data, stateless.
  - **GraphQL:** Single endpoint, clients fetch **only required data**, reduces multiple network calls.

---

**22. How do you handle system failures?**

- **Answer:**

  - Use **replication and failover** for databases.
  - Implement **load balancers** for backend servers.
  - Retry mechanisms and **idempotent operations** for APIs.

---

**23. What is message queue, and why is it important?**

- **Answer:** Asynchronous communication between services. Helps **decouple systems**, process tasks in the background, and improve scalability.

---

**24. How do you reduce database read latency?**

- **Answer:**

  - Caching frequently accessed data.
  - Using **read replicas**.
  - Optimizing queries with **indexes**.

---

**25. What is the difference between monolithic vs microservices architecture?**

- **Answer:**

  - Monolithic: Single codebase, hard to scale.
  - Microservices: Independent services, easier to scale and maintain.

---

**1. What is horizontal vs vertical scaling?**

- **Answer:**

  - **Vertical scaling (scale-up):** Add CPU, RAM, or storage to a single server. Limited by hardware capacity and expensive.
  - **Horizontal scaling (scale-out):** Add more servers; improves **availability, fault tolerance, and scalability**.

---

**2. How do you design a high-traffic system like Instagram or Twitter?**

- **Answer:**

  - Use **microservices** for modularity.
  - **Load balancers** distribute traffic.
  - **Caching** frequently accessed data with Redis.
  - **CDN** for static assets.
  - **Database sharding and replication** for large datasets.
  - Async processing using **message queues** for notifications or background jobs.

---

**3. What is a CDN, and how does it improve performance?**

- **Answer:** A **Content Delivery Network** stores static files in multiple locations worldwide. Users fetch content from the nearest server, reducing latency and speeding up page loads.

---

**4. How do you handle millions of users in real-time chat applications?**

- **Answer:**

  - Use **WebSockets** or **Socket.io** for persistent two-way connections.
  - Horizontally scale Node.js servers behind a **load balancer**.
  - Use **Redis Pub/Sub or message queues** to synchronize events across servers.
  - Offload media to **blob storage + CDN**.

---

**5. Explain caching strategies used in large systems.**

- **Answer:**

  - **Cache-aside:** App checks cache first, loads from DB if missing, then updates cache.
  - **Write-through:** Writes go to cache + DB simultaneously.
  - **Write-back:** Writes go to cache first, DB updated asynchronously.
  - Use TTL (Time-to-Live) to avoid stale data.

---

**6. How do you design a rate-limited API?**

- **Answer:**

  - Restrict users/IP to X requests per time window.
  - Algorithms: **Fixed window, Sliding window, Token bucket, Leaky bucket**.
  - Often implemented via **API gateway** (e.g., Kong, NGINX, or custom middleware).

---

**7. How do you handle database write-heavy workloads?**

- **Answer:**

  - **Partitioning/Sharding** to distribute writes.
  - **Async writes** using message queues.
  - Use **NoSQL DBs** for high throughput when strong consistency is not required.
  - Consider **write-back caching**.

---

**8. What is eventual consistency?**

- **Answer:** In distributed systems, all nodes will eventually have the same data, but not instantly.
- Common in **NoSQL databases** (Cassandra, DynamoDB) and **replicated systems**.

---

**9. How do you handle failures in distributed systems?**

- **Answer:**

  - Retry with exponential backoff.
  - Circuit breakers to prevent cascading failures.
  - Replication & failover for databases.
  - Health checks and monitoring for servers.

---

**10. What is a message queue vs pub/sub?**

- **Answer:**

  - **Message queue:** Tasks are queued and processed by one consumer at a time.
  - **Pub/Sub:** Messages are broadcasted to multiple subscribers; each receives a copy.

- Use for **async processing, notifications, event-driven architecture**.

---

**11. How do you design a scalable notification system?**

- **Answer:**

  - Use **message queues** for decoupling producers (app events) and consumers (notification service).
  - Store messages in DB or cache.
  - Deliver notifications via multiple channels (email, push, SMS).
  - Horizontal scaling for multiple workers.

---

**12. What is the difference between synchronous vs asynchronous communication?**

- **Answer:**

  - **Synchronous:** Client waits for server response (e.g., REST API).
  - **Asynchronous:** Client does not wait; server processes request in background (e.g., message queues, WebSockets).

---

**13. How do you prevent bottlenecks in a distributed system?**

- **Answer:**

  - Use **load balancers** for traffic distribution.
  - Cache frequently accessed data.
  - Use **sharding** for databases.
  - Implement **async processing** for heavy workloads.
  - Monitor metrics and scale servers dynamically.

---

**14. How do you design a video streaming service?**

- **Answer:**

  - Store media in **blob storage** (S3).
  - Use **CDN** for low-latency delivery.
  - Support adaptive bitrate streaming.
  - Microservices for handling uploads, encoding, and streaming.
  - Cache frequently watched videos near users.

---

**15. Explain sharding and partitioning in databases**

- **Answer:**

  - **Sharding (horizontal partitioning):** Split rows across multiple servers.
  - **Vertical partitioning:** Split columns into separate tables.
  - Reduces load on a single DB and improves query performance.

---

**16. How do you handle real-time collaborative apps (e.g., Google Docs)?**

- **Answer:**

  - WebSockets for two-way real-time communication.
  - Operational Transform (OT) or CRDTs for concurrent edits.
  - Backend handles conflict resolution and sync.

---

**17. How do you design a large-scale search system?**

- **Answer:**

  - Use **inverted indexes** for fast text search (ElasticSearch, Solr).
  - Shard indexes across servers.
  - Cache frequently queried results.
  - Load balance search queries.

---

**18. How do you design a high-availability database?**

- **Answer:**

  - Use **replication** (primary + read replicas).
  - Automatic failover to secondary replicas.
  - Multi-region deployment.
  - Periodic backups and monitoring.

---

**19. What is eventual vs strong consistency?**

- **Answer:**

  - **Strong consistency:** All clients see the same data immediately (SQL).
  - **Eventual consistency:** Clients may temporarily see stale data, but eventually converge (NoSQL).

---

**20. How do you scale a real-time leaderboard system?**

- **Answer:**

  - Use **in-memory stores** (Redis) for fast updates.
  - Shard users or games to distribute load.
  - Async batch updates to DB for persistence.
  - Use sorted sets for efficient ranking queries.

---

### **1. Explain the basic architecture of a scalable web application.**

- A scalable web application typically has:

  - **Client layer (frontend):** React, Angular, or mobile app that interacts with the server via APIs.
  - **Application layer (backend):** Node.js/Express server handling business logic and API requests.
  - **Database layer:** SQL (PostgreSQL/MySQL) or NoSQL (MongoDB) for storing data.
  - **Caching layer:** Redis or Memcached for frequently accessed data.
  - **Load balancer:** Distributes incoming traffic across multiple backend servers.
  - **CDN:** Delivers static assets closer to users to reduce latency.
  - **Optional services:** Message queues (RabbitMQ, Kafka) for async processing and microservices for modularity.

- **Goal:** Handle high traffic efficiently, maintain fault tolerance, and ensure quick response times.

---

### **2. What is the difference between monolithic and microservices architecture?**

| Aspect          | Monolithic                   | Microservices                               |
| --------------- | ---------------------------- | ------------------------------------------- |
| Codebase        | Single large codebase        | Multiple small, independent services        |
| Deployment      | Entire app deployed at once  | Each service deployed independently         |
| Scalability     | Limited, scale whole app     | Individual services can scale independently |
| Fault Isolation | Failure can crash entire app | Failures isolated to individual service     |
| Complexity      | Simple to start              | More complex, requires orchestration        |
| Use Case        | Small apps or MVPs           | Large-scale, evolving systems               |

---

### **3. How do you choose between SQL and NoSQL for your application?**

- **SQL:**

  - Structured schema, strong consistency (ACID).
  - Good for relational data (e.g., banking, e-commerce orders).
  - Supports complex queries and joins.

- **NoSQL:**

  - Flexible schema, horizontally scalable, eventual consistency.
  - Good for large-scale apps, high-volume data, real-time apps (e.g., social media feeds, chat apps).

- **Rule of thumb:** Use SQL for structured, relational, and transactional data. Use NoSQL for flexible, high-scale, distributed data.

---

### **4. What is horizontal vs vertical scaling? When would you use each?**

- **Vertical scaling (scale-up):** Add more CPU, RAM, or storage to a single server.

  - **Pros:** Simple, no code changes.
  - **Cons:** Limited by hardware, expensive, single point of failure.
  - **Use case:** Small apps or temporary traffic spikes.

- **Horizontal scaling (scale-out):** Add more servers to distribute load.

  - **Pros:** Highly scalable, fault-tolerant, handles millions of users.
  - **Cons:** Requires load balancers and distributed architecture.
  - **Use case:** Large-scale apps with high traffic and high availability requirements.

---

### **5. What is the difference between a 3-tier and n-tier architecture?**

| Aspect      | 3-Tier Architecture                                      | N-Tier Architecture                                                                             |
| ----------- | -------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Layers      | Presentation (frontend), Application (backend), Database | Multiple layers (e.g., presentation, business logic, data access, caching, service layer, etc.) |
| Complexity  | Simple                                                   | More complex, modular                                                                           |
| Scalability | Limited                                                  | Highly scalable and flexible                                                                    |
| Maintenance | Easier                                                   | Easier to isolate and maintain individual layers                                                |
| Use Case    | Small-medium apps                                        | Large enterprise applications                                                                   |

---

### **1. What is sharding in databases and how does it work?**

- **Sharding** is a **horizontal partitioning** technique where data is split across multiple database servers (shards) based on a **sharding key** (e.g., user ID).
- **How it works:** Each shard contains a subset of the total data. Queries are routed to the correct shard to reduce load and improve performance.
- **Use case:** Large-scale apps with massive datasets, like social media or e-commerce platforms.

---

### **2. What is replication in databases and why is it used?**

- **Replication** involves creating **copies of a database** across multiple servers.
- **Types:** Master-slave (primary-replica) or multi-master replication.
- **Purpose:**

  - Improve **read performance** (replicas serve read queries).
  - Enhance **fault tolerance** (if one server fails, others take over).
  - Enable **geo-distribution** for low-latency access.

---

### **3. What is database partitioning and what types exist?**

- **Database partitioning** splits large tables into smaller, manageable pieces.
- **Types:**

  - **Horizontal partitioning (sharding):** Split rows across servers.
  - **Vertical partitioning:** Split columns into separate tables based on access patterns.

- **Goal:** Reduce query load and improve performance for large datasets.

---

### **4. How do you handle database bottlenecks in high-traffic applications?**

- **Strategies:**

  - **Caching** frequently accessed data (Redis/Memcached).
  - **Read replicas** for heavy read workloads.
  - **Sharding** to distribute data across multiple servers.
  - **Optimize queries** with proper indexing.
  - **Asynchronous processing** for heavy writes (queues, background jobs).

---

### **5. Explain eventual consistency vs strong consistency.**

- **Strong consistency:** All nodes return the same data immediately after a write. Typical in SQL databases.
- **Eventual consistency:** Data may temporarily differ across nodes, but eventually becomes consistent. Common in NoSQL systems like Cassandra or DynamoDB.
- **Use case:** Eventual consistency is acceptable for social feeds or analytics, while strong consistency is needed for banking or transactional systems.

---

### **6. How do you design a highly available and fault-tolerant database?**

- **Techniques:**

  - **Replication:** Primary + read replicas for failover.
  - **Multi-region deployment** for disaster recovery.
  - **Automated failover** to backup servers.
  - **Regular backups** and monitoring.
  - **Partition-tolerant design** to handle network failures.

---

### **7. What is the difference between OLTP and OLAP systems?**

| Aspect   | OLTP                                         | OLAP                           |
| -------- | -------------------------------------------- | ------------------------------ |
| Purpose  | Transactional systems (insert/update/delete) | Analytical/reporting systems   |
| Data     | Current, detailed                            | Historical, aggregated         |
| Queries  | Simple, short                                | Complex, long-running          |
| Examples | E-commerce checkout, banking transactions    | Business analytics, dashboards |

---

### **8. How do you optimize database read performance?**

- **Techniques:**

  - **Indexes** on frequently queried columns.
  - **Read replicas** for distributing read queries.
  - **Caching** frequently accessed queries or objects.
  - **Denormalization** for read-heavy applications.
  - Use **materialized views** for precomputed queries.

---

### **9. How do you handle write-heavy workloads in a distributed database?**

- **Strategies:**

  - **Sharding** to distribute writes across multiple servers.
  - **Batch writes** and asynchronous processing.
  - Use **NoSQL databases** optimized for high write throughput (e.g., Cassandra, MongoDB).
  - **Write-back caching** to reduce DB load.

---

### **10. What are indexes and how do they improve performance?**

- **Index:** A data structure that allows the database to **locate rows faster** without scanning the entire table.
- **How it helps:**

  - Speeds up **SELECT queries**.
  - Commonly used on **primary keys, foreign keys, and frequently filtered columns**.

- **Trade-off:** Slows down writes/updates because indexes must be updated.

---

### **16. What is caching and why is it important in web apps?**

- **Caching** is the process of storing frequently accessed data in **fast storage (memory)** instead of fetching it from the primary database every time.
- **Importance:**

  - Reduces database load and latency.
  - Improves response time and user experience.
  - Common tools: Redis, Memcached, in-memory caches.

---

### **17. Explain cache-aside, write-through, and write-back caching strategies.**

- **Cache-aside (Lazy Loading):**

  - App checks cache first. If data isn’t found, fetch from DB, store in cache, and return it.
  - **Pros:** Only frequently accessed data is cached.
  - **Cons:** Cache miss can cause latency.

- **Write-through:**

  - Writes go to both cache and database simultaneously.
  - **Pros:** Cache is always up-to-date.
  - **Cons:** Slower writes.

- **Write-back (Write-behind):**

  - Writes go to cache first and asynchronously persisted to DB later.
  - **Pros:** Faster writes.
  - **Cons:** Risk of data loss if cache fails before DB write.

---

### **18. How do you handle cache invalidation?**

- **Cache invalidation** ensures cached data is fresh and consistent with the database.
- **Strategies:**

  - **Time-to-live (TTL):** Automatically expire data after a set period.
  - **Explicit invalidation:** Delete or update cache when underlying data changes.
  - **Versioning / key-based invalidation:** Change cache key when data updates.

---

### **19. What is a Content Delivery Network (CDN) and how does it reduce latency?**

- A **CDN** is a global network of distributed servers that caches static assets (images, CSS, JS, videos).
- **How it reduces latency:**

  - Delivers content from a server **closest to the user**, reducing network travel time.
  - Reduces load on the origin server.
  - Improves page load speed and reliability for global users.

- **Examples:** Cloudflare, AWS CloudFront, Akamai.

---

### **20. How do you design caching for dynamic content?**

- **Dynamic content** changes frequently (e.g., user dashboards, notifications).
- **Design approaches:**

  - **Cache fragments:** Only cache portions of the page or specific queries.
  - **Short TTLs:** Expire cache quickly to ensure freshness.
  - **Event-driven invalidation:** Invalidate cache when relevant data changes.
  - **Client-side caching:** Use browser/local storage to cache dynamic data when possible.

---

### **21. What is a load balancer and how does it work?**

- A **load balancer (LB)** distributes incoming client requests across multiple backend servers to **improve performance, scalability, and fault tolerance**.
- **How it works:**

  1. Receives incoming requests from clients.
  2. Uses a **load balancing algorithm** to select a healthy backend server.
  3. Forwards the request to the selected server.
  4. Returns the response back to the client.

- **Benefits:** Prevents a single server from being overloaded, ensures high availability, and can provide SSL termination or caching.

---

### **22. Explain round-robin, least connections, and IP hash load balancing.**

- **Round-robin:**

  - Requests are distributed sequentially across servers.
  - **Pros:** Simple and works for evenly distributed traffic.
  - **Cons:** Doesn’t account for server load.

- **Least connections:**

  - Sends request to the server with the fewest active connections.
  - **Pros:** Better for servers with varying workloads.

- **IP hash:**

  - Server selection based on a hash of the client’s IP.
  - **Pros:** Ensures a client consistently connects to the same server (useful for session persistence).

---

### **23. What is a reverse proxy and why is it used?**

- A **reverse proxy** sits between clients and backend servers, forwarding client requests to the appropriate server.
- **Uses:**

  - Load balancing between multiple servers.
  - SSL termination (handling HTTPS).
  - Caching static content to reduce backend load.
  - Security: hides backend server IPs and blocks malicious requests.

---

### **24. How do you reduce latency in global applications?**

- **Strategies:**

  - Deploy servers/data centers in multiple regions.
  - Use **CDNs** to serve static content from the closest location.
  - Implement **caching** for frequently accessed data.
  - Optimize **database queries** and use **read replicas** near users.
  - Minimize request size and use **compression** (gzip, Brotli).

---

### **25. How do you design APIs for large-scale applications?**

- **Principles:**

  - **Stateless APIs:** Each request contains all necessary information.
  - **Versioning:** Maintain backward compatibility using `/v1`, `/v2`.
  - **Rate limiting:** Prevent abuse and ensure fair usage.
  - **Pagination & filtering:** Handle large datasets efficiently.
  - **Caching:** Reduce repeated database calls.
  - **Monitoring & logging:** Track API usage, performance, and errors.
  - **Security:** Use HTTPS, authentication (JWT, OAuth), and input validation.

---

### **26. How do WebSockets work and why are they used for real-time apps?**

- **WebSockets** establish a **persistent, full-duplex connection** between client and server over a single TCP connection.
- **How it works:**

  1. Client initiates a WebSocket handshake via HTTP.
  2. Connection upgrades to WebSocket protocol.
  3. Both client and server can send messages anytime without repeated HTTP requests.

- **Use case:** Real-time apps like chat, live dashboards, online gaming.
- **Advantage:** Reduces latency and network overhead compared to polling.

---

### **27. What is long polling and how is it different from WebSockets?**

- **Long polling:** Client sends a request to the server. If data isn’t ready, server holds the request until data is available or timeout occurs. Client immediately sends a new request after response.
- **Differences from WebSockets:**

  | Aspect         | Long Polling                    | WebSockets                             |
  | -------------- | ------------------------------- | -------------------------------------- |
  | Connection     | Short-lived, repeated requests  | Persistent, full-duplex                |
  | Latency        | Higher due to repeated requests | Low, real-time                         |
  | Resource usage | Higher on server                | Efficient after connection established |
  | Use case       | Moderate real-time apps         | High-frequency real-time apps          |

---

### **28. How do you handle real-time notifications in a distributed system?**

- **Approaches:**

  - Use **WebSockets** or **Server-Sent Events (SSE)** to push notifications to clients.
  - Use a **message broker (Kafka, RabbitMQ, Redis Pub/Sub)** to propagate events across servers.
  - Ensure **horizontal scalability** by having multiple WebSocket servers behind a **load balancer**.
  - Maintain **user-to-server mapping** in a distributed cache (e.g., Redis) for routing messages.

---

### **29. What are webhooks and how do they improve performance?**

- **Webhooks:** HTTP callbacks triggered by events in one system to notify another system immediately.
- **Benefits:**

  - Eliminates **polling**, saving network resources.
  - Delivers **real-time updates** to client or server.

- **Example:** Payment gateway sending a POST request to your app after a successful transaction.

---

### **30. How do you design a scalable chat system?**

- **Architecture:**

  - Use **WebSockets** for real-time communication.
  - **Message broker** for distributing messages across servers (e.g., Redis Pub/Sub, Kafka).
  - **Database:** NoSQL (MongoDB, DynamoDB) for storing messages; optional caching for recent messages.
  - **Horizontal scaling:** Multiple WebSocket servers behind a **load balancer**.
  - **Features:** Typing indicators, message acknowledgments, offline message storage, and delivery.

---

### **31. How do you handle concurrent updates in collaborative apps?**

- **Strategies:**

  - **Optimistic concurrency control:** Check version or timestamp before updating.
  - **Operational Transformation (OT):** Transform concurrent edits in collaborative editors (like Google Docs).
  - **Conflict-free Replicated Data Types (CRDTs):** Automatically merge updates from multiple clients.
  - **Locking:** Use row-level or document-level locks for critical updates (less preferred for high concurrency).

---

### **32. How do microservices communicate with each other?**

- **Methods:**

  - **Synchronous:** HTTP/REST or gRPC APIs where one service waits for another to respond.
  - **Asynchronous:** Message queues, Pub/Sub, or event streams, where services communicate via messages without blocking.

- **Choice depends on:** Latency tolerance, coupling requirements, and reliability needs.

---

### **33. What is synchronous vs asynchronous communication in microservices?**

| Aspect           | Synchronous               | Asynchronous                         |
| ---------------- | ------------------------- | ------------------------------------ |
| Communication    | Request → Response        | Event/message sent → processed later |
| Coupling         | Tightly coupled           | Loosely coupled                      |
| Latency          | Higher if service is slow | Lower; no blocking                   |
| Failure handling | Direct error propagation  | Can retry or queue messages          |
| Example          | REST API call             | RabbitMQ, Kafka, Redis Pub/Sub       |

---

### **34. What are message queues and how are they used?**

- **Message queue:** A buffer that stores messages until a consumer processes them.
- **Use cases:**

  - Decouple services, allowing **async processing**.
  - Smooth out traffic spikes (buffering requests).
  - Ensure **reliable delivery** even if a consumer is temporarily down.

- **Examples:** RabbitMQ, AWS SQS, Kafka (can also be Pub/Sub).

---

### **35. Explain Pub/Sub messaging.**

- **Pub/Sub (Publish/Subscribe):**

  - Publishers send messages to a **topic** instead of directly to consumers.
  - Subscribers receive messages from the topic asynchronously.

- **Benefits:**

  - Loose coupling: Publisher doesn’t know consumers.
  - Scalability: Multiple subscribers can process messages independently.

- **Examples:** Kafka, Google Pub/Sub, Redis Pub/Sub.

---

### **36. How do you prevent cascading failures in microservices?**

- **Techniques:**

  - **Circuit breaker:** Stop calling failing services temporarily.
  - **Retries with backoff:** Retry failed requests with exponential delay.
  - **Bulkheads:** Isolate resources per service to prevent system-wide failure.
  - **Timeouts:** Prevent long waits for downstream services.

---

### **37. What is an API gateway and why is it important?**

- **API Gateway:** A single entry point for client requests to multiple microservices.
- **Functions:**

  - Request routing to appropriate service.
  - Authentication & authorization.
  - Rate limiting & throttling.
  - Logging and monitoring.
  - Aggregation of multiple service responses.

- **Importance:** Simplifies client communication and improves security, scalability, and maintainability.

---

### **38. How do you handle rate limiting in microservices?**

- **Purpose:** Prevent abuse and protect services from overload.
- **Methods:**

  - **Fixed window:** Limit requests per time window.
  - **Sliding window:** More accurate request count over a moving window.
  - **Token bucket / Leaky bucket:** Smooth request bursts over time.

- **Implementation:** Can be done at **API gateway, service layer, or using Redis** for distributed limits.

---

### **39. What is idempotency and why is it important for distributed systems?**

- **Idempotency:** Ensures that **multiple identical requests produce the same result** as a single request.
- **Importance:**

  - Prevents duplicate actions (e.g., double payments) due to retries or network failures.

- **Implementation:** Assign unique request IDs and check if a request was already processed before executing it.

---

### **40. How do you design a system to handle millions of users?**

- **Techniques:**

  - **Horizontal scaling:** Add more servers for backend services and databases.
  - **Load balancing:** Distribute traffic across servers efficiently.
  - **Caching:** Use Redis/Memcached for frequently accessed data.
  - **Database optimization:** Use read replicas, sharding, and indexing.
  - **CDN:** Serve static content globally to reduce latency.
  - **Asynchronous processing:** Offload heavy tasks to message queues/workers.

---

### **41. How do you prevent single points of failure in a system?**

- **Strategies:**

  - Deploy **redundant servers** for all critical components.
  - Use **load balancers** to route traffic to healthy servers.
  - Implement **replicated databases** and multi-region deployments.
  - Use **circuit breakers** and retries to isolate failing services.
  - Ensure **backup & disaster recovery** mechanisms.

---

### **42. What is the CAP theorem and how does it apply to distributed systems?**

- **CAP theorem:** A distributed system can guarantee only **two out of three** at the same time:

  - **C – Consistency:** All nodes see the same data at the same time.
  - **A – Availability:** Every request receives a response (success or failure).
  - **P – Partition Tolerance:** System continues to operate despite network failures.

- **Application:**

  - Must choose between **CA, CP, or AP** depending on business needs.
  - Example: Banking systems prioritize **CP**, social feeds may prioritize **AP**.

---

### **43. How do you handle system failures and retries?**

- **Techniques:**

  - **Exponential backoff:** Gradually increase retry intervals.
  - **Circuit breaker pattern:** Temporarily stop requests to failing services.
  - **Idempotency:** Ensure retries do not cause duplicate effects.
  - **Fallback mechanisms:** Serve cached data or degraded functionality.
  - **Monitoring & alerting:** Detect failures and recover quickly.

---

### **44. How do you design a system for high availability?**

- **Principles:**

  - Deploy **services and databases across multiple regions/zones**.
  - Use **load balancers** to distribute traffic.
  - Implement **replication and failover** for databases.
  - Use **stateless services** so new instances can be added easily.
  - **Health checks and auto-scaling** to recover from failures automatically.

---

### **45. How do you scale a database for both read-heavy and write-heavy workloads?**

- **Read-heavy workloads:**

  - Use **read replicas** to offload queries from primary DB.
  - **Caching** frequently accessed data.
  - **Denormalization** or materialized views for faster reads.

- **Write-heavy workloads:**

  - **Sharding** to distribute writes across multiple servers.
  - **Batch writes** and asynchronous processing.
  - Consider **NoSQL databases** optimized for high write throughput.

- **Combined approach:** Use **hybrid SQL + NoSQL**, horizontal scaling, and caching to balance both.

---

### **46. How would you design a URL shortening service like bit.ly?**

- **Components:**

  - **API layer:** Create short URLs and redirect.
  - **Database:** Store mapping between short code → original URL.
  - **ID generation:** Use base62 encoding or hash functions.
  - **Caching:** Redis for frequently accessed URLs.
  - **Scalability:** Shard database by hash or range; use CDN for redirects.

---

### **47. How would you design a real-time leaderboard system?**

- **Components:**

  - **Data store:** Use in-memory DB like Redis for fast score updates.
  - **Sorted sets:** Maintain rankings efficiently.
  - **Update mechanism:** Increment scores in real-time via events or WebSockets.
  - **Caching:** Top N users cached for faster reads.
  - **Horizontal scaling:** Partition by game or region.

---

### **48. How would you design a video streaming platform like YouTube?**

- **Components:**

  - **Storage:** Blob storage (S3) for videos, thumbnails.
  - **CDN:** Deliver videos globally.
  - **Encoding:** Transcode videos to multiple resolutions.
  - **Database:** Store metadata, user interactions.
  - **Streaming:** HLS/DASH for adaptive streaming.
  - **Scalability:** Microservices for upload, streaming, analytics.

---

### **49. How would you design an e-commerce website with millions of users?**

- **Components:**

  - **Frontend:** React + caching.
  - **Backend:** Microservices for products, orders, payments, inventory.
  - **Database:** SQL for orders, NoSQL for product catalog & caching.
  - **Search:** Elasticsearch for fast product search.
  - **Scalability:** Load balancers, horizontal scaling, CDN for static content.
  - **Reliability:** Replication, failover, monitoring, rate limiting.

---

### **50. How would you design a social media feed (like Instagram/Twitter)?**

- **Feed generation:**

  - **Push model:** Precompute feeds for active users (low-latency).
  - **Pull model:** Compute feed on demand for less active users.

- **Database:** NoSQL for posts, likes, comments.
- **Caching:** Redis for top posts and timelines.
- **Scalability:** Partition users by ID, shard data, CDN for media.
- **Real-time updates:** WebSockets or push notifications.

---

### **51. How would you design a notification system for millions of users?**

- **Components:**

  - **Message broker:** Kafka or RabbitMQ for distributing events.
  - **Notification service:** Sends email, push, SMS.
  - **User preferences:** Store notification settings per user.
  - **Scalability:** Queue workers horizontally to handle high load.
  - **Real-time updates:** Use WebSockets for push notifications.

---

### **52. How would you design a search engine for large-scale data?**

- **Components:**

  - **Crawler:** Collects data from sources.
  - **Indexer:** Stores inverted indexes for fast retrieval.
  - **Query processor:** Handles search queries efficiently.
  - **Database:** Distributed storage like Elasticsearch, Solr.
  - **Scalability:** Shard indexes, cache top queries, CDNs for static search results.

---

### **53. How would you handle large file uploads and storage?**

- **Techniques:**

  - **Chunked uploads:** Split large files into smaller chunks.
  - **Direct-to-cloud storage:** Upload to S3 or GCS to reduce server load.
  - **Resume capability:** Support retry of failed chunks.
  - **Metadata database:** Track files, ownership, and status.
  - **CDN:** Deliver large files efficiently to users globally.

---

### **54. How would you design a recommendation system?**

- **Types:**

  - **Collaborative filtering:** Recommend based on user behavior similarity.
  - **Content-based filtering:** Recommend based on item attributes.
  - **Hybrid:** Combine both methods.

- **Architecture:**

  - **Data collection:** Track user interactions.
  - **Processing:** Use batch jobs for offline model training.
  - **Serving:** Cache recommendations for fast retrieval.
  - **Scalability:** Use distributed computing (Spark, Hadoop).

---

### **55. How would you design a stock market real-time dashboard?**

- **Components:**

  - **Data ingestion:** Stream live stock prices via Kafka or WebSockets.
  - **In-memory cache:** Redis for latest prices.
  - **Real-time updates:** WebSockets to push updates to clients.
  - **Database:** Time-series DB (InfluxDB, TimescaleDB) for historical data.
  - **Scalability:** Microservices for ingestion, processing, and API layer.
  - **Monitoring & alerts:** Track anomalies and failures.

---

### **56. How do you secure APIs in a distributed system?**

- **Techniques:**

  - Use **HTTPS** for encrypted communication.
  - Implement **authentication** (JWT, OAuth 2.0, API keys).
  - Use **authorization** to control access per user/service.
  - **Input validation & sanitization** to prevent injection attacks.
  - **Rate limiting** and throttling to prevent abuse.
  - **Logging & monitoring** to detect suspicious activity.

---

### **57. How do you prevent DDoS attacks?**

- **Strategies:**

  - **Rate limiting:** Restrict excessive requests per IP.
  - **CDN / WAF:** Use Cloudflare, AWS CloudFront to absorb traffic.
  - **Load balancers:** Distribute requests across multiple servers.
  - **IP blacklisting & geofencing:** Block malicious sources.
  - **Autoscaling:** Handle traffic spikes without crashing.

---

### **58. How do you implement rate limiting?**

- **Purpose:** Prevent overload and abuse.
- **Techniques:**

  - **Fixed window:** Allow N requests per time window.
  - **Sliding window:** More accurate request tracking over moving time.
  - **Token bucket / leaky bucket:** Smooth bursts of traffic.

- **Implementation:**

  - Use **API gateway** (e.g., Kong, Nginx) or distributed cache like **Redis** to store counters.

---

### **59. How do you monitor distributed systems for failures?**

- **Techniques & tools:**

  - **Health checks:** Periodic pings to services.
  - **Centralized logging:** ELK stack (Elasticsearch, Logstash, Kibana).
  - **Metrics & monitoring:** Prometheus, Grafana for CPU, memory, latency.
  - **Alerting:** Trigger notifications for errors or SLA breaches.
  - **Tracing:** Distributed tracing (Jaeger, OpenTelemetry) to detect bottlenecks.

---

### **60. How do you handle authentication and authorization in microservices?**

- **Authentication:** Verify user identity.

  - Use **JWT tokens** or OAuth 2.0 for stateless auth.
  - Token issued by **auth service**, validated by microservices.

- **Authorization:** Control access to resources.

  - Use **role-based (RBAC)** or **attribute-based access control (ABAC)**.
  - Each microservice checks token claims or permissions before allowing access.

- **Best practices:**

  - Keep services **stateless**.
  - Refresh tokens periodically.
  - Centralize auth logic in **API gateway or auth service**.

---

### **1. How do you design a fault-tolerant system?**

- **Techniques:**

  - **Redundancy:** Deploy multiple instances of services and databases.
  - **Failover mechanisms:** Automatic switch to backup systems on failure.
  - **Circuit breakers:** Prevent cascading failures.
  - **Replication:** Keep data copies across nodes or regions.
  - **Monitoring & alerts:** Detect failures and recover quickly.
  - **Stateless services:** Easier to replace failed instances without loss of data.

---

### **2. What is the difference between synchronous and asynchronous processing?**

| Aspect   | Synchronous               | Asynchronous                     |
| -------- | ------------------------- | -------------------------------- |
| Flow     | Caller waits for response | Caller continues without waiting |
| Latency  | Potentially higher        | Usually lower                    |
| Coupling | Tightly coupled           | Loosely coupled                  |
| Example  | REST API call             | Message queue (Kafka, RabbitMQ)  |

---

### **3. How do you handle service discovery in microservices?**

- **Techniques:**

  - **Client-side discovery:** Client queries the service registry to find service instances.
  - **Server-side discovery:** API gateway or load balancer routes requests to appropriate service instance.

- **Tools:** Consul, Eureka, Zookeeper, or Kubernetes DNS-based service discovery.

---

### **4. What is a service registry and why is it needed?**

- **Service registry:** Central database of all available service instances.
- **Purpose:**

  - Keeps track of dynamic IPs/ports of services.
  - Enables **service discovery** so microservices can communicate without hardcoding addresses.
  - Helps with **load balancing** and failover.

---

### **5. How do you design a stateless application?**

- **Principles:**

  - Don’t store session or client data on the server.
  - Store user state in **databases, caches, or cookies**.
  - Each request is independent and self-contained.
  - Benefits: Easy **horizontal scaling**, failover, and simpler deployment.

---

### **6. What are some common design patterns for scalable systems?**

- **Patterns:**

  - **Load balancer:** Distribute requests across servers.
  - **Caching pattern:** Reduce database load with Redis/Memcached.
  - **Queue-based load leveling:** Smooth traffic spikes.
  - **Circuit breaker:** Prevent cascading failures.
  - **Microservices pattern:** Decouple services for scalability.
  - **Database sharding:** Partition data across multiple nodes.

---

### **7. How do you handle cross-region replication?**

- **Purpose:** Improve availability, reduce latency, and disaster recovery.
- **Techniques:**

  - **Database replication:** Sync primary DB with replicas in other regions.
  - **Event-driven replication:** Use message brokers to propagate changes.
  - **CDN for static content:** Serve data from nearest region.

- **Considerations:** Handle **latency, eventual consistency, and conflict resolution**.

---

### **8. How do you design multi-tenant applications?**

- **Approaches:**

  - **Shared database, shared schema:** Multiple tenants share same tables (simplest, less isolation).
  - **Shared database, separate schema:** Each tenant has its own schema (better isolation).
  - **Separate database per tenant:** Maximum isolation and flexibility (costlier).

- **Other considerations:** Tenant-specific caching, rate limiting, and data security.

---

### **9. What are throttling and rate limiting, and how do they differ?**

- **Rate limiting:** Restricts number of requests over a time window.
- **Throttling:** Temporarily slows down request processing to prevent overload.
- **Difference:**

  - Rate limiting **blocks excess requests**.
  - Throttling **queues or delays requests** instead of blocking them.

---

### **10. How do you design a system for disaster recovery?**

- **Strategies:**

  - **Backup & restore:** Periodic snapshots of databases and storage.
  - **Multi-region deployment:** Run services and DB replicas in multiple regions.
  - **Failover automation:** Automatic switch to backup region or server.
  - **Monitoring & alerting:** Detect failures quickly.
  - **DR testing:** Regularly test recovery procedures.

---

### **11. How do you choose between SQL and NoSQL for a new feature?**

- **SQL:**

  - Structured data with relationships.
  - Strong consistency and ACID compliance.
  - Example: Banking transactions, order management.

- **NoSQL:**

  - Flexible schema, high scalability.
  - Optimized for large-scale distributed workloads.
  - Example: Social media feeds, product catalogs.

- **Decision factors:** Data structure, consistency requirements, expected traffic, query patterns.

---

### **12. What is a distributed database and how does it work?**

- **Definition:** A database where data is stored across multiple nodes/machines.
- **How it works:**

  - **Sharding:** Split data across nodes.
  - **Replication:** Copies of data across nodes for fault tolerance.
  - **Consistency protocols:** Ensure data integrity (e.g., eventual or strong consistency).
  - **Benefits:** High availability, scalability, fault tolerance.

---

### **13. How do you handle schema migrations in production?**

- **Techniques:**

  - **Versioned migrations:** Track schema changes in scripts (e.g., Flyway, Liquibase).
  - **Backward-compatible changes:** Add new columns or tables before removing old ones.
  - **Blue-Green deployment:** Deploy new schema alongside old schema.
  - **Testing & rollback:** Test migrations on staging; maintain rollback scripts.

---

### **14. How do you handle large-scale analytics queries?**

- **Techniques:**

  - Use **columnar databases** (Redshift, BigQuery) for faster aggregation.
  - **Data warehousing:** ETL pipelines to pre-process and store analytical data.
  - **Partitioning & indexing:** Optimize queries on large datasets.
  - **Caching & materialized views:** Store frequent query results for faster access.

---

### **15. How do you design a logging system with high write throughput?**

- **Components:**

  - **Append-only log storage:** Kafka or ElasticSearch for high write throughput.
  - **Batch writes:** Aggregate logs before storing to reduce I/O.
  - **Sharding:** Distribute log data across multiple nodes.
  - **Retention policies:** Archive or delete old logs to save storage.

- **Goal:** Handle millions of log events per second efficiently.

---

### **16. What is a time-series database and when would you use it?**

- **Definition:** Optimized for storing sequential, timestamped data.
- **Use cases:**

  - Metrics, monitoring, IoT sensor data, stock prices.

- **Features:** Efficient inserts, compression, and aggregation over time windows.
- **Examples:** InfluxDB, TimescaleDB, Prometheus.

---

### **17. How do you handle hot spots in a sharded database?**

- **Problem:** Certain shards receive disproportionate traffic.
- **Solutions:**

  - **Re-sharding:** Redistribute keys more evenly.
  - **Consistent hashing:** Distribute load dynamically.
  - **Caching hot keys:** Reduce database load with Redis/Memcached.
  - **Load balancing across replicas** to avoid a single hotspot.

---

### **18. How do you design a key-value store for millions of keys?**

- **Components:**

  - **Distributed storage:** Partition keys across nodes (consistent hashing).
  - **In-memory caching:** Fast access for frequently accessed keys.
  - **Replication:** Ensure fault tolerance.
  - **Persistence:** Periodically write data to disk for durability.

- **Examples:** Redis, DynamoDB, Cassandra.

---

### **19. How do you design a metadata storage system for large files?**

- **Architecture:**

  - **Metadata DB:** Stores file info (size, type, owner, location).
  - **Blob storage:** Actual files stored in S3, GCS, or HDFS.
  - **Indexing:** Efficient queries by user, date, or tags.
  - **Replication & backup:** Ensure fault tolerance.

---

### **20. How do you design a system to archive old data efficiently?**

- **Strategies:**

  - **Tiered storage:** Move old data to cheaper storage (cold storage, Glacier).
  - **Partitioning:** Separate active and archival data.
  - **Batch processing:** Periodically move/archive data in bulk.
  - **Retention policies:** Automatically delete or compress old data.
  - **Query routing:** Direct old data queries to archive storage.

---

### **21. How do you implement a distributed cache?**

- **Purpose:** Improve read performance and reduce load on databases.
- **Techniques:**

  - Use in-memory data stores like **Redis** or **Memcached**.
  - **Partitioning/Sharding:** Split cache across multiple nodes to handle large data sets.
  - **Replication:** Keep multiple copies for fault tolerance.
  - **Client-side libraries:** Ensure cache reads/writes are consistent.

- **Example:** Store frequently accessed product details in Redis across multiple app servers.

---

### **22. How do you prevent cache stampede?**

- **Problem:** Many requests simultaneously miss the cache and hit the database.
- **Solutions:**

  - **Mutex/lock:** Only one process rebuilds the cache; others wait.
  - **Early expiration/random TTL:** Add jitter to cache expiry to prevent simultaneous expirations.
  - **Request coalescing:** Queue requests until cache is rebuilt.

---

### **23. How do you design cache invalidation strategies?**

- **Strategies:**

  - **Time-based (TTL):** Cache expires automatically after a set time.
  - **Write-through:** Update cache immediately when DB changes.
  - **Write-back:** Update cache first, then asynchronously update DB.
  - **Manual invalidation:** Explicitly delete/update cache when data changes.

- **Rule:** Always maintain consistency between cache and DB.

---

### **24. How do you handle cache consistency in distributed systems?**

- **Techniques:**

  - **Event-driven invalidation:** Use DB change events or message queues to update cache.
  - **Versioning:** Attach version numbers or timestamps to cached data.
  - **Client-side checks:** Validate cache entry before use.
  - **Read-through caching:** Application always fetches from cache; cache updates DB asynchronously.

- **Goal:** Avoid stale data while maintaining high performance.

---

### **25. How do you cache database queries efficiently?**

- **Best practices:**

  - Cache **frequently accessed or computationally expensive queries**.
  - Use **key design:** Include query parameters in cache key to avoid collisions.
  - Implement **TTL** to prevent stale data.
  - **Invalidate cache** on updates to underlying data.
  - Use **lazy or eager caching** depending on usage patterns.

---

### **26. How do you design APIs for high throughput?**

- **Techniques:**

  - Use **stateless design** so servers can scale horizontally.
  - Implement **caching** at API or database level (Redis, CDN).
  - Use **pagination** and **filtering** for large datasets.
  - Apply **asynchronous processing** for long-running tasks.
  - Optimize payload with **compression** (gzip) and **efficient serialization** (JSON, Protobuf).
  - Use **connection pooling** and **load balancers** to distribute requests.

---

### **27. How do you handle versioning in APIs?**

- **Approaches:**

  - **URL versioning:** `/api/v1/users`
  - **Header versioning:** `Accept: application/vnd.myapp.v1+json`
  - **Query parameter versioning:** `/api/users?version=1`

- **Goal:** Allow clients to continue using older versions while introducing new features.

---

### **28. How do you ensure backward compatibility in API changes?**

- **Techniques:**

  - Avoid removing or renaming fields in responses.
  - Add **optional fields** instead of mandatory changes.
  - Use **default values** for new fields.
  - Maintain old endpoints until all clients migrate.
  - Deprecate endpoints gradually and communicate changes clearly.

---

### **29. How do you design a rate-limited public API?**

- **Techniques:**

  - Assign **request quotas** per user or API key.
  - Implement **rate limiting algorithms:** fixed window, sliding window, token bucket.
  - Use **API gateways** (Kong, Nginx, AWS API Gateway) for enforcement.
  - Return appropriate **HTTP status codes** (e.g., 429 Too Many Requests).
  - Optionally implement **burst handling** to smooth traffic spikes.

---

### **30. How do you implement API monitoring and logging?**

- **Techniques & tools:**

  - **Centralized logging:** ELK stack, Fluentd, or CloudWatch.
  - **Metrics collection:** Track latency, error rates, throughput (Prometheus, Grafana).
  - **Distributed tracing:** Identify bottlenecks across microservices (Jaeger, OpenTelemetry).
  - **Alerts & notifications:** Notify on SLA breaches or unusual patterns.
  - **Health checks:** Periodic pings to ensure API endpoints are responsive.

---

### **31. How do you design a stock trading system with real-time updates?**

- **Architecture:**

  - **WebSockets** for real-time price and trade updates.
  - **Event-driven backend** using message brokers (Kafka, RabbitMQ) to process trades.
  - **Database:** High-throughput, low-latency storage (e.g., in-memory DB + persistent DB).
  - **Scalability:** Partition by stock symbols or user accounts.
  - **Consistency:** Ensure transactions are atomic; use optimistic/pessimistic locking.
  - **Monitoring & alerts:** Track anomalies or failed trades.

---

### **32. How do you design a multiplayer game backend?**

- **Architecture:**

  - **Server clusters** for real-time game sessions.
  - **State synchronization:** Maintain authoritative game state on the server.
  - **WebSockets / UDP:** Real-time communication with clients.
  - **Scaling:** Use **sharding** for game rooms or regions.
  - **Latency optimization:** Place servers closer to players (CDN + edge servers).
  - **Persistence:** Save player progress and stats asynchronously to the database.

---

### **33. How do you handle offline users in real-time apps?**

- **Techniques:**

  - **Message queues:** Store updates/events for offline users (e.g., Kafka, Redis streams).
  - **Push notifications:** Inform users when they reconnect.
  - **Synchronization on reconnect:** Replay missed events from queue or database.
  - **Conflict resolution:** Merge changes if multiple updates occurred while offline.

---

### **34. How do you scale WebSocket connections to millions of users?**

- **Techniques:**

  - **Horizontal scaling:** Deploy multiple WebSocket servers behind a load balancer.
  - **Sticky sessions:** Ensure a client consistently connects to the same server.
  - **Message broker:** Use Redis Pub/Sub or Kafka to propagate messages across servers.
  - **Connection management:** Use connection pooling, heartbeat/ping-pong to detect dead connections.
  - **Edge servers/CDN:** Terminate connections closer to users to reduce latency.

---

### **35. How do you implement message ordering in real-time systems?**

- **Techniques:**

  - **Sequence numbers:** Attach incremental IDs to messages and reorder on the client if necessary.
  - **Partitioning:** Send related messages through the same partition/topic in a message broker.
  - **FIFO queues:** Use message queues that guarantee first-in-first-out delivery (SQS FIFO, Kafka partitions).
  - **Timestamps & buffering:** Temporarily buffer out-of-order messages and deliver them in sequence.

---

### **36. How do you handle distributed transactions across microservices?**

- **Challenges:** Microservices have separate databases; traditional ACID transactions don’t work.
- **Techniques:**

  - **Saga pattern:** Break transactions into a series of local transactions with compensating actions on failure.
  - **Two-phase commit (2PC):** Ensures atomicity but adds latency and complexity.
  - Prefer **event-driven eventual consistency** in most modern architectures.

---

### **37. How do you implement eventual consistency in microservices?**

- **Techniques:**

  - **Asynchronous events:** Services publish events after updating local DB.
  - **Event consumers:** Other services consume events and update their own state.
  - **Conflict resolution:** Use timestamps, versioning, or CRDTs for data convergence.
  - **Benefits:** Improves scalability and decouples services, though data may be slightly stale temporarily.

---

### **38. How do you design an event-driven architecture?**

- **Components:**

  - **Producers:** Emit events when state changes occur.
  - **Event broker:** Kafka, RabbitMQ, or AWS SNS/SQS to distribute events.
  - **Consumers:** Services subscribe and react to events asynchronously.
  - **Patterns:** Pub/Sub, event sourcing, CQRS.

- **Benefits:** Loose coupling, scalability, and real-time updates.

---

### **39. How do you handle message retries in a queue?**

- **Techniques:**

  - **Dead-letter queue (DLQ):** Store failed messages for later inspection.
  - **Exponential backoff:** Retry messages with increasing delay.
  - **Idempotency:** Ensure repeated message processing doesn’t cause inconsistent state.
  - **Monitoring:** Alert if retry failures exceed threshold.

---

### **40. How do you design an audit logging system for microservices?**

- **Architecture:**

  - **Centralized logging:** Aggregate logs from all microservices using ELK stack, Fluentd, or Kafka.
  - **Immutable logs:** Store audit events in append-only storage for compliance.
  - **Structured events:** Include metadata like user ID, timestamp, operation type.
  - **Query & retention:** Optimize for fast queries and implement retention policies.

- **Goal:** Track all critical actions for security, compliance, and debugging.

---
