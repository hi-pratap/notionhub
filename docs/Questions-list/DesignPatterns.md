# Design Patterns:

### 1. Singleton:

The Singleton pattern ensures that a class has only one instance and provides a global point of access to it.

**Description**:

- **Purpose:** Ensure a class has a single instance and provide a global point of access to it.
- **Use Case:** When exactly one object is needed to coordinate actions across the system.

Example:

In Java:

```java
public class Singleton {
    private static Singleton instance;

    // Private constructor to prevent instantiation
    private Singleton() {}

    // Public method to provide access to the instance
    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

```

### 2. Factory:

The Factory pattern defines an interface for creating an object but lets subclasses alter the type of objects that will be created.

**Description**:

- **Purpose:** Define an interface for creating an object, but let subclasses decide which class to instantiate.
- **Use Case:** When a class can't anticipate the class of objects it must create.

**Example**:

In Java:

```java
public abstract class Animal {
    public abstract void speak();
}

public class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("Woof");
    }
}

public class Cat extends Animal {
    @Override
    public void speak() {
        System.out.println("Meow");
    }
}

public class AnimalFactory {
    public static Animal getAnimal(String type) {
        if ("dog".equalsIgnoreCase(type)) {
            return new Dog();
        } else if ("cat".equalsIgnoreCase(type)) {
            return new Cat();
        }
        return null;
    }
}

```

### 3. Observer:

The Observer pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

**Description**:

- **Purpose:** Establish a one-to-many dependency between objects so that when one object changes state, all dependents are notified.
- **Use Case:** When an object change needs to be communicated to multiple dependent objects.

**Example**:

In Java:

```java
import java.util.ArrayList;
import java.util.List;

interface Observer {
    void update(String message);
}

class ConcreteObserver implements Observer {
    private String name;

    public ConcreteObserver(String name) {
        this.name = name;
    }

    @Override
    public void update(String message) {
        System.out.println(name + " received message: " + message);
    }
}

class Subject {
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }
}

```

### 4. Saga:

The Saga pattern manages long-running transactions by breaking them into a series of smaller, atomic steps that can be undone if necessary.

**Description**:

- **Purpose:** Manage complex, long-running business processes and transactions that span multiple microservices.
- **Use Case:** When you need to ensure data consistency across multiple services in a microservices architecture.

**Example**:

In Java, using a saga orchestrator:

```java
public class OrderService {
    public void createOrder(Order order) {
        // Step 1: Create Order
        // Step 2: Deduct Inventory
        // Step 3: Process Payment
        // Each step is a separate transaction
    }

    public void rollbackOrder(Order order) {
        // Rollback logic for the saga
    }
}

```

### 5. Circuit-Breaker:

The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.

### Description:

- **Purpose:** Protect services from repeatedly trying to execute an operation that's likely to fail, allowing time for recovery.
- **Use Case:** When dealing with remote service calls that may fail.

### Example:

In Java:

```java
public class CircuitBreaker {
    private boolean open;
    private long lastFailureTime;
    private int failureCount;
    private final int failureThreshold;
    private final long timeout;

    public CircuitBreaker(int failureThreshold, long timeout) {
        this.failureThreshold = failureThreshold;
        this.timeout = timeout;
        this.open = false;
        this.failureCount = 0;
        this.lastFailureTime = 0;
    }

    public synchronized boolean allowRequest() {
        if (open && (System.currentTimeMillis() - lastFailureTime) > timeout) {
            open = false;
            failureCount = 0;
        }
        return !open;
    }

    public synchronized void recordFailure() {
        failureCount++;
        lastFailureTime = System.currentTimeMillis();
        if (failureCount >= failureThreshold) {
            open = true;
        }
    }

    public synchronized void recordSuccess() {
        failureCount = 0;
        open = false;
    }
}

```

### 6. Strategy:

The Strategy pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable.

### Description:

- **Purpose:** Define a family of algorithms, encapsulate each one, and make them interchangeable.
- **Use Case:** When you need to select an algorithm at runtime.

### Example:

In Java:

```java
public interface Strategy {
    int execute(int a, int b);
}

public class AdditionStrategy implements Strategy {
    @Override
    public int execute(int a, int b) {
        return a + b;
    }
}

public class SubtractionStrategy implements Strategy {
    @Override
    public int execute(int a, int b) {
        return a - b;
    }
}

public class Context {
    private Strategy strategy;

    public void setStrategy(Strategy strategy) {
        this.strategy = strategy;
    }

    public int executeStrategy(int a, int b) {
        return strategy.execute(a, b);
    }
}

```

### 7. Retry:

The Retry pattern enables an application to handle transient failures by retrying an operation that has previously failed.

### Description:

- **Purpose:** Handle transient failures by retrying an operation that has previously failed.
- **Use Case:** When dealing with operations that might temporarily fail but succeed if retried.

### Example:

In Java:

```java
public class RetryPolicy {
    private int maxRetries;
    private long delay;

    public RetryPolicy(int maxRetries, long delay) {
        this.maxRetries = maxRetries;
        this.delay = delay;
    }

    public void execute(Runnable task) {
        int attempt = 0;
        while (attempt < maxRetries) {
            try {
                task.run();
                return; // Success
            } catch (Exception e) {
                attempt++;
                if (attempt >= maxRetries) {
                    throw e;
                }
                try {
                    Thread.sleep(delay);
                } catch (InterruptedException ie) {
                    Thread.currentThread().interrupt();
                }
            }
        }
    }
}

```

These examples provide a good starting point for implementing these design patterns in your applications. Each pattern has specific use cases and benefits, and understanding them can help in designing robust and maintainable systems.