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
