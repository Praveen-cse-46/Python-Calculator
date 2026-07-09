# Python-Calculator
Simple Calculator using Python and Tkinter
from tkinter import *

# Create window
root = Tk()
root.title("Simple Calculator")
root.geometry("300x400")

# Entry box
entry = Entry(root, width=20, font=("Arial", 20), borderwidth=5, justify=RIGHT)
entry.grid(row=0, column=0, columnspan=4, padx=10, pady=10)

# Function to click buttons
def click(number):
    current = entry.get()
    entry.delete(0, END)
    entry.insert(0, current + str(number))

# Function to clear
def clear():
    entry.delete(0, END)

# Function to calculate
def equal():
    try:
        result = eval(entry.get())
        entry.delete(0, END)
        entry.insert(0, str(result))
    except:
        entry.delete(0, END)
        entry.insert(0, "Error")

# Button layout
buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '0', '.', '=', '+'
]

row = 1
col = 0

for button in buttons:
    if button == "=":
        Button(root, text=button, width=6, height=2, font=("Arial", 14),
               command=equal).grid(row=row, column=col, padx=5, pady=5)
    else:
        Button(root, text=button, width=6, height=2, font=("Arial", 14),
               command=lambda b=button: click(b)).grid(row=row, column=col, padx=5, pady=5)

    col += 1
    if col > 3:
        col = 0
        row += 1

# Clear button
Button(root, text="Clear", width=28, height=2, font=("Arial", 14),
       command=clear).grid(row=5, column=0, columnspan=4, padx=5, pady=10)

root.mainloop()
  
