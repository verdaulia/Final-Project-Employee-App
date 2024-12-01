import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class Employee {
    String name;
    String division;
    double salary;

    public Employee(String name, String division, double salary) {
        this.name = name;
        this.division = division;
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Division: " + division + ", Salary: $" + salary;
    }
}

class EmployeeManager {
    ArrayList<Employee> employees;

    public EmployeeManager() {
        employees = new ArrayList<>();
    }

    public void addEmployee(String name, String division, double salary) {
        employees.add(new Employee(name, division, salary));
    }

    private void selectionSortByName() {
        int n = employees.size();
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (employees.get(j).name.compareTo(employees.get(minIndex).name) < 0) {
                    minIndex = j;
                }
            }
            Collections.swap(employees, i, minIndex);
        }
    }

    private void selectionSortByDivision() {
        int n = employees.size();
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (employees.get(j).division.compareTo(employees.get(minIndex).division) < 0) {
                    minIndex = j;
                }
            }
            Collections.swap(employees, i, minIndex);
        }
    }

    private void bubbleSortBySalary(boolean ascending) {
        int n = employees.size();
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if ((ascending && employees.get(j).salary > employees.get(j + 1).salary) ||
                        (!ascending && employees.get(j).salary < employees.get(j + 1).salary)) {
                    Collections.swap(employees, j, j + 1);
                }
            }
        }
    }

    public void sortByChoice(int choice, boolean ascending) {
        switch (choice) {
            case 1:
                selectionSortByName();
                System.out.println("Sorting completed based on Name (alphabetical order).");
                break;
            case 2:
                selectionSortByDivision();
                System.out.println("Sorting completed based on Division (alphabetical order).");
                break;
            case 3:
                if (ascending) {
                    bubbleSortBySalary(true);
                    System.out.println("Sorting completed based on Salary (Low to High).");
                } else {
                    bubbleSortBySalary(false);
                    System.out.println("Sorting completed based on Salary (High to Low).");
                }
                break;
            default:
                System.out.println("Invalid choice. Sorting not applied.");
        }
    }

    public void displayEmployees() {
        for (Employee emp : employees) {
            System.out.println(emp);
        }
    }
}

public class EmployeeApp {
    public static void main(String[] args) {
        EmployeeManager manager = new EmployeeManager();
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter employee data. Type 'exit' to stop.");

        while (true) {
            System.out.print("Enter employee name (or type 'exit' to finish): ");
            String name = sc.nextLine();
            if (name.equalsIgnoreCase("exit")) {
                break;
            }

            System.out.print("Enter division: ");
            String division = sc.nextLine();

            System.out.print("Enter salary: ");
            double salary = Double.parseDouble(sc.nextLine());

            manager.addEmployee(name, division, salary);
        }

        while (true) {
            System.out.println("\nChoose sorting method:");
            System.out.println("1. Sort by Name");
            System.out.println("2. Sort by Division");
            System.out.println("3. Sort by Salary");
            System.out.println("4. Exit");
            System.out.print("Enter your choice (1/2/3/4): ");
            int choice = Integer.parseInt(sc.nextLine());

            if (choice == 4) {
                System.out.println("Exiting program.");
                break;
            }

            if (choice == 3) {
                System.out.println("Choose salary sorting order:");
                System.out.println("1. Ascending (Low to High)");
                System.out.println("2. Descending (High to Low)");
                System.out.print("Enter your choice (1/2): ");
                int salaryOrder = Integer.parseInt(sc.nextLine());
                boolean ascending = (salaryOrder == 1);
                manager.sortByChoice(choice, ascending);
            } else {
                manager.sortByChoice(choice, true);
            }

            System.out.println("\nEmployees after sorting:");
            manager.displayEmployees();
        }

        sc.close();
    }
}
