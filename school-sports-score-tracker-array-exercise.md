# CDG-HYD-JFS-060

## School Sports Score Tracker Array Exercise

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

A school conducts a points-based sports event for up to five players. Each player receives a final score from 0 to 100.

Create a **School Sports Score Tracker** to record scores, display the results, identify the winners, and list players who qualify for the next round.

Assign player numbers in the order scores are recorded. The highest score wins. If players tie for the highest score, display all of them as joint winners. A player qualifies for the next round with a score of **60 or more**.

## 2. Console menu

```text
SCHOOL SPORTS SCORE TRACKER

1. Record player score
2. Display scores
3. Display winners
4. Display qualified players
5. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Record player score | Read one score and store it at the next unused position. Display the assigned player number. |
| Display scores | Display every recorded player number and score. |
| Display winners | Find the highest recorded score, then display every player with that score. |
| Display qualified players | Display every player whose score is at least 60. If no recorded player qualifies, show `No player qualified. Minimum score: 60.` |
| Exit | Display `Thank you!` and stop. |

Display player numbers in ascending order when showing scores, winners, or qualified players.

## 4. Rules and validation

1. Store a maximum of five player scores.
2. Scores must be integers from 0 to 100, inclusive.
3. Player numbers start at 1; array indexes start at 0.
4. Zero is a valid recorded score.
5. Qualification uses `score >= 60`; a score of exactly 60 qualifies.
6. Display all tied winners; do not stop after finding the first match.
7. Use only recorded entries in searches and displays.
8. When there are no records, Display scores, Display winners, and Display qualified players must show `No scores recorded yet.`
9. Reject a sixth score with `Score register is full. Maximum 5 players allowed.`
10. Reject invalid scores with `Invalid score. Enter a value from 0 to 100.`
11. Reject menu choices outside 1 to 5 with `Invalid choice. Choose 1 to 5.`

## 5. Suggested object-oriented design

| Class | Responsibility |
| --- | --- |
| `ScoreTracker` | Own scores; add records, find the maximum, and display matching players. |
| `SportsApplication` | Contain `main()`, read inputs, display the menu, and call the tracker object. |

Suggested fields in `ScoreTracker`:

```java
private int[] scores = new int[5];
private int count = 0;
```

| Suggested method | Responsibility |
| --- | --- |
| `addScore(int score)` | Validate score and capacity, then store the score and increase `count` on success. |
| `displayScores()` | Display recorded players and scores. |
| `findHighestScore()` | Return the highest recorded score using a loop. |
| `displayWinners()` | Handle the empty state; find the maximum and display every matching player. |
| `displayQualifiedPlayers()` | Display players scoring at least 60, or the appropriate empty/no-qualifier message. |

**Hints:** Add at index `count`. Display player number `index + 1`. Use one loop to find the highest score and a second loop to display all players with that score. Check that records exist before calling `findHighestScore()`. Use a local boolean flag to track whether the qualification loop found any matches.

## 6. Sample console session

```text
Enter your choice: 1
Enter player score: 40
Score recorded for Player 1.

Enter your choice: 1
Enter player score: 80
Score recorded for Player 2.

Enter your choice: 1
Enter player score: 80
Score recorded for Player 3.

Enter your choice: 2
Player 1: 40
Player 2: 80
Player 3: 80

Enter your choice: 3
Highest score: 80
Winning players:
Player 2
Player 3

Enter your choice: 4
Qualified players:
Player 2: 80
Player 3: 80

Enter your choice: 5
Thank you!
```

## 7. Sample validation cases

Each row is an independent case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| No scores recorded | Display winners | `No scores recorded yet.` |
| Two scores recorded | Record score `105` | `Invalid score. Enter a value from 0 to 100.` Player count stays at 2. |
| Five scores recorded | Record another score | `Score register is full. Maximum 5 players allowed.` |
| Player 1 has score 40; Player 2 has score 55 | Display qualified players | `No player qualified. Minimum score: 60.` |
| Player 1 has score 60 | Display qualified players | `Qualified players:`, then `Player 1: 60` |
| Two recorded players each have score 0 | Display winners | Highest score `0`; both players displayed as winners. |

## 8. Completion checklist

- Store scores in a fixed-size array.
- Keep `count` separate from score values.
- Display only recorded players.
- Find winners using loops and include every tied winner.
- Include a score of exactly 60 in the qualified list.
- Handle no records and no qualifying players separately.

**Skills practised:** partially filled arrays, maximum searches, matching values, filtering, tie handling, and boundary validation.

