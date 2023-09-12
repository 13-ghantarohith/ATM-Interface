# ATM-Interface 
import java.util.Scanner;

public class ATM {
    private double balance;
    private String accountNumber;
    private String pin;

    public ATM(String accountNumber, String pin) {
        this.accountNumber = accountNumber;
        this.pin = pin;
        this.balance = 1000.0; // Initial balance (for demonstration purposes)
    }

    public void displayMenu() {
        System.out.println("Welcome to Your ATM");
        System.out.println("1. Check Balance");
        System.out.println("2. Deposit");
        System.out.println("3. Withdraw");
        System.out.println("4. Exit");
        System.out.print("Please select an option: ");
    }

    public void checkBalance() {
        System.out.println("Your balance is: $" + balance);
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("$" + amount + " has been deposited.");
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("$" + amount + " has been withdrawn.");
        } else {
            System.out.println("Invalid withdrawal amount or insufficient funds.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Replace these with actual account information
        String accountNumber = "123456";
        String pin = "1234";

        ATM atm = new ATM(accountNumber, pin);

        boolean authenticated = false;

        while (!authenticated) {
            System.out.print("Enter your account number: ");
            String inputAccountNumber = scanner.nextLine();

            System.out.print("Enter your PIN: ");
            String inputPin = scanner.nextLine();

            if (inputAccountNumber.equals(atm.accountNumber) && inputPin.equals(atm.pin)) {
                authenticated = true;
            } else {
                System.out.println("Authentication failed. Please try again.");
            }
        }

        boolean exit = false;

        while (!exit) {
            atm.displayMenu();

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    atm.checkBalance();
                    break;
                case 2:
                    System.out.print("Enter the deposit amount: $");
                    double depositAmount = scanner.nextDouble();
                    atm.deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter the withdrawal amount: $");
                    double withdrawalAmount = scanner.nextDouble();
                    atm.withdraw(withdrawalAmount);
                    break;
                case 4:
                    exit = true;
                    break;
                default:
                    System.out.println("Invalid choice. Please select a valid option.");
            }
        }

        System.out.println("Thank you for using Your ATM!");
    }
}
