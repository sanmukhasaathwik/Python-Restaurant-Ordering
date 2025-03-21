# Python-Restaurant-Ordering
This is a simple restaurant ordering system built using Python with Object-Oriented Programming (OOP) and exception handling. Users can order food from a menu, and the program calculates the total bill.

class Restaurant:
    def __init__(self):
        """Initialize menu and order details."""
        self.menu = {
            'Pizza': 50,
            'Pasta': 60,
            'Burger': 85,
            'Salad': 75,
            'Coffee': 30,
            'Masala Chai': 25,
            'Maggi': 35,
            'Ghee Dosa': 40,
            'Ghee Masala Dosa': 50
        }
        self.order_list = []  # Stores ordered items
        self.order_total = 0  # Stores total bill amount

    def display_menu(self):
        """Display the menu to the user."""
        print("\nWelcome to Python Restaurant \n")
        print("Menu:")
        for item, price in self.menu.items():
            print(f"{item}: ₹{price}")

    def take_order(self):
        """Take customer order with case-insensitive input validation."""
        while True:
            try:
                item_name = input("\nEnter the name of the item you want to order: ").strip().title()

                # Check if item exists in menu
                if item_name not in self.menu:
                    raise ValueError(f"Sorry! '{item_name}' is not available in the menu.")

                # Add item to order
                self.order_total += self.menu[item_name]
                self.order_list.append((item_name, self.menu[item_name]))
                print(f"{item_name} added to your cart.")

            except ValueError as e:
                print(e)  # Display error message
                continue  # Ask again if input is incorrect

            # Ask user if they want to order more
            another_order = input("Do you want to order another item? (yes/no): ").strip().lower()
            if another_order != 'yes':
                break  # Exit loop if user says 'no'

    def generate_bill(self):
        """Display the final bill."""
        print("\nYour Order Summary:")
        for item, price in self.order_list:
            print(f"{item}: ₹{price}")
        print(f"\nTotal Amount to Pay: ₹{self.order_total}")

        print("\nThank you for dining at Python Restaurant! Have a great day!")


# Create an object of the Restaurant class and start the program
restaurant = Restaurant()
restaurant.display_menu()
restaurant.take_order()
restaurant.generate_bill()
