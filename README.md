from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import (
    QApplication, QWidget, QPushButton, QVBoxLayout, QHBoxLayout, QLabel, QRadioButton, QButtonGroup
)
import random

app = QApplication([])

win = QWidget()
win.setWindowTitle("Randomizer")
win.resize(400, 250)

title_text = QLabel("Испытай удачу друг")
font = title_text.font()
font.setPointSize(14)
title_text.setFont(font)

rbtn1 = QRadioButton("1")
rbtn2 = QRadioButton("2")
rbtn3 = QRadioButton("3")
rbtn4 = QRadioButton("4")
rbtn5 = QRadioButton("5")

button_group = QButtonGroup()
button_group.addButton(rbtn1, 1)
button_group.addButton(rbtn2, 2)
button_group.addButton(rbtn3, 3)
button_group.addButton(rbtn4, 4)
button_group.addButton(rbtn5, 5)

btn_submit = QPushButton("Подтвердить")

line = QVBoxLayout()
line1 = QHBoxLayout()

line1.addWidget(rbtn1)
line1.addWidget(rbtn2)
line1.addWidget(rbtn3)
line1.addWidget(rbtn4)
line1.addWidget(rbtn5)

line.addWidget(title_text, alignment=Qt.AlignCenter)
line.addLayout(line1)
line.addWidget(btn_submit, alignment=Qt.AlignCenter)

win.setLayout(line)

def check_win():
    player_choice = button_group.checkedId()
    
    if player_choice == -1:
        title_text.setText("Сначала выбери число")
        return

    secret_number = random.randint(1, 6)
    if player_choice == secret_number:
        title_text.setText("Правильно")
    else:
        title_text.setText(f"не угадал, было число {secret_number}")

btn_submit.clicked.connect(check_win)

win.show()
app.exec_()




import random

from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import QApplication, QWidget, QPushButton, QLabel, QVBoxLayout

def generate_winner():
    random_number = random.randint(1, 100)
    number.setText(str(random_number))

app = QApplication([])
win = QWidget()
win.setWindowTitle("Randomizer")
win.resize(400, 200)

title = QLabel("Нажмите, чтобы определить победителя")
number = QLabel("0")
btn = QPushButton("Сгенерировать")

btn.clicked.connect(generate_winner)

line = QVBoxLayout()
line.addWidget(title, alignment=Qt.AlignCenter)
line.addWidget(number, alignment=Qt.AlignCenter)
line.addWidget(btn, alignment=Qt.AlignCenter)

win.setLayout(line)
win.show()
app.exec_()

win.show()
app.exec_()
