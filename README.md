# ATMmachine
class ATM:
    def _init_(self, balance=0):
        self.balance = balance

    def check_balance(self):
        return self.balance

    def deposit(self, amount):
        if amount <= 0:
            return "Deposit amount must be positive."
        self.balance += amount
        return f"Successfully deposited ${amount}. Current balance: ${self.balance}"

    def withdraw(self, amount):
        if amount <= 0:
            return "Withdrawal amount must be positive."
        if amount > self.balance:
            return "Insufficient funds."
        self.balance -= amount
        return f"Successfully withdrew ${amount}. Current balance: ${self.balance}"

def main():
    atm = ATM()
    while True:
        print("\nATM Menu:")
        print("1. Check Balance")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Exit")
        
        try:
            choice = int(input("Enter your choice: "))
        except ValueError:
            print("Invalid input. Please enter a number between 1 and 4.")
            continue

        if choice == 1:
            print(f"Your current balance is: ${atm.check_balance()}")
        elif choice == 2:
            try:
                amount = float(input("Enter amount to deposit: "))
                print(atm.deposit(amount))
            except ValueError:
                print("Invalid input. Please enter a valid amount.")
        elif choice == 3:
            try:
                amount = float(input("Enter amount to withdraw: "))
                print(atm.withdraw(amount))
            except ValueError:
                print("Invalid input. Please enter a valid amount.")
        elif choice == 4:
            print("Exiting ATM. Have a great day!")
            break
        else:
            print("Invalid choice. Please choose a number between 1 and 4.")

if __name__ == "__main__":
    main()
