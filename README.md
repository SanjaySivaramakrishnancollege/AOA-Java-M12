
# EX 2A Assign Cookies using Greedy Algorithm. 
## DATE: 28/7/2026
## AIM:
To Write a Java program for the following Constraints.
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximise the number of your content children and output the maximum number.

## Algorithm
1. Start the program and import the `Scanner` and `Arrays` classes.
2. Read the number of children `n` and their greed factors into array `g`.
3. Read the number of cookies `m` and their sizes into array `s`.
4. Sort both arrays and use two pointers to compare greed and cookie size.
5. Count and display the maximum number of children who can be content with the available cookies.


## Program:
```
/*
Program to implement Reverse a String
Developed by: Sanjay Sivaramakrishnan M
Register Number:  212223240151
*/
import java.util.*;

public class AssignCookies {
    
    public static int findContentChildren(int[] g, int[] s) {
        // Type Your Logic Here.
        Arrays.sort(g);
        Arrays.sort(s);
        int i = 0, j = 0, count = 0;
        while (i < g.length && j < s.length) {
            if (s[j] >= g[i]) {
                count++;
                i++;
                j++;
            } else {
                j++;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] g = new int[n];
        for (int i = 0; i < n; i++) g[i] = sc.nextInt();
        int m = sc.nextInt();
        int[] s = new int[m];
        for (int i = 0; i < m; i++) s[i] = sc.nextInt();
        System.out.println(findContentChildren(g, s));
    }
}

```

## Output:
<img width="588" height="319" alt="image" src="https://github.com/user-attachments/assets/ff26a77b-4298-43fd-8321-cdc42c6c947e" />



## Result:
The program successfully print all the numbers from 1 to N. 






# EX 2B Jump Game using Greedy Algorithm.
## DATE: 1/08/2026
## AIM:
To write a Java program to for given constraints.
You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position.

You start from the first element (index 0). 
Write a program to find the minimum number of jumps required to reach the last index of the array.

If it is not possible to reach the end, return -1.
## Algorithm
1. Start the program and import the `Scanner` class to take user input.  
2. Read the size of the array `n` and input the array elements.  
3. Initialize a variable `maxReach` to track the farthest index that can be reached.  
4. Iterate through the array, updating `maxReach` and checking if the current index exceeds it.  
5. If traversal completes without exceeding `maxReach`, print that the last index can be reached; otherwise, print false.

## Program:
```
/*
Program to implement Reverse a String
Developed by: Sanjay Sivaramakrishnan M
Register Number: 212223240151
*/
import java.util.Scanner;

public class JumpGame {

    // Function to check if we can reach the last index
    public static boolean canReachLastIndex(int[] nums) {
        // Type Your Code Here.
        int maxReach = 0;
    for (int i = 0; i < nums.length; i++) {
        if (i > maxReach) return false;
        maxReach = Math.max(maxReach, i + nums[i]);
    }
    return true;
    }

    // Main method for input and calling the function
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Size of array
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt(); // Elements of array
        }

        System.out.println("Can reach last index: " + canReachLastIndex(nums));
    }
}

```

## Output:

<img width="749" height="226" alt="image" src="https://github.com/user-attachments/assets/c9c578f9-918a-4bb3-a4ee-c2d14d22a5e4" />


## Result:
The program successfully implemented and the expected output is verified.




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



# EX 2D Pattern Matching using Naive Approach.
## DATE:8-08-2026

## AIM:
To write a Java program to for given constraints.
Given text string with length n and a pattern with length m, the task is to prints all occurrences of pattern in text.
Note: You may assume that n > m.

Examples: 

Input:  text = "THIS IS A TEST TEXT", pattern = "TEST"
Output: Pattern found at index 10

Input:  text =  "AABAACAADAABAABA", pattern = "AABA"
Output: Pattern found at index 0, Pattern found at index 9, Pattern found at index 12
## Algorithm
1. Start  
2. Read the input string `text` and the `pattern` to be searched.  
3. Find the lengths of both strings:  
   - `n = length of text`  
   - `m = length of pattern`  
4. Loop through the text from index `i = 0` to `i <= n - m`:  
   - For each position `i`, compare every character of the pattern with the corresponding character in the text.  
   - If any character does not match, break out of the inner loop.  
