import tkinter as tk
from tkinter import ttk
from PIL import Image, ImageTk

# Create a main window
login_window = tk.Tk()
login_window.title("Login Page")

# Apply a modern theme
style = ttk.Style()
style.theme_use('clam')  # Choose a theme (e.g., "clam")

# Login page
matricule_label = ttk.Label(login_window, text="Entrer votre  Matricule:")
matricule_entry = ttk.Entry(login_window)
login_button = ttk.Button(login_window, text="Login")

matricule_label.pack(pady=10)
matricule_entry.pack(pady=5)
login_button.pack(pady=10)

# Create a main menu window
def open_main_menu():
    main_menu_window = tk.Toplevel(login_window)
    main_menu_window.title("Main Menu")

    # Load icon images
    add_icon = Image.open("add_icon.png")
    add_icon = add_icon.resize((50, 50), Image.ANTIALIAS)
    add_icon = ImageTk.PhotoImage(add_icon)

    update_icon = Image.open("update_icon.png")
    update_icon = update_icon.resize((50, 50), Image.ANTIALIAS)
    update_icon = ImageTk.PhotoImage(update_icon)

    delete_icon = Image.open("delete_icon.png")
    delete_icon = delete_icon.resize((50, 50), Image.ANTIALIAS)
    delete_icon = ImageTk.PhotoImage(delete_icon)

    print_icon = Image.open("print_icon.png")
    print_icon = print_icon.resize((50, 50), Image.ANTIALIAS)
    print_icon = ImageTk.PhotoImage(print_icon)

    # Main menu buttons with icons
    add_button = ttk.Button(main_menu_window, image=add_icon, text="Add Item", compound="top")
    update_button = ttk.Button(main_menu_window, image=update_icon, text="Update Item", compound="top")
    delete_button = ttk.Button(main_menu_window, image=delete_icon, text="Delete Item", compound="top")
    print_button = ttk.Button(main_menu_window, image=print_icon, text="Print Items", compound="top")

    add_button.grid(row=0, column=0, padx=10, pady=10)
    update_button.grid(row=0, column=1, padx=10, pady=10)
    delete_button.grid(row=1, column=0, padx=10, pady=10)
    print_button.grid(row=1, column=1, padx=10, pady=10)

# Bind the login button to open the main menu
login_button.config(command=open_main_menu)

# Run the login application
login_window.mainloop()
