# Create your own IDE
Forget about using Visual Studio Code or PyCharm. With just 70 lines of Python code, you can create your own lightweight Python IDE! This custom IDE allows you to write, save, open, and run Python code easily.
Steps to Build
Import Necessary Modules

Use tkinter for creating the GUI.
Import tkinter.filedialog for file operations.
Import subprocess to run Python code directly from the IDE.

from tkinter import *
from tkinter.filedialog import asksaveasfilename, askopenfilename
import subprocess
Initialize the Compiler Window

compiler = Tk()
compiler.title('Your IDE Name')  # Set your IDE's title
file_path = ''  # To store the path of the current file
Define File and Run Functions

Set File Path: Store the file path for the current file.
Open File: Open and read Python files.
Save File: Save the code to the current file or a new one.
Run Code: Run the Python script and display the output or errors.

def set_file_path(path):
    global file_path
    file_path = path

def open_file():
    path = askopenfilename(filetypes=[('Python Files', '*.py')])
    with open(path, 'r') as file:
        code = file.read()
        editor.delete('1.0', END)
        editor.insert('1.0', code)
        set_file_path(path)

def save_as():
    global file_path
    if file_path == '':
        path = asksaveasfilename(filetypes=[('Python Files', '*.py')])
    else:
        path = file_path
    with open(path, 'w') as file:
        code = editor.get('1.0', END)
        file.write(code)
        set_file_path(path)

def run():
    if file_path == '':
        save_prompt = Toplevel()
        text = Label(save_prompt, text='Please save your code')
        text.pack()
        return
    command = f'python {file_path}'
    process = subprocess.Popen(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE, shell=True)
    output, error = process.communicate()
    code_output.delete('1.0', END)
    code_output.insert('1.0', output)
    code_output.insert('1.0', error)
Create Menus

Add File and Run menus to the menu bar.

menu_bar = Menu(compiler)

file_menu = Menu(menu_bar, tearoff=0)
file_menu.add_command(label='Open', command=open_file)
file_menu.add_command(label='Save', command=save_as)
file_menu.add_command(label='Save As', command=save_as)
file_menu.add_command(label='Exit', command=exit)
menu_bar.add_cascade(label='File', menu=file_menu)

run_menu = Menu(menu_bar, tearoff=0)
run_menu.add_command(label='Run', command=run)
menu_bar.add_cascade(label='Run', menu=run_menu)

compiler.config(menu=menu_bar)
Create the Text Editor and Output Area

Use Text widgets for the code editor and the output display.

editor = Text()
editor.pack()

code_output = Text(height=10)
code_output.pack()
Run the Compiler
Finally, launch the IDE:

compiler.mainloop()
Now you have your very own Python IDE! It includes:

Open, Save, and Run functionality
A text editor to write your code
An output area to display results and errors
Features:
Lightweight: Just 70 lines of code!
Customizable: Add more features like syntax highlighting or debugging support.
Enjoy coding with your new IDE! 🎉
