# Developer Performance Calculator

This project is a simple web-based calculator designed to measure developer performance based on tickets completed, average T-shirt size (difficulty), time taken, and bugs found. The performance score is calculated by comparing the time taken against the expected time for the tasks and applying deductions for bugs.

## Features

- **Calculate performance score** based on the number of tickets completed, the complexity of the tasks (T-shirt size), time taken, and bugs found.
- Visual feedback on performance with a score percentage.

---

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [Performance Calculation Logic](#performance-calculation-logic)
   - [Expected Time Calculation](#expected-time-calculation)
   - [Performance Score Calculation](#performance-score-calculation)
   - [Bug Deduction](#bug-deduction)
4. [Reference Tables](#reference-tables)
5. [Example Scenarios](#example-scenarios)

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/developer-performance-calculator.git
   ```
2. Open the `index.html` file in your browser.

---

## Usage

1. Open the `index.html` file.
2. Enter the number of tickets completed.
3. Select the average T-shirt size that represents the complexity of the tasks.
4. Enter the time taken in hours.
5. Enter the number of bugs found.
6. Click the "Calculate Performance" button to view the performance score.

---

## Performance Calculation Logic

### Expected Time Calculation

The expected time for task completion is based on the **T-shirt Size** and the number of tickets completed. T-shirt sizes range from 1 to 10, with higher values representing more complex tasks.

### Formula:

```plaintext
Expected Time = Expected Time for T-shirt Size × Number of Tickets
```

For example:

- T-shirt size 1 = 2 hours per ticket.
- If 2 tickets are completed at T-shirt size 2, the expected time is:
  - `2 × 4 hours = 8 hours`.

### Performance Score Calculation

The performance score starts at 100% and is reduced if the time taken exceeds the expected time or if bugs are found.

1. **Time Deduction**: If the time taken exceeds the expected time, a deduction is made:
   ```plaintext
   Time Deduction = (Excess Time / Expected Time) × 100
   ```
2. **Bug Deduction**: A deduction is made based on the number of bugs found and the T-shirt size.

   ```plaintext
   Bug Deduction = (Bugs / Tickets) × Bug Weight
   ```

3. **Final Performance Score**:
   ```plaintext
   Performance Score = 100 - Time Deduction - Bug Deduction
   ```
   The score is always clamped to a minimum of 0%.

---

## Reference Tables

### T-Shirt Size Table

| T-Shirt Size | Description     | Expected Time (Hours) | Bug Weight |
| ------------ | --------------- | --------------------- | ---------- |
| 1            | 1 (2 Hours)     | 2                     | 100        |
| 2            | 2 (4 Hours)     | 4                     | 100        |
| 3            | 3 (8 Hours)     | 8                     | 80         |
| 4            | 4 (16 Hours)    | 16                    | 70         |
| 5            | 5 (32 Hours)    | 32                    | 60         |
| 6            | 6 (64 Hours)    | 64                    | 50         |
| 7            | 7 (128 Hours)   | 128                   | 40         |
| 8            | 8 (256 Hours)   | 256                   | 30         |
| 9            | 9 (512 Hours)   | 512                   | 20         |
| 10           | 10 (1024 Hours) | 1024                  | 10         |

---

### Bug Deduction Table

| Number of Bugs | Description           | Bug Deduction (Based on T-Shirt Size) |
| -------------- | --------------------- | ------------------------------------- |
| 0              | No bugs found         | 0                                     |
| 1              | Minor issues found    | Varies based on T-Shirt Size          |
| 2              | Moderate issues found | Varies based on T-Shirt Size          |
| 3              | Several issues found  | Varies based on T-Shirt Size          |
| 4              | Major issues found    | Varies based on T-Shirt Size          |
| 5              | Critical issues found | Varies based on T-Shirt Size          |

---

### Time Taken Reference Table

| Time Taken (Hours) | Description                         | Expected Time Comparison |
| ------------------ | ----------------------------------- | ------------------------ |
| 0                  | No time taken                       | Less than expected       |
| 1                  | Minimal time taken                  | Less than expected       |
| 2                  | Exactly expected time               | Matches expected time    |
| 3                  | Slightly exceeds expected time      | Exceeds expected time    |
| 4                  | Moderately exceeds expected time    | Exceeds expected time    |
| 5                  | Significantly exceeds expected time | Exceeds expected time    |
| 6                  | Much longer than expected           | Exceeds expected time    |
| 8                  | Double the expected time            | Exceeds expected time    |
| 10                 | Well over expected time             | Exceeds expected time    |
| 12                 | Considerably over expected time     | Exceeds expected time    |

---

## Example Scenarios

Here are some example scenarios showing how the performance score is calculated:

| Number of Tickets | T-Shirt Size | Time Taken (Hours) | Number of Bugs | Expected Time (Hours) | Excess Time (Hours) | Bug Deduction | Performance Score (%) |
| ----------------- | ------------ | ------------------ | -------------- | --------------------- | ------------------- | ------------- | --------------------- |
| 1                 | 1            | 3                  | 0              | 2                     | 1                   | 0             | 50.00                 |
| 2                 | 2            | 6                  | 1              | 8                     | 0                   | 100           | 87.50                 |
| 3                 | 3            | 12                 | 0              | 24                    | 0                   | 0             | 100.00                |
| 5                 | 4            | 25                 | 2              | 80                    | 25                  | 35            | 66.25                 |
| 4                 | 5            | 45                 | 1              | 128                   | 0                   | 50            | 93.75                 |
| 1                 | 6            | 70                 | 0              | 128                   | 0                   | 0             | 100.00                |
| 2                 | 7            | 250                | 4              | 256                   | 0                   | 120           | 80.00                 |
| 3                 | 8            | 500                | 3              | 768                   | 0                   | 90            | 96.25                 |
| 2                 | 9            | 600                | 5              | 1024                  | 0                   | 100           | 94.00                 |
| 1                 | 10           | 1100               | 0              | 1024                  | 76                  | 0             | 92.56                 |

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
