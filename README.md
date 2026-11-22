# public class BankAccount {

    // 1. Private Attributes
    private String name;
    private String number;
    private String code;
    private double balance;

    // 2. Constructor
    public BankAccount(String name, String number, String code) {

        this.name = name;
        this.number = number;
        this.code = code;
        this.balance = 0;
    }

    // 3. Getters and Setters

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getNumber() {
        return number;
    }

    public void setNumber(String number) {
        this.number = number;
    }

    public String getCode() {
        return code;
    }

    public void setCode(String code) {
        this.code = code;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        if (balance >= 0) {
            this.balance = balance;
        }
    }

    // 4. Cash In
    public void cashIn(double amount) {

        if (amount > 0) {
            balance += amount;
            System.out.println("Cash In successful!");
        }
        else {
            System.out.println("Invalid amount!");
        }
    }

    // 5. Cash Out
    public void cashOut(double amount) {

        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Cash Out successful!");
        }
        else {
            System.out.println("Insufficient balance!");
        }
    }

    // 6. Check Balance
    public void checkBalance() {

        System.out.println("Balance: " + balance + " DA");
    }

    // 7. Display Information
    public void displayInformation() {

        System.out.println("\n===== ACCOUNT INFORMATION =====");

        System.out.println("Name: " + name);
        System.out.println("Number: " + number);
        System.out.println("Code: " + code);
        System.out.println("Balance: " + balance + " DA");
    }

    // 8. Transfer To
    public void transferTo(BankAccount recipient, double amount) {

        if (recipient != null && recipient != this
                && amount > 0 && amount <= balance) {

            this.balance -= amount;
            recipient.balance += amount;

            System.out.println("Transfer successful!");

        }
        else {
            System.out.println("Transfer failed!");
        }
    }

    // 9. Automatic Transfer
    public void automaticTransfer(BankAccount recipient,
                                  double amount) {

        if (recipient != null && recipient != this
                && amount > 0 && amount <= balance) {

            transferTo(recipient, amount);

            System.out.println("Monthly automatic transfer completed!");

        }
        else {
            System.out.println("Automatic transfer failed!");
        }
    }
}