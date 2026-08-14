
# EX 1C Job Sequencing using Greedy Approach
## DATE: 5/08/2026
## AIM:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.You're given N jobs, each with:

A unique jobId

A deadline (by which it must be completed)

A profit (earned only if completed on or before the deadline)

Each job:

Takes exactly 1 unit of time

Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm

1. Start the program and import the `Scanner` and `Arrays` classes.
2. Read the number of jobs `n` and input each job’s `id`, `deadline`, and `profit`.
3. Sort all jobs in descending order based on profit to prioritize high-profit jobs.
4. Assign jobs to available slots before their deadlines, ensuring only one job per time slot.
5. Count the total scheduled jobs and sum up their profits, then display both values as output.
 

## Program:
```
/*
Program to implement Reverse a String
Developed by: Sanjay Sivaramakrishnan M
Register Number:  212223240151
*/

import java.util.*;

public class JobScheduling {

    static class Job {
        int id, deadline, profit;

        Job(int id, int deadline, int profit) {
            this.id = id;
            this.deadline = deadline;
            this.profit = profit;
        }
    }

    public static int[] jobScheduling(Job[] jobs, int n) {
        // Type Your Code Here.
        Arrays.sort(jobs, (a, b) -> b.profit - a.profit);

    int maxDeadline = 0;
    for (Job job : jobs) {
        if (job.deadline > maxDeadline)
            maxDeadline = job.deadline;
    }

    int[] slot = new int[maxDeadline + 1];
    Arrays.fill(slot, -1);

    int countJobs = 0, jobProfit = 0;

    for (int i = 0; i < n; i++) {
        for (int j = jobs[i].deadline; j > 0; j--) {
            if (slot[j] == -1) {
                slot[j] = jobs[i].id;
                countJobs++;
                jobProfit += jobs[i].profit;
                break;
            }
        }
    }

    return new int[]{countJobs, jobProfit};
        
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Job[] jobs = new Job[n];

        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            int deadline = sc.nextInt();
            int profit = sc.nextInt();
            jobs[i] = new Job(id, deadline, profit);
        }

        int[] result = jobScheduling(jobs, n);
        System.out.println(result[0] + " " + result[1]);
    }
}

```

## Output:
<img width="563" height="403" alt="image" src="https://github.com/user-attachments/assets/b4254006-7acc-4300-92b5-7903a852dda6" />



## Result:
The program successfully implemented and the expected output is verified.
