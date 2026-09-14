# Multithreaded Web Server in Java

A Java-based web server project that demonstrates the difference between **single-threaded execution, multi-threaded execution, and thread-pool based concurrency**.

The project was built to understand how web servers handle multiple client connections and how Java multithreading can improve concurrent request processing.

## 📌 Project Overview

A traditional single-threaded server processes one client request at a time. When multiple clients connect simultaneously, requests must wait for the previous request to finish.

This project explores three different approaches:

1. **Single-Threaded Server** – Handles one client connection at a time.
2. **Multi-Threaded Server** – Creates a separate thread for each client connection.
3. **Thread Pool Server** – Uses a fixed pool of reusable threads to efficiently manage multiple client connections.

The project demonstrates how concurrency changes the way a server handles multiple requests.

## 🏗️ Architecture

```text
                         Client Requests
                               │
                               ▼
                     ┌───────────────────┐
                     │    Web Server     │
                     └─────────┬─────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       Single-Threaded   Multi-Threaded    Thread Pool
           Server            Server           Server
              │                │                │
              ▼                ▼                ▼
        One request      One thread per    Reusable worker
        at a time            client           threads
```

## 📂 Project Structure

```text
MultithreadedWebServer/
│
├── SingleThreaded/
│   └── Single-threaded server implementation
│
├── Multithreaded/
│   └── Multi-threaded server implementation
│
├── ThreadPool/
│   └── Thread-pool based server implementation
│
└── README.md
```

## 🔹 1. Single-Threaded Server

The single-threaded implementation processes client connections sequentially.

```text
Client 1 ──► Server ──► Process
                         │
Client 2 ────────────────┘
                         │
                         ▼
                      Process
```

### Characteristics

* One client is processed at a time.
* Simple implementation.
* Easy to understand and debug.
* Other clients must wait while the current request is being processed.
* Not suitable for handling many concurrent clients efficiently.

## 🔹 2. Multi-Threaded Server

The multi-threaded implementation creates a separate thread for each client connection.

```text
Client 1 ──► Thread 1 ──► Server
Client 2 ──► Thread 2 ──► Server
Client 3 ──► Thread 3 ──► Server
Client 4 ──► Thread 4 ──► Server
```

### Characteristics

* Multiple clients can be processed concurrently.
* Each connection gets its own thread.
* Better responsiveness compared with a single-threaded server.
* Large numbers of clients can create many threads.
* Excessive thread creation can increase memory and CPU overhead.

## 🔹 3. Thread Pool Server

The thread-pool implementation uses a fixed set of reusable worker threads.

```text
                 Client Requests
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Request 1    Request 2    Request 3
          │            │            │
          └────────────┼────────────┘
                       ▼
              ┌─────────────────┐
              │   Thread Pool   │
              ├─────────────────┤
              │ Worker Thread 1 │
              │ Worker Thread 2 │
              │ Worker Thread 3 │
              │ Worker Thread 4 │
              └─────────────────┘
```

### Characteristics

* Reuses existing threads.
* Avoids creating a new thread for every request.
* Controls the maximum number of concurrent worker threads.
* Reduces thread creation overhead.
* More scalable than creating unlimited threads.

## ⚖️ Comparison

| Feature                   | Single-Threaded | Multi-Threaded | Thread Pool |
| ------------------------- | --------------- | -------------- | ----------- |
| Concurrent clients        | ❌ Limited       | ✅ Yes          | ✅ Yes       |
| Thread creation           | One             | One per client | Reused      |
| Implementation            | Simple          | Moderate       | Moderate    |
| Resource usage            | Low             | Higher         | Controlled  |
| Scalability               | Low             | Medium         | Higher      |
| Thread reuse              | ❌               | ❌              | ✅           |
| Suitable for many clients | ❌               | ⚠️             | ✅           |

## 🧠 Key Concepts Demonstrated

### Java Multithreading

Understanding how multiple threads can execute tasks concurrently.

### Socket Programming

Using Java networking concepts to establish communication between clients and the server.

### Concurrency

Handling multiple client requests at the same time.

### Thread Management

Understanding the difference between creating individual threads and managing reusable worker threads.

### Thread Pools

Using a controlled number of worker threads to process incoming tasks.

### Client-Server Architecture

Understanding how clients communicate with a server through network connections.

## 🛠️ Technologies Used

* **Java**
* Java Sockets
* Java Threads
* Java Concurrency
* Executor / Thread Pool concepts
* Object-Oriented Programming

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/poojakuver535/MultithreadedWebServer.git
```

### 2. Navigate to the project

```bash
cd MultithreadedWebServer
```

### 3. Choose an implementation

You can run any of the following:

```text
SingleThreaded
Multithreaded
ThreadPool
```

### 4. Compile the Java files

Example:

```bash
javac FileName.java
```

### 5. Run the server

```bash
java ClassName
```

> Replace `FileName` and `ClassName` with the actual Java file and class names in the selected implementation.

## 🔄 Request Processing Flow

```text
Client
   │
   │ Connect
   ▼
Server Socket
   │
   │ Accept Connection
   ▼
Client Socket
   │
   ▼
Request Processing
   │
   ├── Single Thread
   │
   ├── New Thread
   │
   └── Thread Pool Worker
   │
   ▼
Response
   │
   ▼
Client
```

## 🎯 What I Learned

Through this project, I gained practical understanding of:

* Java socket programming
* Client-server communication
* Java multithreading
* Thread lifecycle
* Concurrent request processing
* Thread pools
* Executor-based task management
* Resource management
* Differences between sequential and concurrent execution
* Designing a basic server architecture

## 🚀 Future Improvements

Possible improvements include:

* HTTP request parsing
* HTTP response handling
* Support for GET and POST requests
* Static file serving
* Request logging
* Graceful server shutdown
* Configurable thread-pool size
* Connection timeout handling
* Error handling
* Performance benchmarking
* Load testing with multiple concurrent clients
* Docker support

## 📊 Performance Analysis

A useful extension of this project is to compare the three implementations under increasing numbers of concurrent clients.

Metrics that can be measured include:

* Response time
* Throughput
* Number of concurrent connections
* CPU utilization
* Memory usage
* Thread creation overhead

This can help demonstrate why thread pools are commonly preferred over creating an unlimited number of threads.

## 🔗 Repository

**GitHub:**
https://github.com/poojakuver535/MultithreadedWebServer

## 👩‍💻 Author

**Pooja S**

Computer Science and Engineering Graduate

**GitHub:**
https://github.com/poojakuver535

**LinkedIn:**
https://www.linkedin.com/in/pooja-s-79538827/

---

⭐ If you found this project useful, consider giving the repository a star.
