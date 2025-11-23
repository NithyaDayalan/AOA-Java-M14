# EX 4B Frog Jump - Dynamic Programming.
## AIM:
To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
 Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm:
1. Read the number of stairs n from the user.
2. Handle base cases: if n is 1 return 1, if n is 2 return 2.
3. Initialize a dp array to store the number of ways to reach each step.
4. Use a loop to fill the dp array using the relation dp[i] = dp[i-1] + dp[i-2]. 
5. Print dp[n], which is the total number of ways to reach the top.  

## Program:
```
Developed by: NITHYA D
Register Number: 212223240110
```
```
import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
       
        int n = scanner.nextInt();
        scanner.close();

        System.out.println(countWays(n));
    }

   
    public static int countWays(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;

        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;

        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }
}
```

## Output:
<img width="438" height="179" alt="image" src="https://github.com/user-attachments/assets/616065d1-c7f8-4d91-8e10-6fe4d4f86795" />

## Result:
The program successfully implemented and the expected output is verified.
