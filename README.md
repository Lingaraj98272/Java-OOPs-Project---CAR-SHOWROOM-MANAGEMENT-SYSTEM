Part 1: The Theory
This project is a Console-Based Object-Oriented Application in Java. It is designed to be beginner-friendly by intentionally skipping complex OOP rules like Encapsulation and Abstraction.

1. Core Concepts Used:
Classes and Objects: We use classes (Showroom, Employees, Cars) as blueprints to create objects that hold data.

Arrays of Objects: Instead of a database, we use arrays (e.g., Showroom[] myShowrooms = new Showroom[5];) to store the data in memory while the program runs.

Constructors: We use default constructors to initialize our objects.

Scanner Class: Used to take input from the user via the keyboard.

2. Design Choices (Per Your Request):
No Access Modifiers (Default Scope):

Theory: Usually, we use private for data and public for methods. Here, we use no keywords. This means all variables and methods are "package-private" (accessible by any class in the same folder).

Why: It simplifies the code syntax. You don't need to type public or private everywhere.

No Encapsulation:

Theory: Encapsulation means hiding data and accessing it via getters and setters. Here, we access variables directly (e.g., s.showroom_name = ...).

Why: This makes the data flow very visible and direct, which is great for understanding how data moves in a small program.

No Abstraction/Interfaces:

Theory: Abstraction hides implementation details (using interface or abstract class). Here, every method (get_details, set_details) is fully written out in every class.

Why: You can see exactly what every method does without jumping between files or looking at abstract definitions.





Part 2: The Code
You can copy this code into your Java IDE (like IntelliJ, Eclipse, or VS Code). Create three separate files for the classes (Showroom.java, Employees.java, Cars.java) and one for the main logic (Main.java).

File 1: Showroom.java
Java
import java.util.Scanner;

class Showroom {
    String showroom_name;
    String showroom_address;
    int total_employees;
    int total_cars_in_stock = 0;
    String manager_name;

    // Method to get details (Input)
    void set_details() {
        Scanner sc = new Scanner(System.in);
        System.out.println("======================= *** ENTER SHOWROOM DETAILS *** =======================");
        System.out.println();
        System.out.print("SHOWROOM NAME: ");
        showroom_name = sc.nextLine();
        System.out.print("SHOWROOM ADDRESS: ");
        showroom_address = sc.nextLine();
        System.out.print("MANAGER NAME: ");
        manager_name = sc.nextLine();
        System.out.print("TOTAL NO OF EMPLOYEES: ");
        total_employees = sc.nextInt();
        System.out.print("TOTAL CARS IN STOCK: ");
        total_cars_in_stock = sc.nextInt();
    }

    // Method to show details (Output)
    void get_details() {
        System.out.println("Showroom Name: " + showroom_name);
        System.out.println("Showroom Address: " + showroom_address);
        System.out.println("Manager Name: " + manager_name);
        System.out.println("Total Employees: " + total_employees);
        System.out.println("Total Cars In Stock: " + total_cars_in_stock);
    }
}
File 2: Employees.java
Java
import java.util.Scanner;
import java.util.UUID;

class Employees {
    String emp_id;
    String emp_name;
    int emp_age;
    String emp_department;

    // Method to get details (Input)
    void set_details() {
        Scanner sc = new Scanner(System.in);
        UUID uuid = UUID.randomUUID();
        emp_id = String.valueOf(uuid); // Auto-generating a unique ID
        System.out.println("======================= *** ENTER EMPLOYEE DETAILS *** =======================");
        System.out.println();
        System.out.print("EMPLOYEE NAME: ");
        emp_name = sc.nextLine();
        System.out.print("EMPLOYEE AGE: ");
        emp_age = sc.nextInt();
        sc.nextLine(); // Consume newline left-over
        System.out.print("EMPLOYEE DEPARTMENT: ");
        emp_department = sc.nextLine();
        System.out.println("SHOWROOM NAME: "); // Asking which showroom they belong to (optional logic)
        String showroom_name = sc.nextLine(); 
    }

    // Method to show details (Output)
    void get_details() {
        System.out.println("ID: " + emp_id);
        System.out.println("Name: " + emp_name);
        System.out.println("Age: " + emp_age);
        System.out.println("Department: " + emp_department);
    }
}
File 3: Cars.java
Java
import java.util.Scanner;

class Cars {
    String car_name;
    String car_color;
    String car_fuel_type;
    double car_price;
    String car_type;
    String car_transmission;

