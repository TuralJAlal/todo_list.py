# todo_list.py# todo_list.py

def read_todo_list(filename):
    try:
        with open(filename, 'r') as file:
            return file.readlines()
    except FileNotFoundError:
        return []

def write_todo_list(filename, items):
    with open(filename, 'w') as file:
        file.write('\n'.join(items))

def show_todo_list(items):
    for index, item in enumerate(items, start=1):
        print(f"{index}. {item.strip()}")

def add_item(items, new_item):
    items.append(new_item)

def remove_item(items, index):
    try:
        items.pop(index - 1)
    except IndexError:
        print("Invalid index. No item removed.")

def main():
    filename = "todo.txt"
    todo_list = read_todo_list(filename)

    while True:
        print("\nTODO List:")
        show_todo_list(todo_list)

        print("\nOptions:")
        print("1. Add item")
        print("2. Remove item")
        print("3. Quit")

        choice = input("Enter your choice (1/2/3): ")

        if choice == "1":
            new_item = input("Enter the new item: ")
            add_item(todo_list, new_item)
        elif choice == "2":
            index = int(input("Enter the index of the item to remove: "))
            remove_item(todo_list, index)
        elif choice == "3":
            write_todo_list(filename, todo_list)
            print("TODO list saved. Exiting.")
            break
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()
