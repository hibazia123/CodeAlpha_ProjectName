#include <iostream>
#include <vector>
#include <string>
#include <ctime>

using namespace std;

class Transaction {
public:
    string type;
    double amount;
    string date;

    Transaction(string t, double a) {
        type = t;
        amount = a;

        time_t now = time(0);
        date = ctime(&now);
    }

    void displayTransaction() {
        cout << "Type: " << type
             << " | Amount: " << amount
             << " | Date: " << date;
    }
};

class Account {
private:
    int accountNumber;
    double balance;
    vector<Transaction> transactions;

public:
    Account(int accNo) {
        accountNumber = accNo;
        balance = 0.0;
    }

    int getAccountNumber() {
        return accountNumber;
    }

    double getBalance() {
        return balance;
    }

    void deposit(double amount) {
        balance += amount;
        transactions.push_back(Transaction("Deposit", amount));
        cout << "Deposit successful!\n";
    }

    bool withdraw(double amount) {
        if (amount > balance) {
            cout << "Insufficient balance!\n";
            return false;
        }
        balance -= amount;
        transactions.push_back(Transaction("Withdrawal", amount));
        cout << "Withdrawal successful!\n";
        return true;
    }

    bool transfer(Account &receiver, double amount) {
        if (withdraw(amount)) {
            receiver.deposit(amount);
            transactions.push_back(Transaction("Transfer Sent", amount));
            receiver.transactions.push_back(Transaction("Transfer Received", amount));
            cout << "Transfer successful!\n";
            return true;
        }
        return false;
    }

    void showTransactions() {
        cout << "\nTransaction History:\n";
        for (auto &t : transactions) {
            t.displayTransaction();
        }
    }

    void showAccountInfo() {
        cout << "\nAccount Number: " << accountNumber
             << "\nBalance: " << balance << endl;
    }
};

class Customer {
private:
    int customerID;
    string name;
    vector<Account> accounts;

public:
    Customer(int id, string n) {
        customerID = id;
        name = n;
    }

    int getCustomerID() {
        return customerID;
    }

    string getName() {
        return name;
    }

    void createAccount(int accNo) {
        accounts.push_back(Account(accNo));
        cout << "Account created successfully!\n";
    }

    Account* getAccount(int accNo) {
        for (auto &acc : accounts) {
            if (acc.getAccountNumber() == accNo) {
                return &acc;
            }
        }
        return nullptr;
    }

    void showCustomerInfo() {
        cout << "\nCustomer ID: " << customerID
             << "\nName: " << name << endl;
    }
};

int main() {
    vector<Customer> customers;
    int choice;

    do {
        cout << "\n===== Banking System =====\n";
        cout << "1. Create Customer\n";
        cout << "2. Create Account\n";
        cout << "3. Deposit\n";
        cout << "4. Withdraw\n";
        cout << "5. Transfer\n";
        cout << "6. Show Transactions\n";
        cout << "7. Show Account Info\n";
        cout << "0. Exit\n";
        cout << "Enter choice: ";
        cin >> choice;

        if (choice == 1) {
            int id;
            string name;
            cout << "Enter Customer ID: ";
            cin >> id;
            cout << "Enter Name: ";
            cin >> name;
            customers.push_back(Customer(id, name));
            cout << "Customer created!\n";
        }

        else if (choice == 2) {
            int id, accNo;
            cout << "Enter Customer ID: ";
            cin >> id;

            for (auto &c : customers) {
                if (c.getCustomerID() == id) {
                    cout << "Enter New Account Number: ";
                    cin >> accNo;
                    c.createAccount(accNo);
                }
            }
        }

        else if (choice == 3) {
            int id, accNo;
            double amount;
            cout << "Enter Customer ID: ";
            cin >> id;

            for (auto &c : customers) {
                if (c.getCustomerID() == id) {
                    cout << "Enter Account Number: ";
                    cin >> accNo;
                    Account* acc = c.getAccount(accNo);
                    if (acc) {
                        cout << "Enter Amount: ";
                        cin >> amount;
                        acc->deposit(amount);
                    }
                }
            }
        }

        else if (choice == 4) {
            int id, accNo;
            double amount;
            cout << "Enter Customer ID: ";
            cin >> id;

            for (auto &c : customers) {
                if (c.getCustomerID() == id) {
                    cout << "Enter Account Number: ";
                    cin >> accNo;
                    Account* acc = c.getAccount(accNo);
                    if (acc) {
                        cout << "Enter Amount: ";
                        cin >> amount;
                        acc->withdraw(amount);
                    }
                }
            }
        }

        else if (choice == 5) {
            int id1, id2, acc1, acc2;
            double amount;

            cout << "Sender Customer ID: ";
            cin >> id1;
            cout << "Receiver Customer ID: ";
            cin >> id2;

            Account *sender = nullptr, *receiver = nullptr;

            for (auto &c : customers) {
                if (c.getCustomerID() == id1) {
                    cout << "Sender Account Number: ";
                    cin >> acc1;
                    sender = c.getAccount(acc1);
                }
                if (c.getCustomerID() == id2) {
                    cout << "Receiver Account Number: ";
                    cin >> acc2;
                    receiver = c.getAccount(acc2);
                }
            }

            if (sender && receiver) {
                cout << "Enter Amount: ";
                cin >> amount;
                sender->transfer(*receiver, amount);
            }
        }

        else if (choice == 6) {
            int id, accNo;
            cout << "Enter Customer ID: ";
            cin >> id;

            for (auto &c : customers) {
                if (c.getCustomerID() == id) {
                    cout << "Enter Account Number: ";
                    cin >> accNo;
                    Account* acc = c.getAccount(accNo);
                    if (acc) {
                        acc->showTransactions();
                    }
                }
            }
        }

        else if (choice == 7) {
            int id, accNo;
            cout << "Enter Customer ID: ";
            cin >> id;

            for (auto &c : customers) {
                if (c.getCustomerID() == id) {
                    cout << "Enter Account Number: ";
                    cin >> accNo;
                    Account* acc = c.getAccount(accNo);
                    if (acc) {
                        acc->showAccountInfo();
                    }
                }
            }
        }

    } while (choice != 0);

    return 0;
}
