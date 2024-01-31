import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QWidget, QVBoxLayout, QLabel, QLineEdit, QPushButton, QTableWidget, QTableWidgetItem
from PyQt5.QtGui import QIcon
from PyQt5.QtCore import Qt


class AddItemPage(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Add Item")
        self.setWindowIcon(QIcon("icon.png"))  # Replace "icon.png" with the path to your icon
        self.setStyleSheet("background-color: #f0f0f0;")

        self.setupUI()

    def setupUI(self):
        self.reference_label = QLabel("Reference:")
        self.reference_input = QLineEdit()

        self.name_label = QLabel("Name:")
        self.name_input = QLineEdit()

        self.color_label = QLabel("Color:")
        self.color_input = QLineEdit()

        self.entry_date_label = QLabel("Entry Date:")
        self.entry_date_input = QLineEdit()

        self.exit_date_label = QLabel("Exit Date:")
        self.exit_date_input = QLineEdit()

        self.add_button = QPushButton("Add Item")
        self.add_button.clicked.connect(self.add_item)

        layout = QVBoxLayout()
        layout.addWidget(self.reference_label)
        layout.addWidget(self.reference_input)
        layout.addWidget(self.name_label)
        layout.addWidget(self.name_input)
        layout.addWidget(self.color_label)
        layout.addWidget(self.color_input)
        layout.addWidget(self.entry_date_label)
        layout.addWidget(self.entry_date_input)
        layout.addWidget(self.exit_date_label)
        layout.addWidget(self.exit_date_input)
        layout.addWidget(self.add_button)

        self.setLayout(layout)

    def add_item(self):
        reference = self.reference_input.text()
        name = self.name_input.text()
        color = self.color_input.text()
        entry_date = self.entry_date_input.text()
        exit_date = self.exit_date_input.text()

        print("Item added to the database:")
        print("Reference:", reference)
        print("Name:", name)
        print("Color:", color)
        print("Entry Date:", entry_date)
        print("Exit Date:", exit_date)


class ViewDatabasePage(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("View Database")
        self.setWindowIcon(QIcon("icon.png"))  # Replace "icon.png" with the path to your icon
        self.setStyleSheet("background-color: #f0f0f0;")

        self.setupUI()

    def setupUI(self):
        self.database_contents_label = QLabel("Database Contents:")
        self.table_widget = QTableWidget()

        self.table_widget.setColumnCount(5)
        self.table_widget.setHorizontalHeaderLabels(["Reference", "Name", "Color", "Entry Date", "Exit Date"])

        # Add sample data to the table (you can replace this with actual database contents)
        data = [
            ["001", "Item1", "Red", "2022-01-01", "2022-01-10"],
            ["002", "Item2", "Blue", "2022-01-05", "2022-01-15"],
            ["003", "Item3", "Green", "2022-01-10", "2022-01-20"]
        ]

        self.table_widget.setRowCount(len(data))

        for i, row in enumerate(data):
            for j, val in enumerate(row):
                item = QTableWidgetItem(val)
                self.table_widget.setItem(i, j, item)

        layout = QVBoxLayout()
        layout.addWidget(self.database_contents_label)
        layout.addWidget(self.table_widget)

        self.setLayout(layout)


class LoginPage(QWidget):
    def __init__(self, main_window):
        super().__init__()
        self.main_window = main_window
        self.setWindowTitle("Employee Login")
        self.setWindowIcon(QIcon("icon.png"))  # Replace "icon.png" with the path to your icon
        self.setStyleSheet("background-color: #f0f0f0;")

        self.setupUI()

    def setupUI(self):
        self.matricule_label = QLabel("Matricule Number:")
        self.matricule_input = QLineEdit()

        self.login_button = QPushButton("Login")
        self.login_button.clicked.connect(self.login)

        self.status_label = QLabel("")

        layout = QVBoxLayout()
        layout.addWidget(self.matricule_label)
        layout.addWidget(self.matricule_input)
        layout.addWidget(self.login_button)
        layout.addWidget(self.status_label)

        self.setLayout(layout)

    def login(self):
        matricule = self.matricule_input.text()
        if matricule == "1587":
            self.status_label.setText("Login successful")
            self.main_window.open_add_item_page()
        elif matricule == "1893":
            self.status_label.setText("Login successful")
            self.main_window.open_view_database_page()
        else:
            self.status_label.setText("Invalid matricule number")


class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Item Management System")
        self.setWindowIcon(QIcon("icon.png"))  # Replace "icon.png" with the path to your icon
        self.setStyleSheet("background-color: #f0f0f0;")
        self.login_page = LoginPage(self)
        self.setCentralWidget(self.login_page)

    def open_add_item_page(self):
        self.add_item_page = AddItemPage()
        self.setCentralWidget(self.add_item_page)

    def open_view_database_page(self):
        self.view_database_page = ViewDatabasePage()
        self.setCentralWidget(self.view_database_page)


# Create the application instance
app = QApplication(sys.argv)

# Create the main window
main_window = MainWindow()
main_window.show()

# Run the application
sys.exit(app.exec_())
                    
