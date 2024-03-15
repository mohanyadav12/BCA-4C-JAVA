# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-
import java.util.Scanner;

class Employee {
    private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    // Constructor to initialize the employee details
    public Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate Gross Salary
    private void calculateGrossSalary() {
        double hra = 0.25 * basicSalary;
        double da = 0.4 * basicSalary;
        this.grossSalary = basicSalary + hra + da;
    }

    // Getter for grossSalary
    public double getGrossSalary() {
        return grossSalary;
    }

    // Getter for nameOfEmp
    public String getNameOfEmp() {
        return nameOfEmp;
    }

    // Getter for empId
    public int getEmpId() {
        return empId;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input number of employees
        System.out.print("Enter the number of employees: ");
        int n = scanner.nextInt();

        // Create an array of Employee objects
        Employee[] employees = new Employee[n];

        // Input details of each employee
        for (int i = 0; i < n; i++) {
            System.out.println("Enter details for employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.next();
            System.out.print("Employee ID: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            employees[i] = new Employee(name, empId, basicSalary);
        }

        // Display employees whose name starts with a consonant
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (Employee emp : employees) {
            if (!isVowel(emp.getNameOfEmp().charAt(0))) {
                System.out.println("Name: " + emp.getNameOfEmp() + ", Gross Salary: " + emp.getGrossSalary());
            }
        }

        // Display employees whose Emp-Id is between 101 and 150
        System.out.println("\nEmployees whose Emp-Id is between 101 and 150:");
        for (Employee emp : employees) {
            if (emp.getEmpId() >= 101 && emp.getEmpId() <= 150) {
                System.out.println("Emp ID: " + emp.getEmpId() + ", Gross Salary: " + emp.getGrossSalary());
            }
        }

        // Count the total number of Employees whose GrossSalary is less than 35000/-
        int count = 0;
        for (Employee emp : employees) {
            if (emp.getGrossSalary() < 35000) {
                count++;
            }
        }
        System.out.println("\nTotal number of employees whose Gross Salary is less than 35000/-: " + count);
    }

    // Function to check if a character is a vowel
    private static boolean isVowel(char ch) {
        ch = Character.toUpperCase(ch);
        return ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U';
    }
}
