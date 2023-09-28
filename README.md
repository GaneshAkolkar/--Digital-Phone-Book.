# --DigiCreate a Digital Phone Book 📞

**Statement**
Earlier, we use to have a phone book, which consists of contact numbers. Now that we
know the power of python, let's create a digital phonebook.
What does that mean?
This means we have to create a menu-driven console application, where multiple users
can create their account,
We have to create an authentication system :
1. Registration
2. Login (If user is already registered)
After successful authentication, user should have right to
1. Add contacts
2. Read all contacts
3. Read any specific contact
4. Update any specific contact
5. Delete any specific contact
6. Delete all contactstal-Phone-Book.



import json

# User database to store registered users
user_db = {}

# Phone book to store contacts
phone_book = {}

def register_user():
    username = input("Enter your username: ")
    password = input("Enter your password: ")
    
    if username in user_db:
        print("User already exists. Please login.")
    else:
        user_db[username] = password
        print("Registration successful. You can now log in.")

def login():
    username = input("Enter your username: ")
    password = input("Enter your password: ")
    
    if username in user_db and user_db[username] == password:
        print("Login successful. Welcome,", username)
        return True
    else:
        print("Login failed. Please check your username and password.")
        return False

def add_contact():
    name = input("Enter contact name: ")
    number = input("Enter contact number: ")
    phone_book[name] = number
    print("Contact added successfully.")

def read_all_contacts():
    if phone_book:
        print("Contacts in the phone book:")
        for name, number in phone_book.items():
            print(f"{name}: {number}")
    else:
        print("Phone book is empty.")

def read_specific_contact():
    name = input("Enter the name of the contact you want to read: ")
    if name in phone_book:
        print(f"{name}: {phone_book[name]}")
    else:
        print("Contact not found in the phone book.")

def update_contact():
    name = input("Enter the name of the contact you want to update: ")
    if name in phone_book:
        new_number = input("Enter the new contact number: ")
        phone_book[name] = new_number
        print("Contact updated successfully.")
    else:
        print("Contact not found in the phone book.")

def delete_contact():
    name = input("Enter the name of the contact you want to delete: ")
    if name in phone_book:
        del phone_book[name]
        print("Contact deleted successfully.")
    else:
        print("Contact not found in the phone book.")

def delete_all_contacts():
    global phone_book
    phone_book = {}
    print("All contacts deleted successfully.")

# Main menu
while True:
    print("\nDigital Phone Book Menu:")
    print("1. Register")
    print("2. Login")
    print("3. Add Contact")
    print("4. Read All Contacts")
    print("5. Read Specific Contact")
    print("6. Update Contact")
    print("7. Delete Contact")
    print("8. Delete All Contacts")
    print("9. Exit")
    
    choice = input("Enter your choice: ")
    
    if choice == "1":
        register_user()
    elif choice == "2":
        if login():
            while True:
                print("\nPhone Book Menu:")
                print("1. Add Contact")
                print("2. Read All Contacts")
                print("3. Read Specific Contact")
                print("4. Update Contact")
                print("5. Delete Contact")
                print("6. Delete All Contacts")
                print("7. Logout")
                
                sub_choice = input("Enter your choice: ")
                
                if sub_choice == "1":
                    add_contact()
                elif sub_choice == "2":
                    read_all_contacts()
                elif sub_choice == "3":
                    read_specific_contact()
                elif sub_choice == "4":
                    update_contact()
                elif sub_choice == "5":
                    delete_contact()
                elif sub_choice == "6":
                    delete_all_contacts()
                elif sub_choice == "7":
                    print("Logged out.")
                    break
                else:
                    print("Invalid choice. Please try again.")
    elif choice == "9":
        print("Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")
