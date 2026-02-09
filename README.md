Customer Order System (COS) – Part 3
------------------------------------

This project is the final part of the Customer Order System assignment.
Part 1 focused on the UML and class design, Part 2 implemented a full
console-based version of the system, and Part 3 adds a graphical user
interface (GUI) while keeping all use cases functional.

The system now supports two complete applications:

1. A console application (Main.java)
2. A GUI application built using Java Swing (MainGUI.java)

Both applications use the SAME backend classes developed in Parts 1 and 2:
Customer, AccountManager, Catalog, Product, Cart, CartItem, Order,
OrderManager, Bank, and SecurityQuestion.


---------------------------------------------------------------------------
HOW TO RUN THE PROGRAM
---------------------------------------------------------------------------

Using IntelliJ IDEA :
----------------------------------
1. Open IntelliJ IDEA.
2. Create a new Java project (no module needed).
3. Copy all .java files into the project’s src/ folder.
4. To run the console application:
        - Open Main.java
        - Click the green Run button
5. To run the GUI application:
        - Open MainGUI.java
        - Click the green Run button

Both files contain their own main() method, so you choose which version to run.


---------------------------------------------------------------------------
HOW TO DEMONSTRATE USE CASES (CONSOLE APPLICATION)
---------------------------------------------------------------------------

1. CREATE ACCOUNT
   - From the menu, choose option 1.
   - Enter ID, password, name, address, and credit card number.
        - The password must meet ALL of the following criteria:
            • At least 6 characters long
            • Must contain at least one UPPERCASE letter
            • Must contain at least one NUMBER
            • Must contain at least one SPECIAL CHARACTER from: @ # $ % & *
        If any of these conditions are not met, the system will reject the password.
   - Choose one of the security questions and provide an answer.
   - Account is created if the password meets the rules and the ID is not taken.

2. LOG IN
   - Choose option 2.
   - Enter ID.
   - Enter password (up to 3 attempts).
   - Answer security question correctly.
   - Once both are correct, the login succeeds.

3. BROWSE CATALOG
   - Choose option 3 to view all products and any sale prices.

4. SELECT ITEMS
   - Choose option 4.
   - Type a product ID and quantity to add it to cart.
   - Type "done" when finished.
   - The running subtotal is shown as items are added.

5. MAKE ORDER
   - Choose option 5 (must be logged in).
   - Choose delivery method (MAIL adds a $3.00 fee or PICKUP).
   - The Bank system attempts to authorize credit card.
   - If authorization fails, try a different credit card.
   - If approved, the system creates an order with an authorization code.

6. VIEW ORDERS
   - Choose option 6.
   - Displays all previous orders placed by the logged-in customer.

7. LOG OUT
   - Choose option 7 to sign out and reset the cart.

8. EXIT
   - Choose option 8 to end the program.


---------------------------------------------------------------------------
HOW TO DEMONSTRATE USE CASES (GUI VERSION)
---------------------------------------------------------------------------

The GUI supports all required use cases from Parts 1 and 2. The top navigation
menu allows accessing each feature directly.

1. CREATE ACCOUNT
   - Click “Create Account” in the top toolbar.
   - Enter ID, password, name, address, credit card number, security question,
     and answer.
   - Password must meet these rules:
        • At least 6 characters long
        • At least one UPPERCASE letter
        • At least one NUMBER
        • At least one SPECIAL CHARACTER: @ # $ % & *
   - If the ID is unique and the password is valid, the account is created.

2. LOG IN
   - Click “Log In” on the toolbar.
   - Enter ID and password.
   - If the password is correct, answer the stored security question.
   - After both checks pass, you are logged in.

3. BROWSE CATALOG
   - Click “Catalog.”
   - All products are displayed in a scrollable list.
   - Select a product and choose a quantity to add it to the cart.

4. MANAGE CART
   - Click “Cart.”
   - View all items, their quantities, unit prices, and subtotal.
   - Remove items if needed.
   - Click “Checkout” to begin ordering.

