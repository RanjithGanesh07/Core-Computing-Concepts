# Experiment 2(b): Program to Implement Priority Scheduling

## Aim

To write and execute a C program to implement the **Priority CPU Scheduling Algorithm** and calculate the **Waiting Time (WT)** and **Turnaround Time (TAT)** for each process along with their average values.

---

## Algorithm

1. **Start the program.**
2. Read the number of processes `n`.
3. Read the burst time and priority of each process and assign process IDs.
4. Sort the processes in ascending order of priority.

   * A **smaller priority number indicates higher priority**.
5. Assign the waiting time of the first process as `0`.
6. Calculate the waiting time for the remaining processes using:

   * `WT[i] = WT[i-1] + BT[i-1]`
7. Calculate the turnaround time for each process using:

   * `TAT[i] = WT[i] + BT[i]`
8. Display the **Process ID, Priority, Burst Time, Waiting Time, and Turnaround Time**.
9. Calculate the **Average Waiting Time** and **Average Turnaround Time**.
10. **Stop the program.**

---

## Procedure for Executing the C Program

1. Open any C compiler such as **Code::Blocks**.
2. Create a new C source file.
3. Type or paste the Priority Scheduling program.
4. Save the file with the `.c` extension.
5. Compile the program.
6. Execute the program.
7. Enter the number of processes, burst times, and priorities.
8. Observe the **execution order, waiting time, turnaround time, and average values** displayed.

---

## Program

```c id="9a8x4r"
#include <stdio.h>

int main() {
    int n, i, j, temp;
    int bt[20], wt[20], tat[20], p[20], pr[20];
    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        p[i] = i + 1;

        printf("Enter Burst Time for P%d: ", i + 1);
        scanf("%d", &bt[i]);

        printf("Enter Priority for P%d: ", i + 1);
        scanf("%d", &pr[i]);
    }

    for (i = 0; i < n - 1; i++) {
        for (j = i + 1; j < n; j++) {
            if (pr[i] > pr[j]) {
                temp = pr[i];
                pr[i] = pr[j];
                pr[j] = temp;

                temp = bt[i];
                bt[i] = bt[j];
                bt[j] = temp;

                temp = p[i];
                p[i] = p[j];
                p[j] = temp;
            }
        }
    }

    wt[0] = 0;

    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    for (i = 0; i < n; i++) {
        tat[i] = wt[i] + bt[i];
    }

    printf("\nProcess\tPriority\tBT\tWT\tTAT\n");

    for (i = 0; i < n; i++) {
        printf("P%d\t%d\t\t%d\t%d\t%d\n",
               p[i], pr[i], bt[i], wt[i], tat[i]);

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

<img width="1830" height="768" alt="image" src="https://github.com/user-attachments/assets/70cf4385-b4ed-4820-8e41-c5ca544f7f58" />

---

## Result

Thus, the C program to implement the **Priority CPU Scheduling Algorithm** was successfully executed. The **Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time** were calculated and displayed successfully.
