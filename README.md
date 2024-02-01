# file_manager.py

import os
import shutil

class FileManager:
    def __init__(self, base_directory):
        self.base_directory = base_directory

    def create_file(self, filename, content=""):
        filepath = os.path.join(self.base_directory, filename)
        with open(filepath, 'w') as file:
            file.write(content)
        print(f"File '{filename}' created.")

    def delete_file(self, filename):
        filepath = os.path.join(self.base_directory, filename)
        if os.path.exists(filepath):
            os.remove(filepath)
            print(f"File '{filename}' deleted.")
        else:
            print(f"File '{filename}' not found.")

    def list_files(self):
        files = [f for f in os.listdir(self.base_directory) if os.path.isfile(os.path.join(self.base_directory, f))]
        if files:
            print("Files in the directory:")
            for file in files:
                print(f"- {file}")
        else:
            print("No files in the directory.")

if __name__ == "__main__":
    base_directory = "files"  # Specify your base directory here
    file_manager = FileManager(base_directory)

    while True:
        print("\nOptions:")
        print("1. Create File")
        print("2. Delete File")
        print("3. List Files")
        print("4. Exit")

        choice = input("Enter your choice (1/2/3/4): ")

        if choice == '1':
            filename = input("Enter the file name: ")
            content = input("Enter the file content (optional): ")
            file_manager.create_file(filename, content)

        elif choice == '2':
            filename = input("Enter the file name to delete: ")
            file_manager.delete_file(filename)

        elif choice == '3':
            file_manager.list_files()

        elif choice == '4':
            print("Exiting the file management system. Goodbye!")
            break

        else:
            print("Invalid choice. Please choose a valid option.")