5. If all characters of the pattern match (`j == m`), print the index `i` where the pattern starts in the text.  
6. Continue checking until the end of the text.  
7. End  
 

## Program:
```
/*
Developed by: Sanjay Sivaramakrishnan M
Register Number: 212223240151
*/
import java.util.Scanner;

public class NaivePatternSearch {

    public static void search(String text, String pattern) {
        int n = text.length();
        int m = pattern.length();

        for (int i = 0; i <= n - m; i++) {
            int j;
            for (j = 0; j < m; j++) {
                if (text.charAt(i + j) != pattern.charAt(j)) {
                    break;
                }
            }
            if (j == m) {
                System.out.println("Pattern found at index " + i);
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        //System.out.print("Enter the text: ");
        String text = scanner.nextLine();

        //System.out.print("Enter the pattern: ");
        String pattern = scanner.nextLine();

        search(text, pattern);

        scanner.close();
    }
}

```

## Output:

<img width="1042" height="411" alt="image" src="https://github.com/user-attachments/assets/4fbde6a2-3110-4802-8d7e-116d13020d3d" />


## Result:
The program successfully implemented and the expected output is verified.




# EX 2E Pattern Matching using Manacher's Algorithm.
## DATE:10-08-2026

## AIM:
To write a Java program for the following constraints.
Longest Palindromic Substring
Given a string s, return the longest palindromic substring in s.
using Manacher's Algorithm

## Algorithm
1. Start  
2. Read the input string `s`.  
3. If the string is empty, return an empty result.  
4. Preprocess the string by inserting a special character (e.g., `#`) between each letter and at both ends to handle even-length palindromes uniformly.  
   - Example: `"abba"` → `"#a#b#b#a#"`  
5. Initialize variables:  
   - `p[]` → array to store palindrome radii centered at each position  
   - `center = 0` and `right = 0` → current center and right boundary of the known palindrome  
   - `maxLen = 0` and `centerIndex = 0` → track longest palindrome found so far  
6. For each position `i` in the processed string:  
   - Find the mirror position: `mirror = 2 * center - i`  
   - If `i < right`, set `p[i] = min(right - i, p[mirror])`.  
   - Expand around `i` while characters on both sides match (`t[a] == t[b]`).  
   - Update `p[i]` for every successful expansion.  
7. If `i + p[i] > right`, update `center = i` and `right = i + p[i]`.  
8. If `p[i] > maxLen`, update `maxLen` and `centerIndex`.  
9. Compute the starting index of the palindrome in the original string:  
   - `start = (centerIndex - maxLen) / 2`  
10. Extract and return the substring from `start` to `start + maxLen`.  
11. Print the longest palindromic substring.  
12. End  


## Program:
```
/*
Developed by: Sanjay Sivaramakrishnan M
Register Number: 212223240151
*/
import java.util.Scanner;

public class LongestPalindromeManacher {

    public static String longestPalindrome(String s) {
        if (s == null || s.length() == 0) return "";

        StringBuilder t = new StringBuilder();
        t.append('#');
        for (int i = 0; i < s.length(); i++) {
            t.append(s.charAt(i));
            t.append('#');
        }

        int n = t.length();
        int[] p = new int[n];
        int center = 0, right = 0;
        int maxLen = 0, centerIndex = 0;

        for (int i = 0; i < n; i++) {
            int mirror = 2 * center - i;
            if (i < right) {
                p[i] = Math.min(right - i, p[mirror]);
            }

            int a = i + (1 + p[i]);
            int b = i - (1 + p[i]);
            while (a < n && b >= 0 && t.charAt(a) == t.charAt(b)) {
                p[i]++;
                a++;
                b--;
            }

            if (i + p[i] > right) {
                center = i;
                right = i + p[i];
            }

            if (p[i] > maxLen) {
                maxLen = p[i];
                centerIndex = i;
            }
        }

        int start = (centerIndex - maxLen) / 2;
        return s.substring(start, start + maxLen);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        String result = longestPalindrome(input);
        System.out.println("Longest Palindromic Substring: " + result);
        sc.close();
    }
}

```

## Output:

<img width="1266" height="391" alt="image" src="https://github.com/user-attachments/assets/c9ecddb8-7f68-427c-b22f-0149833458aa" />


## Result:
The program successfully implemented and the expected output is verified.

