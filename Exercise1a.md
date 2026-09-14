# Exercise 1(a): Program to Implement FCFS Scheduling

## Aim

To write and execute a C program to implement the **First Come First Serve (FCFS) CPU Scheduling Algorithm** and calculate the **Waiting Time** and **Turnaround Time** for each process.

---

## Algorithm: FCFS (First Come First Serve) Scheduling

1. **Start.**
2. Read the number of processes `n`.
3. Input the burst time (BT) for each process.
4. Initialize the waiting time of the first process:

   * `WT[0] = 0`
5. Calculate the waiting time for the remaining processes:

   * `WT[i] = WT[i-1] + BT[i-1]` for `i = 1` to `n-1`.
6. Calculate the turnaround time for each process:

   * `TAT[i] = WT[i] + BT[i]`
7. Calculate the average waiting time:

   * `Average WT = (Sum of all WT) / n`
8. Calculate the average turnaround time:

   * `Average TAT = (Sum of all TAT) / n`
9. Display the **Process ID, Burst Time, Waiting Time, and Turnaround Time** for each process.
10. Display the **Average Waiting Time** and **Average Turnaround Time**.
11. **Stop.**

---

## Procedure for Executing the C Program

1. Open a C programming environment such as **GCC, Turbo C, Code::Blocks, or Dev-C++**.
2. Create a new C source file.
3. Type or paste the FCFS scheduling program into the editor.
4. Save the file with the extension `.c`, for example:

   * `fcfs.c`
5. Compile the program and ensure there are no syntax errors.
6. Run the compiled program.
7. Enter the number of processes and their burst times when prompted.
8. Observe the **Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time** displayed on the screen.
9. Verify that the processes are executed in the order of their arrival, following the **FCFS principle**.

---

## Program

```c
#include <stdio.h>

int main() {
    int n, i;
    int bt[20], wt[20], tat[20];
    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        printf("Enter Burst Time for P%d: ", i + 1);
        scanf("%d", &bt[i]);
    }

    wt[0] = 0;

    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    for (i = 0; i < n; i++) {
        tat[i] = wt[i] + bt[i];
    }

    printf("\nProcess\tBT\tWT\tTAT\n");

    for (i = 0; i < n; i++) {
        printf("P%d\t%d\t%d\t%d\n",
               i + 1, bt[i], wt[i], tat[i]);

        avg_wt += wt[i];
        avg_tat += tat[i];
    }

    printf("\nAverage Waiting Time = %.2f", avg_wt / n);
    printf("\nAverage Turnaround Time = %.2f\n", avg_tat / n);

    return 0;
}
```

---

## Output
<img width="1337" height="452" alt="image" src="https://github.com/user-attachments/assets/ab07c5c6-6fcd-41e0-9224-d543751c29a1" />

---

## Result

Thus, the C program to implement the **First Come First Serve (FCFS) CPU Scheduling Algorithm** was executed successfully, and the **Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time** were obtained.
