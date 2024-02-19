class Library:
    def __init__(self):
        self.file = open("books.txt", "a+")  # Open the file in append mode (create if not exists)
        self.file.seek(0)  # Move the cursor to the beginning of the file

    def __del__(self):
        self.file.close()  # Close the file when the object is destroyed

    def add_book(self):
        title = input("Enter book title: ").strip().title()
        author = input("Enter book author: ").strip().title()
        year = input("Enter first release year: ").strip()
        pages = input("Enter number of pages: ").strip()
        self.file.write(f"{title},{author},{year},{pages}\n")
        print("Book added successfully.")

    def list_books(self):
        self.file.seek(0)  # Move the cursor to the beginning of the file
        books = self.file.read().splitlines()  # Read the file and split lines into a list
        if not books:
            print("No books available.")
        else:
            books = sorted(books, key=lambda x: x.split(',')[0])
            for book in books:
                title, author, year, pages = book.split(',')
                print(f"Title: {title}, Author: {author}")

    def remove_book(self):
        title = input("Enter the title of the book to remove: ").title()
        self.file.seek(0)
        books = self.file.readlines()
        updated_books = []
        removed = False
        for book in books:
            if title not in book.strip().split(',')[0]:
                updated_books.append(book)
            else:
                removed = True
        if not removed:
            print("Book not found.")
            return
        self.file.seek(0)
        self.file.truncate()
        self.file.writelines(updated_books)
        print("Book removed successfully.")


# Create an object named "lib" with "Library" class
lib = Library()

# Create a menu to interact with the "lib" object
while True:
    print("\n***MENU***")
    print("1) List Books")
    print("2) Add Book")
    print("3) Remove Book")
    print("Q) Quiting System")

    choice = input("Enter your choice: ")
    print()

    if choice == "1":
        lib.list_books()
    elif choice == "2":
        lib.add_book()
    elif choice == "3":
        lib.remove_book()
    elif choice == "Q".casefold():
        print("Quiting...")
        break
    else:
        print("Invalid choice. Please enter a valid option.")
