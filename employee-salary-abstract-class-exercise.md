# CDG-HYD-JFS-062

## Employee Salary Calculator Abstract Class Exercise

**Application:** Interactive console application  
**Approach:** Object-oriented programming using an abstract class and subclasses

## 1. Problem statement

A company pays its employees using different salary structures. Some employees receive a fixed monthly salary, while others are paid based on the number of hours they work.

Create a Java application called **Employee Salary Calculator**. The application should calculate salaries for two employee types:

- **Full-time employee:** receives a fixed monthly salary.
- **Part-time employee:** receives payment based on hours worked and hourly rate.

Use an abstract class named `Employee` to represent the common employee information and behavior. Create concrete subclasses that provide their own salary-calculation logic.

The application should let the user select an employee type, enter the required details, and display the calculated salary. This exercise does not require a database or file storage.

## 2. Console menu

Display this menu repeatedly until the user chooses Exit:

```text
EMPLOYEE SALARY CALCULATOR

1. Calculate Full-time Employee Salary
2. Calculate Part-time Employee Salary
3. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Calculate full-time salary | Read the employee name and fixed monthly salary, then calculate and display the salary. |
| Calculate part-time salary | Read the employee name, hours worked, and hourly rate, then calculate and display the salary. |
| Exit | Display `Thank you!` and end the program. |

For each calculation, display the employee type, employee name, and calculated salary formatted to two decimal places.

## 4. Rules and validation

1. The employee name must not be blank.
2. The fixed monthly salary must be greater than `0`.
3. Hours worked must be greater than `0` and must not exceed `250` for this exercise.
4. The hourly rate must be greater than `0`.
5. Reject an invalid salary with `Invalid salary. Enter a value greater than 0.`
6. Reject invalid hours with `Invalid hours. Enter a value greater than 0 and at most 250.`
7. Reject an invalid hourly rate with `Invalid hourly rate. Enter a value greater than 0.`
8. Reject a blank name with `Employee name cannot be blank.`
9. Reject menu choices outside 1 to 3 with `Invalid choice. Choose 1 to 3.`
10. Do not display a salary result if any required input is invalid.
11. For this exercise, assume numeric prompts receive numeric input. Handling non-numeric input is an optional extension.

## 5. Suggested object-oriented design

Create four required types: one abstract class, two concrete subclasses, and one program class.

### Abstract class: `Employee`

This class stores common employee information and defines the behavior shared by all employee types.

Suggested fields:

```java
private String name;
```

Suggested constructor and methods:

```java
public Employee(String name) {
    this.name = name;
}

public String getName() {
    return name;
}

public abstract double calculateSalary();

public void displayDetails() {
    System.out.println("Employee name: " + name);
    System.out.printf("Calculated salary: %.2f%n", calculateSalary());
}
```

Requirements:

- Declare `Employee` using the `abstract` keyword.
- Declare `calculateSalary()` as an abstract method because each employee type calculates salary differently.
- Implement `displayDetails()` as a concrete method because the basic display behavior is shared.
- Keep the `name` field private and provide access through a getter.
- Do not attempt to instantiate `Employee` directly.

You may adjust the display method to include the employee type in the output.

### Class 1: `FullTimeEmployee`

- Extends `Employee`.
- Stores a fixed monthly salary in a private field.
- Calls the superclass constructor using `super(name)`.
- Implements `calculateSalary()` to return the fixed monthly salary.

Suggested constructor:

```java
public FullTimeEmployee(String name, double monthlySalary) {
    super(name);
    this.monthlySalary = monthlySalary;
}
```

### Class 2: `PartTimeEmployee`

- Extends `Employee`.
- Stores the number of hours worked and the hourly rate in private fields.
- Calls the superclass constructor using `super(name)`.
- Implements `calculateSalary()` by multiplying hours worked by the hourly rate.

Calculation:

```text
Salary = Hours Worked × Hourly Rate
```

Suggested method:

```java
@Override
public double calculateSalary() {
    return hoursWorked * hourlyRate;
}
```

### Class 3: `EmployeeSalaryApplication`

This class contains `main()`. It should:

- Create a `Scanner` to read console input.
- Display the menu repeatedly.
- Read and validate the user's choice.
- Read the required details for the selected employee type.
- Create a `FullTimeEmployee` or `PartTimeEmployee` object.
- Store the object in an `Employee` reference.
- Call the inherited `displayDetails()` method.
- Exit when the user chooses option 3.

Use the following pattern to demonstrate polymorphism:

```java
Employee employee;

