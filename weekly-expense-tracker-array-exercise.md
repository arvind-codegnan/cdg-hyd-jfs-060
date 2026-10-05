# CDG-HYD-JFS-060

## Weekly Expense Tracker Array Exercise

**Application:** Interactive console application  
**Approach:** Object-oriented programming with arrays

Implementation requirements:

- Use two classes: one to own the arrays and perform operations, and one to contain `main()` and handle the menu.
- Keep array fields private.
- Use `Scanner`, loops, conditions, and methods.
- Display the menu repeatedly until Exit is selected.
- Keep records in memory while the program runs.
- Assume users type integers at numeric prompts; still validate ranges and state.
- Use arrays rather than collection classes for storage.
- Do not let invalid input change existing data.

Repeated menus are omitted from the sample sessions for readability.

## 1. Problem statement

A student wants to track daily spending for one week. Create a **Weekly Expense Tracker** that stores an expense amount for each day from Monday to Sunday.

All seven daily expenses start at zero. The student can record a day's expense or correct it later. Recording a new value for the same day replaces the previous value.

Use whole rupees for input. The tracker should display all daily expenses, the weekly total, the average per calendar day, and the day with the highest expense.

## 2. Console menu

```text
WEEKLY EXPENSE TRACKER

1. Record or change daily expense
2. Display weekly expenses
3. Display expense summary
4. Display highest-expense day
5. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Record or change daily expense | Read a day number and amount. Store or replace the expense for that day. |
| Display weekly expenses | Display all seven day numbers, day names, and amounts. |
| Display expense summary | Display the total expense and average daily expense. |
| Display highest-expense day | Display the day name and largest daily expense. If the total is zero, show `No expenses recorded.` |
| Exit | Display `Thank you!` and stop. |

Use day numbers 1 to 7 for Monday to Sunday. Display monetary values to two decimal places.

## 4. Rules and validation

1. Day numbers must be from 1 to 7.
2. Amounts must be non-negative integers in whole rupees.
3. Zero is a valid amount and represents no expense for that day.
4. Days not changed by the user remain zero.
5. The average is the weekly total divided by **7**, including zero-expense days.
6. Recording an amount replaces the existing daily amount; it does not add to it.
7. When several days share the highest positive expense, display the earliest one in the week.
8. Validate the day number before asking for the amount.
9. Reject invalid day numbers with `Invalid day number. Choose 1 to 7.`
10. Reject negative amounts with `Expense cannot be negative.`
11. Reject menu choices outside 1 to 5 with `Invalid choice. Choose 1 to 5.`

## 5. Suggested object-oriented design

| Class | Responsibility |
| --- | --- |
| `ExpenseTracker` | Own day names and amounts; update expenses and calculate results. |
| `ExpenseApplication` | Contain `main()`, read inputs, display the menu, and call the tracker object. |

Suggested fields in `ExpenseTracker`:

```java
private String[] dayNames = {
    "Monday", "Tuesday", "Wednesday", "Thursday",
    "Friday", "Saturday", "Sunday"
};
private int[] expenses = new int[7];
```

| Suggested method | Responsibility |
| --- | --- |
| `isValidDayNumber(int dayNumber)` | Check whether the day number is from 1 to 7. |
| `recordExpense(int dayNumber, int amount)` | Validate and store the amount at that day's index. |
| `displayExpenses()` | Display all seven days and amounts. |
| `calculateTotalExpense()` | Return the sum of all seven expenses. |
| `calculateAverageDailyExpense()` | Return the total divided by 7 using decimal division. |
| `displayHighestExpenseDay()` | Handle a zero total; otherwise find and display the highest-expense day. |

**Hints:** Use `dayNumber - 1` as the index. Use `total / 7.0` for a decimal average. During the maximum search, update the chosen index only when a strictly larger expense is found; this preserves the earliest day when values tie.

## 6. Sample console session

```text
Enter your choice: 1
Enter day number (1=Monday, ..., 7=Sunday): 1
Enter expense in whole rupees: 150
Monday expense saved: Rs. 150.00

Enter your choice: 1
Enter day number (1=Monday, ..., 7=Sunday): 2
Enter expense in whole rupees: 200
Tuesday expense saved: Rs. 200.00

Enter your choice: 1
Enter day number (1=Monday, ..., 7=Sunday): 3
Enter expense in whole rupees: 100
Wednesday expense saved: Rs. 100.00

Enter your choice: 2
1. Monday: Rs. 150.00
2. Tuesday: Rs. 200.00
3. Wednesday: Rs. 100.00
4. Thursday: Rs. 0.00
5. Friday: Rs. 0.00
6. Saturday: Rs. 0.00
7. Sunday: Rs. 0.00

Enter your choice: 3
Total expense: Rs. 450.00
Average daily expense: Rs. 64.29

Enter your choice: 4
Highest-expense day: Tuesday
Expense: Rs. 200.00

Enter your choice: 1
Enter day number (1=Monday, ..., 7=Sunday): 1
Enter expense in whole rupees: 120
Monday expense saved: Rs. 120.00

Enter your choice: 3
Total expense: Rs. 420.00
Average daily expense: Rs. 60.00

Enter your choice: 5
Thank you!
```

## 7. Sample validation cases

Each row is an independent case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| All amounts zero | Display highest-expense day | `No expenses recorded.` |
| Any state | Record expense, day `8` | `Invalid day number. Choose 1 to 7.` |
| Monday expense 150 | Record expense, day `1`, amount `-10` | `Expense cannot be negative.` Monday remains 150. |
| Monday and Tuesday each 200; other days zero | Display highest-expense day | `Highest-expense day: Monday`, then `Expense: Rs. 200.00` |
| All amounts zero | Display summary | Total `Rs. 0.00`; average `Rs. 0.00`. |

## 8. Completion checklist

- Store all seven expenses in a fixed-size array.
- Use day numbers rather than asking users for array indexes.
- Replace the correct day without affecting other days.
- Include zero-expense days in the seven-day average.
- Display the earliest day when the maximum is tied.
- Produce the sample results and validation messages.

**Skills practised:** fixed array positions, parallel arrays, updating values, totals, decimal averages, and maximum searches.

