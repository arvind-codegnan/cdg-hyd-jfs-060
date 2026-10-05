# Student Marks Array Exercise

**Level:** Beginner  
**Application:** Interactive console application  
**Approach:** Object-oriented programming with a one-dimensional array

## 1. Problem statement

A teacher conducts a test for a small group of students. The teacher needs a console application to record the marks of up to **five students** and review their results.

Create a Java application called **Student Marks Register**. The teacher should be able to add a student's mark, view all recorded marks, correct a student's mark, and view a summary.

Store marks in a fixed-size integer array. Give students numbers in the order their marks are added: Student 1, Student 2, and so on. Student names, login, and file storage are outside this exercise. Records remain available while the program runs.

The array must belong to an object. The `main()` method should read input and call that object's methods to perform the operations.

## 2. Console menu

Display this menu repeatedly until the teacher chooses Exit:

```text
STUDENT MARKS REGISTER

1. Add marks
2. Display marks
3. Update marks
4. Display summary
5. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Add marks | Read one integer mark and add it at the next unused array position. Display the assigned student number. |
| Display marks | Display each recorded student number and mark. Do not display unused array positions. |
| Update marks | Read a student number and a new mark. Replace the existing mark for that student. |
| Display summary | Display the number of recorded students, total marks, average marks, and highest mark. |
| Exit | Display `Thank you!` and end the program. |

Calculate totals and the highest mark by looping through the recorded entries. Display the average to two decimal places.

## 4. Rules and validation

1. The array can store marks for a maximum of **five students**.
2. Each mark must be an integer from **0 to 100**, inclusive.
3. Student numbers start at **1**. Array indexes start at **0**.
4. A student number is valid only if that student's mark has already been recorded.
5. When there are no records, Display marks, Update marks, and Display summary must show `No marks recorded yet.`
6. When the array is full, Add marks must show `Register is full. Maximum 5 students allowed.`
7. Reject marks outside the allowed range with `Invalid marks. Enter a value from 0 to 100.`
8. Reject an invalid student number with `Invalid student number.`
9. Reject menu choices outside 1 to 5 with `Invalid choice. Choose 1 to 5.`
10. Invalid input must not add a record or change existing marks.

For the required exercise, assume the user types integers at numeric prompts. Handling non-numeric input is an optional extension.

**Important:** Zero is a valid mark. Use a separate `count` field to identify how many entries are recorded; do not treat zero as an empty position.

## 5. Suggested object-oriented design

Create two classes.

### Class 1: MarksRegister

This class owns the array and performs operations on it.

Suggested fields:

```java
public int[] marks = new int[5];
```

| Suggested method | Responsibility |
| --- | --- |
| `addMark(int mark)` | Validate the mark and available capacity, then add it and increase `count` only on success. |
| `displayMarks()` | Display recorded students and their marks. |
| `updateMark(int studentNumber, int newMark)` | Validate the existing student number and new mark, then replace the mark. |
| `getStudentCount()` | Return the number of recorded students. |
| `calculateTotal()` | Return the sum of the recorded marks. |
| `calculateAverage()` | Return the total divided by the student count using decimal division. |
| `findHighestMark()` | Return the highest recorded mark using a loop. |

Check that at least one mark exists before calculating the average or finding the highest mark. Keep the fields private; do not expose the array for direct modification from `main()`.

### Class 2: MarksApplication

This class contains `main()`. It should:

- Create one `MarksRegister` object.
- Use `Scanner` to read console input.
- Repeatedly display the menu.
- Use `switch` or `if-else` to process the choice.
- Call the `MarksRegister` object's methods.
- Stop when the teacher chooses Exit.

**Array hints:**

- Add a mark at index `count`, then increment `count`.
- Convert a student number to an array index using `studentNumber - 1`.
- Process indexes from `0` to `count - 1`.
- Use decimal division for the average, for example `total / (double) count`.

## 6. Sample console session

The menu is shown once below. In your application, show it again after each operation. Numbers following prompts represent user input.

```text
STUDENT MARKS REGISTER

1. Add marks
2. Display marks
3. Update marks
4. Display summary
5. Exit

Enter your choice: 1
Enter marks: 50
Marks added for Student 1.

Enter your choice: 1
Enter marks: 60
Marks added for Student 2.

Enter your choice: 1
Enter marks: 70
Marks added for Student 3.

Enter your choice: 2
Student 1: 50
Student 2: 60
Student 3: 70

Enter your choice: 4
Students recorded: 3
Total marks: 180
Average marks: 60.00
Highest mark: 70

Enter your choice: 3
Enter student number: 2
Enter new marks: 75
Marks updated for Student 2.

Enter your choice: 2
Student 1: 50
Student 2: 75
Student 3: 70

Enter your choice: 4
Students recorded: 3
Total marks: 195
Average marks: 65.00
Highest mark: 75

Enter your choice: 5
Thank you!
```

## 7. Sample validation cases

Each row describes a separate case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| No marks recorded | Menu choice `4` | `No marks recorded yet.` |
| Two marks recorded | Menu choice `1`, mark `105` | `Invalid marks. Enter a value from 0 to 100.` The student count stays at 2. |
| Three marks recorded | Menu choice `3`, student number `4` | `Invalid student number.` No mark changes. |
| Five marks recorded | Menu choice `1` | `Register is full. Maximum 5 students allowed.` |
| Any state | Menu choice `8` | `Invalid choice. Choose 1 to 5.` |

## 8. Completion checklist

- Use a fixed-size `int[]`; implement array operations with loops.
- Keep the array and count private inside `MarksRegister`.
- Put menu handling and input reading in `MarksApplication`.
- Ensure zero marks are displayed and included in calculations.
- Ensure updating a mark does not change the number of recorded students.
- Produce the sample results and handle the validation cases above.

**Skills practised:** arrays, indexes, loops, conditions, classes, objects, methods, and console input.

