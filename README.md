def display_menu():
    print("\nContact Book Menu")
    print("1. Add a new contact")
    print("2. Search for a contact")
    print("3. Delete a contact")
    print("4. Display all contacts")
    print("5. Exit")

def add_contact(contacts):
    name = input("Enter contact name: ").strip()
    if not name:
        print("⚠ Name cannot be empty.")
        return
    if name in contacts:
        print("⚠ This contact already exists.")
        return

    phone = input("Enter phone number (10 digits): ").strip()
    try:
        if not phone.isdigit():
            # Contains non-numeric characters
            raise ValueError("Phone number must contain digits only.")
        if len(phone) != 10:
            # Not exactly 10 digits
            raise ValueError("Phone number must be exactly 10 digits.")
    except ValueError as e:
        print("⚠ Invalid phone number:", e)
        return

    contacts[name] = phone
    print(f"✅ Contact '{name}' added successfully.")

def search_contact(contacts):
    name = input("Enter contact name to search: ").strip()
    if name in contacts:
        print(f"{name}: {contacts[name]}")
    else:
        print("Contact not found.")

def delete_contact(contacts):
    name = input("Enter contact name to delete: ").strip()
    if name in contacts:
        del contacts[name]
        print(f"Contact '{name}' deleted successfully.")
    else:
        print("Contact not found.")

def display_contacts(contacts):
    if not contacts:
        print("No contacts to display.")
    else:
        print("\nAll Contacts:")
        for name, phone in contacts.items():
            print(f"{name}: {phone}")

def main():
    contacts = {}
    while True:
        display_menu()
        choice = input("Enter your choice (1-5): ").strip()
        if choice == '1':
            add_contact(contacts)
        elif choice == '2':
            search_contact(contacts)
        elif choice == '3':
            delete_contact(contacts)
        elif choice == '4':
            display_contacts(contacts)
        elif choice == '5':
            print("Exiting Contact Book. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":

    main()
    
