## 🧠 SOLID Principles in Java

### 🔹 S - Single Responsibility Principle (SRP)
A class should have only one reason to change.

```java
class InvoicePrinter {
    void printInvoice(Invoice invoice) { /* printing logic */ }
}

class InvoiceSaver {
    void saveInvoice(Invoice invoice) { /* saving logic */ }
}
```

### 🔹 O - Open/Closed Principle (OCP)
Software entities should be open for extension, but closed for modification.

```java
interface Discount {
    double apply(double price);
}

class NewYearDiscount implements Discount {
    public double apply(double price) { return price * 0.9; }
}

class Invoice {
    double calculatePrice(Discount discount, double price) {
        return discount.apply(price);
    }
}
```

### 🔹 L - Liskov Substitution Principle (LSP)
Subtypes should be substitutable for their base types.

```java
class Bird {
    void fly() { System.out.println("Flying"); }
}

class Crow extends Bird { }

class Ostrich extends Bird {
    @Override
    void fly() { throw new UnsupportedOperationException(); } // violates LSP
}
```

### 🔹 I - Interface Segregation Principle (ISP)
Clients should not be forced to depend on interfaces they do not use.

```java
interface Printer {
    void print();
}

interface Scanner {
    void scan();
}

class MultiFunctionPrinter implements Printer, Scanner {
    public void print() {}
    public void scan() {}
}

class SimplePrinter implements Printer {
    public void print() {}
}
```

### 🔹 D - Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules; both should depend on abstractions.

```java
interface Database {
    void connect();
}

class MySQLDatabase implements Database {
    public void connect() { System.out.println("Connected to MySQL"); }
}

class DataAccess {
    Database db;
    DataAccess(Database db) { this.db = db; }
    void init() { db.connect(); }
}
```

---

## 📚 References
- [DigitalOcean SOLID Guide](https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)
- [YouTube Playlist - SOLID](https://www.youtube.com/playlist?list=PL6n9fhu94yhXjG1w2blMXUzyDrZ_eyOme)
