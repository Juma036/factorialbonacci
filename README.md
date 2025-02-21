# factorialbonacci
EB3/61592/22   JUMA NEWTON

import java.util.Scanner;

public class FactorialFibonacci {

    // Factorial using Recursion
    public static long factorialRecursive(int n) {
        return (n <= 1) ? 1 : n * factorialRecursive(n - 1);
    }

    // Factorial using Iteration
    public static long factorialIterative(int n) {
        long result = 1;
        for (int i = 2; i <= n; i++) {
            result *= i;
        }
        return result;
    }

    // Fibonacci using Recursion
    public static long fibonacciRecursive(int n) {
        return (n <= 1) ? n : fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
    }

    // Fibonacci using Iteration
    public static long fibonacciIterative(int n) {
        if (n <= 1) return n;
        long a = 0, b = 1, temp;
        for (int i = 2; i <= n; i++) {
            temp = a + b;
            a = b;
            b = temp;
        }
        return b;
    }

    // Measure Execution Time
    public static long measureTime(Runnable function) {
        long start = System.nanoTime();
        function.run();
        return System.nanoTime() - start;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int n = scanner.nextInt();
        scanner.close();

        // Measure Factorial Time
        System.out.println("\nFactorial (" + n + "):");
        long factorialRecTime = measureTime(() -> factorialRecursive(n));
        long factorialItrTime = measureTime(() -> factorialIterative(n));
        System.out.println("Recursive Result: " + factorialRecursive(n));
        System.out.println("Iterative Result: " + factorialIterative(n));
        System.out.println("Recursive Time: " + factorialRecTime + " ns");
        System.out.println("Iterative Time: " + factorialItrTime + " ns");

        // Measure Fibonacci Time
        System.out.println("\nFibonacci (" + n + "):");
        long fibonacciRecTime = measureTime(() -> fibonacciRecursive(n));
        long fibonacciItrTime = measureTime(() -> fibonacciIterative(n));
        System.out.println("Recursive Result: " + fibonacciRecursive(n));
        System.out.println("Iterative Result: " + fibonacciIterative(n));
        System.out.println("Recursive Time: " + fibonacciRecTime + " ns");
        System.out.println("Iterative Time: " + fibonacciItrTime + " ns");
    }
}
