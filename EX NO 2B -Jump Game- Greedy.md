
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
