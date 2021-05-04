# IDE
Now no need to use VScode or Pycharm now with just 70 lines of python code you can make your own IDE!!
In your own IDE you can run your code, save your code, open another code and exit it!!
I have done it by using Pycharm which is an python code editor.
In the firs of my code I have imported tkinter which is default in Pycharm.
Then I have told the tkinter, tkinter.filedialog import asksaveasfilename, askopenfilename.
Then I have imported subprocess.
Then I have created a variable called compiler and entered the value as Tk().
Then I hav told the compiler that compiler.title('**THE NAME YOU WANT TO DISPLAY ON LEFT TOP CORNER**').
Then I have created another variable called file_path and entered the value as ''.
Then I have created a function called def set_file_path(path): and inside the function I have written global file_path file_path = path.
Then I have created another function called def open_file(): and inside it I have created a variable called path and entered the value as askopenfilename(filetypes=[('Python Files', '*.py')]), Then I have written with open(path, 'r') as file: and inside it I have created another variable called code and entered the value as file.read() then I have written editor.delete('1.0', END) editor.insert('1.0', code) set_file_path(path).
Then I have created another function callled def save_as(): and inside it I have written if file_path == '': path = asksaveasfilename(filetypes=[('Python Files', '*.py')]) else: path = file_path with open(path, 'w') as file: code = editor.get('1.0', END) file.write(code) set_file_path(path).
Then I have created another function called def run(): and inside this function I have written if file_path == '': save_prompt = Toplevel() text = Label(save_prompt, text='Please save your code') text.pack() return command = f'python{file_path}' process = subprocess.Popen(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE, shell=True) output, error = process.communicate() code_output.insert('1.0', output) code_output.insert('1.0', error).
Then I have created another variable called menu_bar and entered the value as Menu(compiler).
Then for the file_menu I have written some code file_menu = Menu(menu_bar, tearoff=0) file_menu.add_command(label='Open', command=open_file) file_menu.add_command(label='Save', command=save_as) file_menu.add_command(label='Save As', command=save_as) file_menu.add_command(label='Exit', command=exit) menu_bar.add_cascade(label='File', menu=file_menu).
And same for th run_bar I have written run_bar = Menu(menu_bar, tearoff=0) run_bar.add_command(label='Run', command=run) menu_bar.add_cascade(label='Run', menu=run_bar).
Then I have written compiler.config(menu=menu_bar).
And for the editor I have written editor = Text() and then editor.pack().
And for the code output I have written code_output = Text(height=10) and then code_output.pack()
And then to run program I have written compiler.mainloop().
And there you go your own new IDE is ready now you can ditch Visual Code and Pycharm!!
