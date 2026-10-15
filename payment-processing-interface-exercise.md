# CDG-HYD-JFS-061

## Payment Processing Interface Exercise

**Level:** Beginner  
**Application:** Interactive console application  
**Approach:** Object-oriented programming using an interface and implementing classes

## 1. Problem statement

A small online store accepts payments using different payment methods. The store needs a console application that allows a user to select a payment method, enter a payment amount, and process the payment.

Create a Java application called **Payment Processing System**. The application must support payments using **Credit Card**, **UPI**, and **Bank Transfer**.

Use a common Java interface so that each payment method provides its own implementation of the payment operation. The application should work with the interface type rather than depending directly on a particular implementation class.

This is a practice exercise: do not connect to a real bank, payment gateway, or external service. Simulate successful payments by displaying messages in the console.

## 2. Console menu

Display this menu repeatedly until the user chooses Exit:

```text
PAYMENT PROCESSING SYSTEM

1. Pay using Credit Card
2. Pay using UPI
3. Pay using Bank Transfer
4. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Pay using Credit Card | Read the payment amount and process it using the credit-card implementation. |
| Pay using UPI | Read the payment amount and process it using the UPI implementation. |
| Pay using Bank Transfer | Read the payment amount and process it using the bank-transfer implementation. |
| Exit | Display `Thank you for using the Payment Processing System.` and end the program. |

For every successful payment, display the payment method, amount, and a confirmation message. Format the amount to two decimal places.

## 4. Rules and validation

1. The payment amount must be greater than `0`.
2. Reject zero or negative amounts with `Invalid amount. Enter an amount greater than 0.`
3. Reject menu choices outside 1 to 4 with `Invalid choice. Choose 1 to 4.`
4. Do not process a payment if its amount is invalid.
5. Simulate payment processing only. Do not collect real card numbers, UPI PINs, passwords, or bank credentials.
6. For this exercise, assume the user enters numeric values at numeric prompts. Handling non-numeric input is an optional extension.
7. Each implementation class must provide its own implementation of the interface method.
8. The menu-handling code should use an interface reference to call the payment operation.

## 5. Suggested object-oriented design

Create five classes and one interface.

### Interface: `Payment`

Declare the following method:

```java
public interface Payment {
    void pay(double amount);
}
```

The interface defines the operation that all payment methods must provide. It does not implement the payment behavior itself.

### Class 1: `CreditCardPayment`

- Implements the `Payment` interface.
- Implements `pay(double amount)`.
- Displays a message indicating that the credit-card payment was processed.

Example output:

```text
Payment method: Credit Card
Amount: 1250.00
Credit-card payment processed successfully.
```

### Class 2: `UpiPayment`

- Implements the `Payment` interface.
- Implements `pay(double amount)`.
- Displays a message indicating that the UPI payment was processed.

Example output:

```text
Payment method: UPI
Amount: 500.00
UPI payment processed successfully.
```

### Class 3: `BankTransferPayment`

- Implements the `Payment` interface.
- Implements `pay(double amount)`.
- Displays a message indicating that the bank-transfer payment was processed.

Example output:

```text
Payment method: Bank Transfer
Amount: 3000.00
Bank-transfer payment processed successfully.
```

### Class 4: `PaymentApplication`

This class contains `main()`. It should:

- Create a `Scanner` to read console input.
- Display the menu repeatedly.
- Read the user's choice.
- Validate the menu choice and payment amount.
- Create the appropriate implementation object.
- Store that object in a variable of type `Payment`.
- Invoke `pay(amount)` using the `Payment` reference.
- Exit when the user chooses option 4.

Use this pattern when processing a payment:

```java
Payment payment;

switch (choice) {
    case 1:
        payment = new CreditCardPayment();
        break;
    case 2:
        payment = new UpiPayment();
        break;
    case 3:
        payment = new BankTransferPayment();
        break;
    default:
        // Handle an invalid choice.
        return;
}

// Read and validate the amount before calling:
payment.pay(amount);
```

Adapt the control flow as needed so that an invalid menu choice does not terminate the application unexpectedly.

### Class 5: `PaymentDemo` (optional)

If you want to keep the application class focused on user interaction, create a separate demo class to demonstrate polymorphism by passing different implementations through a `Payment` reference. This class is optional; the main exercise can be completed with the four required types above.

### Suggested project structure

```text
PaymentProcessingSystem/
└── src/
    ├── Payment.java
    ├── CreditCardPayment.java
    ├── UpiPayment.java
    ├── BankTransferPayment.java
    └── PaymentApplication.java
```

**Important:** Keep the interface and implementation classes separate. Do not place all payment behavior inside `main()`, and do not use `if-else` statements inside one class to simulate all three payment implementations.

## 6. Sample console session

The menu is shown once below. In your application, show it again after each operation. Numbers following prompts represent user input.

```text
PAYMENT PROCESSING SYSTEM

1. Pay using Credit Card
2. Pay using UPI
3. Pay using Bank Transfer
4. Exit

Enter your choice: 1
Enter payment amount: 1250
Payment method: Credit Card
Amount: 1250.00
Credit-card payment processed successfully.

Enter your choice: 2
Enter payment amount: 500
Payment method: UPI
Amount: 500.00
UPI payment processed successfully.

Enter your choice: 3
Enter payment amount: 3000
Payment method: Bank Transfer
Amount: 3000.00
Bank-transfer payment processed successfully.

Enter your choice: 1
Enter payment amount: -100
Invalid amount. Enter an amount greater than 0.

Enter your choice: 8
Invalid choice. Choose 1 to 4.

Enter your choice: 4
Thank you for using the Payment Processing System.
```

## 7. Sample validation cases

Each row describes a separate case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| Application running | Menu choice `1`, amount `1250` | Credit-card payment confirmation; amount displayed as `1250.00`. |
| Application running | Menu choice `2`, amount `500` | UPI payment confirmation; amount displayed as `500.00`. |
| Application running | Menu choice `3`, amount `3000` | Bank-transfer payment confirmation; amount displayed as `3000.00`. |
| Application running | Menu choice `1`, amount `0` | `Invalid amount. Enter an amount greater than 0.` No payment is processed. |
| Application running | Menu choice `2`, amount `-50` | `Invalid amount. Enter an amount greater than 0.` No payment is processed. |
| Application running | Menu choice `8` | `Invalid choice. Choose 1 to 4.` |
| Application running | Menu choice `4` | `Thank you for using the Payment Processing System.` |

## 8. Completion checklist

- Declare a `Payment` interface with the `pay(double amount)` method.
- Implement `Payment` in `CreditCardPayment`, `UpiPayment`, and `BankTransferPayment`.
- Provide a distinct implementation of `pay()` in each class.
- Use a `Payment` reference to invoke `pay()` on different implementation objects.
- Validate the menu choice and payment amount.
- Keep menu handling and input reading in `PaymentApplication`.
- Repeat the menu until the user chooses Exit.

**Skills practised:** interfaces, `implements`, method implementation, abstraction, polymorphism, interface references, classes, objects, `switch`, validation, and console input.

## 9. Optional extensions

1. Add a `String getPaymentMethod()` method to the interface and implement it in all three classes.
2. Add a fourth implementation, `WalletPayment`, without changing the existing payment classes.
3. Add a `PaymentService` class that accepts a `Payment` object and calls `pay(amount)`.
4. Explore why `Payment payment = new UpiPayment();` is valid.
