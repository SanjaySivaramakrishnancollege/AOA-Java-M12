
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
