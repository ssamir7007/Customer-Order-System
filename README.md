<div align="center">

# 🛒 Customer Order System
### A Java shopping and order-management application

![Java](https://img.shields.io/badge/Java-ED8B00?logo=openjdk&logoColor=white) ![Swing](https://img.shields.io/badge/GUI-Java_Swing-334155) ![OOP](https://img.shields.io/badge/Design-Object_Oriented-0F766E)

</div>

## Overview

A Java application that demonstrates an end-to-end shopping workflow through **both console and graphical interfaces**. The project grew from UML and class design into a console implementation, then added a **Java Swing GUI** while reusing the same backend classes.

## Features

- **Accounts:** Registration, password checks, login, and security questions
- **Catalog:** Browse products and sale prices
- **Cart:** Add and remove items, adjust quantities, and review totals
- **Checkout:** Select mail or pickup and simulate bank authorization
- **Order history:** Review orders associated with the signed-in customer
- **Two interfaces:** Console and Swing GUI backed by the same domain classes

## Architecture

| Component | Responsibility |
| --- | --- |
| `Customer`, `AccountManager` | Customer accounts and login flow |
| `Product`, `Catalog` | Product information and lookup |
| `Cart`, `CartItem` | Shopping cart and quantities |
| `Order`, `OrderManager` | Orders and checkout orchestration |
| `Bank` | Simulated payment authorization |
| `Main`, `MainGUI` | Console and graphical entry points |

## Run the application

This project uses standard Java and Swing, without an external GUI framework.

1. Clone the repository:
   ```bash
   git clone https://github.com/ssamir7007/Customer-Order-System.git
   cd Customer-Order-System
   ```
2. Open the Java source files in IntelliJ IDEA or another Java IDE.
3. Run **`Main.java`** for the console version or **`MainGUI.java`** for the graphical version.

If your checkout only contains the packaged archive, extract **`Part 3.zip`** first and locate the Java source files. The repository also includes compiled `.class` artifacts.

## Design notes

- Both interfaces share the same backend classes.
- GUI navigation uses Java Swing components and `CardLayout`.
- Data is stored in memory; it is not persisted across application restarts.
- Bank approval and denial are simulated, **not real payment processing**.

## Potential improvements

- Persistent database storage
- Automated unit tests
- Screenshots of the GUI
- More explicit separation of application and domain layers

---

Made by [Shadman Samir](https://github.com/ssamir7007) · [More projects](https://github.com/ssamir7007?tab=repositories)
