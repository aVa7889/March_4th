# March_4th
#Create an empty list. This list will later store a customer's order in dictionary format, as follows:

menu = {
    "Snacks": {
        "Crickets": .99,
        "Mealworms": .69,
        "Silkworms": .49,
        "Grasshoppers": 1.99
    },
    "Meals": {
        "Mealworm Pasta": 4.49,
        "Grasshopper Taco ": 9.99,
        "Insect Sushi": 7.49,
        "Beetle Larvae Stir-Fry": 6.99,
        "Ant Salad": 6.99,
        "Locust Pizza": {
            "Cheese": 8.99,
            "Pepperoni": 10.99,
            "Vegetarian": 9.99
        },
        "Cricket Burger": {
            "Roasted Cricket": 7.49,
            "Stir-Fry Cricket": 8.49
        },
        "Silkworm Noodle": 7.99
    },
    "Drinks": {
        "Smoothie & Shake": {
            "Cricket Protein Shake": 1.99,
            "Mealworm Smoothie": 2.49,
        },
        "Tea & Juice": {
            "Silkworm Tea": 2.49,
            "Grasshopper Juice": 3.99,
            "Beetle Larvae Tea": 2.49
        },
        "Cocktail": {
            "Ant-infused Cocktail": 2.99
        }
    },
    "Dessert": {
        "Ants on a Log": 10.99,
        "Beetle Larvae Cupcakes": 7.99,
        "Grasshopper Ice Cream": 9.99,
        "Silkworm pudding": 4.99,
        "Wealworm Cookies": 4.49,
        "Cricket Flour Brownies": 3.99
    }
}
menu_dashes = "-" * 70


print("\n" + "************* Welcome to the Bug Bites on Wheels ************** " + "\n")

while True:
    print("Which menu would you like to review? ")
    
    # Create a variable for the menu item number
    i = 1
    # Create a dictionary to store the menu for later retrival
    menu_items = {}

    # Print the options to choose from menu headings
    for key in menu.keys():
        print(f"{i}: {key}")
        # Store the menu category associated with its menu item number 
        menu_items[i] = key
        # Add 1 to the menu item number
        i += 1

    # Customer's input
    menu_selection = input("Please type menu number to review or q to quit: ")

    # Exit the loop if user typed 'q'
    if menu_selection == 'q':
        break
    # Check if the customer's input is a number
    elif menu_selection.isdigit():
        # Check if the customer's input is a valid option
        if int(menu_selection) in menu_items.keys():
        #Save the menu selection to a variable
            menu_selection_name = menu_items[int(menu_selection)]
        # Print out the menu selection name 
            print(f"\nYou selected {menu_selection_name}")

        # Display the heading for the sub-menu
            print(menu_dashes)
            print(f"This is the {menu_selection_name} menu.")
            print(menu_dashes)
            print("Item #  |  Item name                                        |   Price")
            print("--------|---------------------------------------------------|---------")

            # Initialize a menu item counter
            item_counter = 1
            # Create a dictionary to store the sub menu for later retrival
            sub_menu_items = {}
            # Print out the menu options from the menu_selection_name
            for key, value in menu[menu_selection_name].items():
                # Check if the sub menu item is a dictionary to handle differently
                if type(value) is dict:
                    # Iterate through the dictionary items
                    for key2, value2 in value.items():
                        # Print the sub menu item
                        num_item_spaces = 48 - len(key + key2) - 3
                        item_spaces = " " * num_item_spaces
                        print(f"{item_counter}   |"
                              + f"{key} - {key2}{item_spaces}          | "
                              + f"${value2}")
                        # Store the sub menu associated with its menu item number
                        sub_menu_items[item_counter] = key
                        # Add 1 to the item_counter
                        item_counter += 1
                else:
                    # Print the menu item
                    num_item_spaces = 48 - len(key)
                    item_spaces = " " * num_item_spaces
                    print(f"{item_counter}       | "
                          + f"{key}{item_spaces}  |  ${value}")
                    # Add 1 to the item_counter
                    item_counter += 1

            print(menu_dashes)

    # Customer's input
            sub_menu_selection = input("Please select sub menu number or Enter to return to Main menu: ")

    # Exit the loop if user presss 'Enter'
    if sub_menu_selection == 'Enter':
        break
    # Check if the customer's input is a number
    elif sub_menu_selection.isdigit():
        # Check if the customer's input is a valid option
        if int(sub_menu_selection) in sub_menu_items.keys():
        #Save the sub menu selection to a variable
            sub_menu_selection_name = sub_menu_items[int(sub_menu_selection)]
        # Print out the menu selection name 
            print(f"You selected {sub_menu_selection_name}")
        else:
            # Tell the customer they didn't select a menu option
            print(f"{sub_menu_selection} is not a menu options.")
    else:
        # Tell the customer they didn't select a number
        print("You didn't select a number.")
        # Print the options to choose from menu headings


Quantity = int(input("What quantity of " + sub_menu_selection_name + " would you like to purchase? ")
)

# Print results
print(
    "You want to buy "
    + str(Quantity)
    + " "
    + item
)