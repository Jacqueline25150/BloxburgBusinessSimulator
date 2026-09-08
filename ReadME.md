# Bloxburg Business Simulator

A console-based Java application simulating a business management ecosystem. Users can instantiate unique businesses, manage liquid capital structures, process employee payroll, and execute tax calculations using clean Object-Oriented Programming (OOP) design patterns.

---

## 🛠️ How This Project Was Used

The program acts as a backend business operations tracker. The executable driver logic is located inside the main entry point of the `BloxburgGame` class. When executed, it models the complete lifecycle of a business cluster through these core runtime operations:

1. **System Initialization:** Registers new commercial venues utilizing flexible instantiation models. 
2. **State Adjustment:** Demonstrates proper access control (encapsulation) by updating blank data structures via runtime setter methods.
3. **Workforce Allocation:** Dynamically establishes instances of nested `Employee` objects directly linked into the composition lists of their parent businesses.
4. **Financial Cycling:** Automates multi-tiered economic adjustments by systematically checking cash reserves, deducting recurring payroll liabilities, and executing fixed flat-rate corporate tax write-offs.

---

## 🔄 Where Method Overloading Was Implemented

Method overloading occurs when a class has multiple methods or constructors with the same name but different parameter lists. In this project, **constructor overloading** was implemented inside the `Business` class to provide three distinct ways to instantiate a company:

```java
// 1-Parameter Constructor: Used when only the name is known
public Business(String name) {
    this(name, "Unknown", 0.0); 
}

// 2-Parameter Constructor: Used for quick-start setups with predefined funds
public Business(String name, double startingFunds) {
    this(name, "Unknown", startingFunds); 
}

// 3-Parameter Constructor: Master initialization constructor
public Business(String name, String owner, double startingFunds) {
    this.name = name;
    this.owner = owner;
    this.funds = startingFunds;
    totalBusinesses++;
}
```

### ⚡ Architectural Optimization: Constructor Chaining
To prevent code duplication, **Constructor Chaining** via the `this(...)` keyword was utilized. The 1-parameter and 2-parameter constructors do not allocate memory independently; instead, they immediately pass their available arguments up to the master 3-parameter constructor. This ensures that field default assignments and global static analytics increments are processed consistently through a single centralized gateway.

---

## 📊 How Static Fields Were Used

Static fields belong to the class itself rather than individual object instances. This project utilizes two distinct types of static components:

### 1. Instance Tracking State Tracker (`totalBusinesses`)
```java
private static int totalBusinesses = 0;
```
Every time a user creates an instance of a business (e.g., `new Business("Pizza Palace")`), each discrete object gets its own unique `name`, `owner`, and `funds` tracking blocks inside memory. 

However, the `totalBusinesses` field is marked as `static`, meaning only **one shared copy** of this variable exists globally in the computer's memory. Every distinct business object looks at and modifies this exact same field. When the master constructor executes `totalBusinesses++`, it updates the global scoreboard, allowing the system to know exactly how many businesses exist at any point during runtime.

### 2. Immutable Configuration Rule Constants (`TAX_RATE`)
```java
public static final double TAX_RATE = 0.1;
```
* **`static`:** Ensures that the memory allocation for the tax rate limit ($10\%$) is shared globally among all businesses rather than redundantly copying the decimal value into every single company created.
* **`final`:** Acts as a security lock, rendering the variable immutable so that runtime code operations cannot accidentally change or alter the global tax deduction rate.
