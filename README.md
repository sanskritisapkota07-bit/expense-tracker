# expense-tracker
A simple expenses-tracking application for recording categorized expenses , validating entries, calculating monthly totals, and generating spending summaries.
expenses = []


def add_expense():
    print("\n--- Add Expense ---")

    category = input("Enter category: ")
    description = input("Enter description: ")

    try:
        amount = float(input("Enter amount: €"))

        if amount <= 0:
            print("Amount must be greater than 0.")
            return

    except ValueError:
        print("Please enter a valid number.")
        return

    expense = {
        "category": category,
        "description": description,
        "amount": amount
    }

    expenses.append(expense)

    print("Expense added successfully!")


def show_expenses():
    print("\n--- Your Expenses ---")

    if not expenses:
        print("No expenses recorded.")
        return

    for i, expense in enumerate(expenses, start=1):
        print(
            f"{i}. {expense['category']} - "
            f"{expense['description']} - "
            f"€{expense['amount']:.2f}"
        )


def show_total():
    total = sum(expense["amount"] for expense in expenses)

    print(f"\nTotal spending: €{total:.2f}")


def main():
    while True:
        print("\n===== Expense Tracker =====")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Show Total")
        print("4. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            add_expense()

        elif choice == "2":
            show_expenses()

        elif choice == "3":
            show_total()

        elif choice == "4":
            print("Goodbye!")
            break

        else:
            print("Invalid choice. Please try again.")


main()
