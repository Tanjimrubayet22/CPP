#include <iostream>
#include <string>

class BankAccount {
private:
    std::string accountNumber;
    std::string accountHolder;
    double balance;

public:
    BankAccount(const std::string& accNumber, const std::string& accHolder, double initialBalance)
        : accountNumber(accNumber), accountHolder(accHolder), balance(initialBalance) {}

    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            std::cout << "Deposit successful. New balance: " << balance << std::endl;
        } else {
            std::cout << "Invalid deposit amount." << std::endl;
        }
    }

    void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            std::cout << "Withdrawal successful. New balance: " << balance << std::endl;
        } else {
            std::cout << "Insufficient funds or invalid withdrawal amount." << std::endl;
        }
    }

    void displayBalance() {
        std::cout << "Account Holder: " << accountHolder << std::endl;
        std::cout << "Account Number: " << accountNumber << std::endl;
        std::cout << "Balance: " << balance << std::endl;
    }
};

int main() {
    std::string accNumber;
    std::string accHolder;
    double initialBalance;

    std::cout << "Enter account number: ";
    std::cin >> accNumber;

    std::cout << "Enter account holder's name: ";
    std::cin.ignore(); // Clear newline left in the input buffer
    std::getline(std::cin, accHolder);

    std::cout << "Enter initial balance: ";
    std::cin >> initialBalance;

    BankAccount account(accNumber, accHolder, initialBalance);

    int choice;
    double amount;

    do {
        std::cout << "Bank Account Menu:" << std::endl;
        std::cout << "1. Display Balance" << std::endl;
        std::cout << "2. Deposit" << std::endl;
        std::cout << "3. Withdraw" << std::endl;
        std::cout << "4. Exit" << std::endl;
        std::cout << "Enter your choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1:
                account.displayBalance();
                break;
            case 2:
                std::cout << "Enter deposit amount: ";
                std::cin >> amount;
                account.deposit(amount);
                break;
            case 3:
                std::cout << "Enter withdrawal amount: ";
                std::cin >> amount;
                account.withdraw(amount);
                break;
            case 4:
                std::cout << "Exiting program." << std::endl;
                break;
            default:
                std::cout << "Invalid choice. Please select a valid option." << std::endl;
        }
    } while (choice != 4);

    return 0;
}