if (choice == 1) {
    employee = new FullTimeEmployee(name, monthlySalary);
} else {
    employee = new PartTimeEmployee(name, hoursWorked, hourlyRate);
}

employee.displayDetails();
```

Adapt this pattern to your menu and validation logic. Validate all input before creating the employee object.

## 6. Sample console session

The menu is shown once below. In your application, show it again after each operation. Values following prompts represent user input.

```text
EMPLOYEE SALARY CALCULATOR

1. Calculate Full-time Employee Salary
2. Calculate Part-time Employee Salary
3. Exit

Enter your choice: 1
Enter employee name: Ananya
Enter fixed monthly salary: 45000
Employee type: Full-time
Employee name: Ananya
Calculated salary: 45000.00

Enter your choice: 2
Enter employee name: Ravi
Enter hours worked: 80
Enter hourly rate: 250
Employee type: Part-time
Employee name: Ravi
Calculated salary: 20000.00

Enter your choice: 1
Enter employee name: Meera
Enter fixed monthly salary: 0
Invalid salary. Enter a value greater than 0.

Enter your choice: 2
Enter employee name: Kiran
Enter hours worked: 300
Invalid hours. Enter a value greater than 0 and at most 250.

Enter your choice: 8
Invalid choice. Choose 1 to 3.

Enter your choice: 3
Thank you!
```

## 7. Sample validation cases

Each row describes a separate case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| Application running | Full-time employee, name `Ananya`, salary `45000` | Salary displayed as `45000.00`. |
| Application running | Part-time employee, name `Ravi`, hours `80`, rate `250` | Salary displayed as `20000.00`. |
| Application running | Full-time employee, salary `0` | `Invalid salary. Enter a value greater than 0.` |
| Application running | Part-time employee, hours `0` | `Invalid hours. Enter a value greater than 0 and at most 250.` |
| Application running | Part-time employee, hours `300` | `Invalid hours. Enter a value greater than 0 and at most 250.` |
| Application running | Part-time employee, hourly rate `-10` | `Invalid hourly rate. Enter a value greater than 0.` |
| Application running | Blank employee name | `Employee name cannot be blank.` |
| Application running | Menu choice `8` | `Invalid choice. Choose 1 to 3.` |
| Application running | Menu choice `3` | `Thank you!` |

## 8. Completion checklist

- Declare `Employee` as an abstract class.
- Store the common employee name in a private field.
- Declare `calculateSalary()` as an abstract method.
- Implement `displayDetails()` as a concrete method in `Employee`.
- Extend `Employee` in both subclasses.
- Use `super(name)` to initialize the superclass state.
- Override `calculateSalary()` in each subclass.
- Use an `Employee` reference to refer to both subclass objects.
- Validate input before displaying a salary.
- Keep menu handling and input reading in `EmployeeSalaryApplication`.
- Repeat the menu until the user chooses Exit.

**Skills practised:** abstract classes, abstract methods, concrete methods, inheritance, `extends`, constructors, `super`, method overriding, runtime polymorphism, encapsulation, validation, and console input.

## 9. Optional extensions

1. Add a `ContractEmployee` subclass that calculates payment using a contract amount.
2. Add an abstract method `getEmployeeType()` and implement it in each subclass.
3. Add a concrete method `isEligibleForBonus()` to `Employee`, with a shared default rule based on calculated salary.
4. Create an `Employee` array to store multiple employee objects and display their salaries in a loop.
5. Compare the design with an interface-based solution: identify which shared state and concrete behavior make an abstract class useful here.
