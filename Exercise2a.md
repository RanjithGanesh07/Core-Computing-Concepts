# Experiment 2(a): Program to Implement Round Robin Scheduling
```
Name: Ranjith Ganesh B.
Reg No: 212223060222
```

## Aim

To write and execute a C program to implement the **Round Robin (RR) CPU Scheduling Algorithm** and calculate the **Waiting Time** and **Turnaround Time** for each process using a given **Time Quantum**.

---

## Algorithm

1. **Start.**
2. Read the number of processes `n`.
3. Input the burst time (BT) for each process.
4. Read the **Time Quantum (TQ)**.
5. Initialize:

   * Remaining Burst Time (RBT) = Burst Time (BT).
   * Waiting Time (WT) = `0` for all processes.
6. Repeat until all processes are completed:

   * Traverse each process.
   * If the remaining burst time is greater than TQ:

     * Execute the process for TQ units.
     * Reduce the remaining burst time by TQ.
     * Increase the current time by TQ.
   * Otherwise:

     * Execute the process for its remaining burst time.
     * Increase the current time accordingly.
     * Calculate:

       * `Turnaround Time (TAT) = Current Time`
       * `Waiting Time (WT) = TAT − BT`
     * Mark the process as completed.
7. Calculate:

   * `Average Waiting Time = (Sum of WT) / n`
   * `Average Turnaround Time = (Sum of TAT) / n`
8. Display the **Process ID, Burst Time, Waiting Time, and Turnaround Time**.
9. Display the **Average Waiting Time** and **Average Turnaround Time**.
10. **Stop.**

---

## Procedure for Executing the C Program

1. Open a C programming environment such as **GCC, Turbo C, Code::Blocks, or Dev-C++**.
2. Create a new C source file.
3. Type or paste the Round Robin Scheduling program into the editor.
4. Save the file with the `.c` extension, for example:

   * `roundrobin.c`
5. Compile the program and ensure there are no syntax errors.
6. Run the program.
7. Enter the number of processes, burst times, and the time quantum.
8. Observe the **Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time** displayed on the screen.
9. Verify that each process is executed in a **cyclic manner** based on the specified time quantum.

---

## Program

```c
#include <stdio.h>

int main() {
    int n, i, time = 0, remain, tq;
    int bt[20], rt[20], wt[20], tat[20];
    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        printf("Enter Burst Time for P%d: ", i + 1);
        scanf("%d", &bt[i]);
        rt[i] = bt[i];
    }

    printf("Enter Time Quantum: ");
    scanf("%d", &tq);

    remain = n;

    while (remain > 0) {
        for (i = 0; i < n; i++) {
            if (rt[i] > 0) {
                if (rt[i] <= tq) {
                    time += rt[i];
                    rt[i] = 0;

                    tat[i] = time;
                    wt[i] = tat[i] - bt[i];

                    remain--;
                } else {
                    time += tq;
                    rt[i] -= tq;
                }
            }
        }
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
<img width="1717" height="618" alt="image" src="https://github.com/user-attachments/assets/bdfedbb8-6bb0-4834-946c-5439d72c0dc3" />

---

## Result

Thus, the C program to implement the **Round Robin CPU Scheduling Algorithm** was executed successfully, and the **Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time** were obtained.
