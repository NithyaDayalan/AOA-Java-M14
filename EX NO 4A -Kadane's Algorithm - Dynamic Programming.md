# EX 4A Kadane's Algorithm - Dynamic Programming. 
## AIM:
To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6

## Algorithm:
1. Read the array of energy values from the user.
2. Use Kadane’s algorithm to find the maximum subarray sum (non-circular case).
3. Use Kadane’s algorithm to find the minimum subarray sum.
4. Compute the wraparound maximum as total sum minus the minimum subarray sum. 
5. Return the larger of the non-circular maximum and wraparound maximum. 

## Program:
```
Developed by: NITHYA D
Register Number: 212223240110 
```
```
import java.util.*;

public class SolarEnergyMaximizer {

    public static int maxCircularEnergy(int[] energy) {
        int totalSum = 0;
        int maxKadane = kadaneMax(energy);  // Non-wrapping case
        int minKadane = kadaneMin(energy);  // Minimum subarray sum

        for (int val : energy) {
            totalSum += val;
        }

        int wraparoundMax = totalSum - minKadane;

        if (wraparoundMax == 0) // All numbers are negative
            return maxKadane;

        return Math.max(maxKadane, wraparoundMax);
    }

    private static int kadaneMax(int[] arr) {
        int maxSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.max(arr[i], current + arr[i]);
            maxSoFar = Math.max(maxSoFar, current);
        }
        return maxSoFar;
    }

    private static int kadaneMin(int[] arr) {
        int minSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.min(arr[i], current + arr[i]);
            minSoFar = Math.min(minSoFar, current);
        }
        return minSoFar;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}
```

## Output:
<img width="535" height="226" alt="image" src="https://github.com/user-attachments/assets/c5daadd5-f348-4886-b4bf-31480f6e4a52" />

## Result:
The program successfully Implemented and the output is verified. 