5. PLACE ORDER
   - Choose delivery type:
        • MAIL (adds $3.00)
        • PICKUP (free)
   - Choose to use the stored credit card or enter a new one.
   - Bank authorization is simulated and may deny the payment.
   - If denied, the user can retry with a different card.
   - If approved, an order is created and stored.

6. VIEW ORDER HISTORY
   - Click “My Orders.”
   - Displays all previous orders placed by the logged-in user.

7. LOG OUT
   - Click “Log Out” in the toolbar.
   - The cart is cleared, and the user is logged out.


---------------------------------------------------------------------------
UML DIAGRAM DESCRIPTION (UPDATED FOR PART 3)
---------------------------------------------------------------------------

The updated UML diagram includes all backend classes from Parts 1 and 2,
plus the new MainGUI class introduced in Part 3. It shows the structure of
the system and the relationships between classes.

• MainGUI
  This is the new GUI controller class. It interacts with AccountManager,
  Catalog, OrderManager, Bank, Customer, and Cart. It provides GUI screens
  for account creation, login, product browsing, cart management, order
  placement, and order history.

• Main
  The original console-based driver. Calls the same backend classes but uses
  text-based input/output instead of a graphical interface.

• AccountManager
  Manages Customer accounts, including creation, password checks, login
  validation, and storage. Aggregates multiple Customer objects.

• Customer
  Represents a user. Stores ID, password, name, address, credit card, and
  security question/answer.

• SecurityQuestion
  Enum listing possible security questions.

• Catalog
  Stores Product objects and allows lookup by product ID.

• Product
  Represents a purchasable item, with optional sale price.

• Cart and CartItem
  Cart tracks products selected by the customer.
  CartItem stores a specific product and quantity.

• Order
  Represents a completed transaction, including delivery type, date,
  total amount, and bank authorization number.

• OrderManager
  Stores all orders and interacts with the Bank to authorize payments.

• Bank
  Simulates payment authorization and randomly denies some charges.

The diagram demonstrates how MainGUI and Main both depend on the same backend
classes, showing a clean separation between user interface and core logic.


---------------------------------------------------------------------------
CHANGES FROM PART 2 TO PART 3
---------------------------------------------------------------------------

Part 3 builds on the completed console application from Part 2 and adds a
graphical user interface using Java Swing. Below are the main changes:

1. Added **MainGUI.java**, a complete GUI application
   - Uses CardLayout to switch between screens.
   - Includes screens for:
        • Home
        • Create Account
        • Log In
        • Catalog
        • Cart
        • Checkout
        • Order History
   - Fully supports all use cases through GUI controls.

2. Integrated backend classes with GUI
   - No changes were made to the core logic classes.
   - MainGUI interacts with AccountManager, Catalog, OrderManager, Bank,
     Customer, and Cart just like Main.java.

3. Added visual components
   - Product list (JList)
   - Text areas for cart and order history
   - Buttons, labels, text fields, combo boxes, and spinners
   - Status bar for messages and feedback

4. Added input validation in the GUI
   - Ensures fields are not empty
   - Ensures quantities are positive
   - Displays clear error messages via JOptionPane dialogs

5. Updated UML diagram
   - Includes MainGUI as a new class
   - Updated relationships for GUI interactions
   - Shows structure and behavior of the full system


---------------------------------------------------------------------------
NOTES & ASSUMPTIONS
---------------------------------------------------------------------------

- The GUI and console applications both use the same backend classes.
- No external libraries are used; only Java Swing and basic Java utilities.
- All data is stored in memory and is lost when the program terminates.
- The Bank class still rejects approximately 5% of transactions to simulate
  real payment failures.
- The GUI does not allow product editing or administrative features (not
  required by assignment).
- Passwords remain stored as plain text since encryption is beyond project
  scope.


---------------------------------------------------------------------------
END OF README
---------------------------------------------------------------------------
