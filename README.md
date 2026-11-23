# Student-Marks-and-Grading-System-developed-using-Java.

Conditional Statements, Looping Constructs, Static Methods, Method Overloading and Scope Rules in Java
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
<img width="1365" height="618" alt="Screenshot 2026-11-23 015332" src="https://github.com/user-attachments/assets/e838d5e0-554e-49d2-91b0-0accfeabcec6" />
The program successfully demonstrates how loops and conditional statements can work together. It also prevents invalid marks from being included in the calculation.

Static Methods and Method Overloading
For Question 2, I improved the program by introducing static methods. The purpose of using methods is to separate specific tasks from the main program, making the code easier to understand, manage and reuse.
First, I created a static method called calculateGrade(double average). This method receives the student's average and uses conditional statements to determine whether the student receives an A, B, C or F.
I also created another method with the same name but different parameters. This second method accepts the total marks and the number of subjects. It calculates the average internally and then returns the appropriate grade.
This process is known as method overloading. It allows methods to have the same name while performing related tasks using different parameter lists (Oracle, n.d.-b).
Java implementation:
public static String calculateGrade(double average) {
    if (average >= 90) {
        return "A";
    } else if (average >= 80) {
        return "B";
    } else if (average >= 70) {
        return "C";
    } else {
        return "F";
    }
}

public static String calculateGrade(double total, int subjects) {
    double average = total / subjects;
    return calculateGrade(average);
}
<img width="1365" height="564" alt="Screenshot 2026-11-23 015901" src="https://github.com/user-attachments/assets/f78788f1-eb62-4747-9bce-f1c519ad708f" />

Both methods can be called without creating an object because they are declared as static methods. This makes the grading process reusable in different parts of the application.
Scope Rules and Displaying Student Performance
In Question 3, I combined the concepts from the previous questions to develop a more complete student grading application.
The program collects and validates five subject marks, calculates the total and average, and determines the student's grade using the calculateGrade() method.
I also introduced a switch statement to display a description of the student's performance. For example, a student with an A receives the description "Excellent performance", while a student with an F receives "Unsatisfactory performance".
Another important concept applied here is variable scope. I declared variables such as total, average and grade inside the main() method because they are only required during the execution of that method. The average variable inside the overloaded method is also local to that method. This prevents unnecessary access to variables outside their intended areas.
Java implementation: The complete program is presented below.
import java.util.Scanner;

public class StudentMarks {

    public static String calculateGrade(double average) {
        if (average >= 90) {
            return "A";
        } else if (average >= 80) {
            return "B";
        } else if (average >= 70) {
            return "C";
        } else {
            return "F";
        }
    }

    public static String calculateGrade(double total, int subjects) {
        double average = total / subjects;
        return calculateGrade(average);
    }

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        double[] marks = new double[5];
        double total = 0;
        double average;
        String grade;

        for (int i = 0; i < 5; i++) {
            System.out.print("Enter mark for subject " + (i + 1) + ": ");
            marks[i] = input.nextDouble();

            if (marks[i] < 0 || marks[i] > 100) {
                System.out.println(
                    "Invalid input - Marks must be between 0 and 100 (inclusive)"
                );
                input.close();
                return;
            }
        }

        for (int i = 0; i < 5; i++) {
            total += marks[i];
        }

        average = total / 5;
        grade = calculateGrade(average);

        System.out.println("\n===== STUDENT PERFORMANCE REPORT =====");
        System.out.println("Total Marks: " + total + " / 500");
        System.out.printf("Average Marks: %.2f%%%n", average);
        System.out.println("Final Grade: " + grade);

        switch (grade) {
            case "A":
                System.out.println("Performance: Excellent performance");
                break;
            case "B":
                System.out.println("Performance: Very good performance");
                break;
            case "C":
                System.out.println("Performance: Satisfactory performance");
                break;
            default:
                System.out.println("Performance: Unsatisfactory performance");
        }

        input.close();
    }
}
<img width="1359" height="572" alt="Screenshot 2026-11-23 020034" src="https://github.com/user-attachments/assets/f3cc3fe4-adde-4901-bdf0-be977d77ddfd" />

Working on this assignment has helped me understand how different Java programming concepts can be combined to solve a practical problem. I was able to use loops to collect and calculate students' marks, conditional statements to validate inputs and determine grades, and methods to make the program more organised.
I also gained a better understanding of method overloading and variable scope. One thing I found important is that a program should not only produce the correct result but should also be structured in a way that makes it easy to understand and maintain.
Overall, this assignment has improved my understanding of how Java handles decision-making, repetition and reusable methods when developing simple applications.
