# Student-Marks-and-Grading-System-developed-using-Java.
onditional Statements, Looping Constructs, Static Methods, Method Overloading and Scope Rules in Java
Introduction
Java is a programming language that provides different ways of solving problems through instructions and logical operations. Some of these include conditional statements, loops and methods. Conditional statements allow a program to make decisions based on certain conditions, while loops help repeat instructions without having to write the same code several times.
In this assignment, I developed a Java program that accepts marks for five subjects, checks that the marks entered are valid, calculates the total and average, and determines the student's grade. I also applied static methods, method overloading and variable scope to make the program more organised and reusable.
Question 1: Applying Conditional Statements and Looping Constructs
To solve this problem, I used a for loop to collect marks for five subjects. Instead of creating separate input statements for every subject, the loop allows the program to request the marks one after another.
I also used an if statement to validate each mark. Since the accepted range is between 0 and 100, the program checks every input before proceeding. If a student enters a mark below 0 or above 100, the program displays the required error message and terminates immediately.
After validating all five marks, another for loop adds the marks together to calculate the total. The average is then calculated by dividing the total marks by five.
Java implementation: The complete code for Question 1 is presented below.
import java.util.Scanner;

public class StudentMarksQ1 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        double[] marks = new double[5];
        double total = 0;
        double average;

        for (int i = 0; i < 5; i++) {
            System.out.print("Enter mark for subject " + (i + 1) + ": ");
            marks[i] = input.nextDouble();

            if (marks[i] < 0 || marks[i] > 100) {
                System.out.println("Invalid input - Marks must be between 0 and 100 (inclusive)");
                input.close();
                return;
            }
        }

        for (int i = 0; i < 5; i++) {
            total += marks[i];
        }

        average = total / 5;

        System.out.println("\n===== STUDENT RESULTS =====");
        System.out.println("Total Marks: " + total);
        System.out.println("Average Marks: " + average);

        input.close();
    }
}