    // Method to get details (Input)
    void set_details() {
        Scanner sc = new Scanner(System.in);
        System.out.println("======================= *** ENTER CAR DETAILS *** =======================");
        System.out.println();
        System.out.print("CAR NAME: ");
        car_name = sc.nextLine();
        System.out.print("CAR COLOR: ");
        car_color = sc.nextLine();
        System.out.print("CAR FUEL TYPE(PETROL/DIESEL): ");
        car_fuel_type = sc.nextLine();
        System.out.print("CAR PRICE: ");
        car_price = sc.nextDouble();
        sc.nextLine(); // Consume newline
        System.out.print("CAR TYPE(SEDAN/SUV/HATCHBACK): ");
        car_type = sc.nextLine();
        System.out.print("TRANSMISSION TYPE(AUTOMATIC/MANUAL): ");
        car_transmission = sc.nextLine();
    }

    // Method to show details (Output)
    void get_details() {
        System.out.println("NAME: " + car_name);
        System.out.println("COLOR: " + car_color);
        System.out.println("FUEL TYPE: " + car_fuel_type);
        System.out.println("PRICE: " + car_price);
        System.out.println("CAR TYPE: " + car_type);
        System.out.println("TRANSMISSION: " + car_transmission);
    }
}
File 4: Main.java (The Runner Class)
Java
import java.util.Scanner;

class Main {
    // Main method creation
    static void main_menu() {
        System.out.println();
        System.out.println("======================= *** WELCOME TO SHOWROOM MANAGEMENT SYSTEM *** =======================");
        System.out.println();
        System.out.println("=================== *** ENTER YOUR CHOICE *** ===================");
        System.out.println();
        System.out.println("1].ADD SHOWROOMS \t\t\t 2].ADD EMPLOYEES \t\t\t 3].ADD CARS");
        System.out.println();
        System.out.println("4].GET SHOWROOMS \t\t\t 5].GET EMPLOYEES \t\t\t 6].GET CARS");
        System.out.println();
        System.out.println("======================= *** ENTER 0 TO EXIT *** =======================");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Showroom[] showroom = new Showroom[5];
        Employees[] employee = new Employees[5];
        Cars[] car = new Cars[5];
        int car_counter = 0;
        int showroom_counter = 0;
        int employees_counter = 0;
        int choice = 100;

        while (choice != 0) {
            main_menu();
            choice = sc.nextInt();

            while (choice != 9 && choice != 0) {
                switch (choice) {
                    case 1:
                        showroom[showroom_counter] = new Showroom();
                        showroom[showroom_counter].set_details();
                        showroom_counter++;
                        System.out.println();
                        System.out.println("1].ADD NEW SHOWROOM");
                        System.out.println("9].GO BACK TO MAIN MENU");
                        choice = sc.nextInt();
                        break;
                    case 2:
                        employee[employees_counter] = new Employees();
                        employee[employees_counter].set_details();
                        employees_counter++;
                        System.out.println();
                        System.out.println("1].ADD NEW EMPLOYEE");
                        System.out.println("9].GO BACK TO MAIN MENU");
                        choice = sc.nextInt();
                        break;
                    case 3:
                        car[car_counter] = new Cars();
                        car[car_counter].set_details();
                        car_counter++;
                        System.out.println();
                        System.out.println("1].ADD NEW CAR");
                        System.out.println("9].GO BACK TO MAIN MENU");
                        choice = sc.nextInt();
                        break;
                    case 4:
                        for (int i = 0; i < showroom_counter; i++) {
                            showroom[i].get_details();
                            System.out.println();
                            System.out.println();
                        }
                        System.out.println();
                        System.out.println("9].GO BACK TO MAIN MENU");
                        System.out.println("0].EXIT");
                        choice = sc.nextInt();
                        break;
                    case 5:
                        for (int i = 0; i < employees_counter; i++) {
                            employee[i].get_details();
                            System.out.println();
                            System.out.println();
                        }
                        System.out.println();
                        System.out.println("9].GO BACK TO MAIN MENU");
                        System.out.println("0].EXIT");
                        choice = sc.nextInt();
                        break;
                    case 6:
                        for (int i = 0; i < car_counter; i++) {
                            car[i].get_details();
                            System.out.println();
                            System.out.println();
                        }
                        System.out.println();
                        System.out.println("9].GO BACK TO MAIN MENU");
                        System.out.println("0].EXIT");
                        choice = sc.nextInt();
                        break;
                    default:
                        System.out.println("ENTER VALID CHOICE: ");
                        break;
                }
            }
        }
    }
}
