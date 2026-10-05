# CDG-HYD-JFS-060

## Movie Seat Booking System Array Exercise

**Level:** Beginner  
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

A small screening room has five seats in one row. A booking-counter operator needs a console application to see which seats are free, book a seat, and cancel a booking.

Create a **Movie Seat Booking System** using a boolean array. Seats are numbered 1 to 5. All seats are available when the application starts.

The application does not need customer names, payments, or multiple shows.

## 2. Console menu

```text
MOVIE SEAT BOOKING SYSTEM

1. Display seats
2. Book seat
3. Cancel booking
4. Display booking summary
5. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Display seats | Display every seat number and its status: Available or Booked. |
| Book seat | Read a seat number. Book it only if it is currently available. |
| Cancel booking | Read a seat number. Release it only if it is currently booked. |
| Display booking summary | Display the total number of seats, booked seats, and available seats. |
| Exit | Display `Thank you!` and stop. |

Each booking or cancellation changes only the selected seat.

## 4. Rules and validation

1. Seat numbers must be from 1 to 5.
2. Use `false` for Available and `true` for Booked.
3. A booked seat cannot be booked again.
4. An available seat cannot have its booking cancelled.
5. Cancellation changes a booked seat back to available.
6. Booked seats plus available seats must always equal 5.
7. Reject invalid seat numbers with `Invalid seat number. Choose 1 to 5.`
8. Reject duplicate bookings with `Seat <number> is already booked.`
9. Reject cancellation of an available seat with `Seat <number> is not booked.`
10. Reject menu choices outside 1 to 5 with `Invalid choice. Choose 1 to 5.`

## 5. Suggested object-oriented design

| Class | Responsibility |
| --- | --- |
| `SeatBooking` | Own the seat array; book, cancel, and count seats. |
| `SeatApplication` | Contain `main()`, read inputs, display the menu, and call the booking object. |

Suggested field in `SeatBooking`:

```java
private boolean[] booked = new boolean[5];
```

| Suggested method | Responsibility |
| --- | --- |
| `displaySeats()` | Display every seat and its readable status. |
| `bookSeat(int seatNumber)` | Validate the seat number and availability, then book the seat. |
| `cancelBooking(int seatNumber)` | Validate the seat number and booking status, then release it. |
| `countBookedSeats()` | Count entries whose value is `true`. |
| `countAvailableSeats()` | Return the number of available seats. |

**Hints:** Use `seatNumber - 1` as the index. Booking sets the value to `true`; cancellation sets it to `false`. Count booked seats using a loop, then subtract that count from `booked.length` to obtain available seats.

## 6. Sample console session

```text
Enter your choice: 1
Seat 1: Available
Seat 2: Available
Seat 3: Available
Seat 4: Available
Seat 5: Available

Enter your choice: 2
Enter seat number: 2
Seat 2 booked successfully.

Enter your choice: 2
Enter seat number: 4
Seat 4 booked successfully.

Enter your choice: 1
Seat 1: Available
Seat 2: Booked
Seat 3: Available
Seat 4: Booked
Seat 5: Available

Enter your choice: 4
Total seats: 5
Booked seats: 2
Available seats: 3

Enter your choice: 3
Enter seat number: 2
Booking cancelled for Seat 2.

Enter your choice: 4
Total seats: 5
Booked seats: 1
Available seats: 4

Enter your choice: 5
Thank you!
```

## 7. Sample validation cases

Each row is an independent case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| All seats available | Book seat `6` | `Invalid seat number. Choose 1 to 5.` |
| Seat 2 booked | Book seat `2` | `Seat 2 is already booked.` |
| Seat 1 available | Cancel seat `1` | `Seat 1 is not booked.` |
| All five seats booked | Display summary | Total seats `5`; booked seats `5`; available seats `0`. |
| Any state | Cancel seat `0` | `Invalid seat number. Choose 1 to 5.` |

## 8. Completion checklist

- Use a boolean array with five seats.
- Convert boolean values into readable status messages.
- Prevent booking the same seat twice.
- Prevent cancellation of an available seat.
- Ensure cancellation makes the seat available again.
- Keep the summary consistent with the array.

**Skills practised:** boolean arrays, state changes, index conversion, conditional updates, and counting.

