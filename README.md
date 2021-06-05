# Saving-Passwords
#Imports
import tkinter as tk
from tkinter import simpledialog
from tkinter import messagebox

#Telling coumputor I am going to use tinker
ROOT = tk.Tk()
Frame = tk.Frame(ROOT)
Frame.pack()

#The code for how enter and save that data to the Data file
def Enter_Data():
    Password = simpledialog.askstring(title="Password Safe", prompt="Enter Password:")
    if Password == str("12345"):
        Username = simpledialog.askstring(title="Password Safe", prompt="Username and Password:") 
        Username = Username + "\ "
        file = open('D:\Dattu\Password Safe Data\Data.txt', 'a')
        file.write(Username)
        file.close()
        messagebox.showinfo("Thanks", "Your information have been saved")
    else:
        messagebox.showerror("Error","This is the wrong Password! Please try again")
        
#The code for how to see the saved data in the Data file
def See_Data():
    Password = simpledialog.askstring(title="Password Safe", prompt="Enter Password:")
    if Password == str("12345"):
        file = open('D:\Dattu\Password Safe Data\Data.txt')
        data = file.readlines()
        file.close()
        messagebox.showinfo("Here is your Usernames and Passwords", data)
    else:
        messagebox.showerror("Error","This is the wrong Password! Please try again")
        
#The code for to clear all the data in the Data file       
def Clear_Data():
    Password = simpledialog.askstring(title="Password Safe", prompt="Enter Password:")
    if Password == str("12345"):
        f = open("D:\Dattu\Password Safe Data\Data.txt", "r+") 
        f.seek(0) 
        f.truncate()
    else:
        messagebox.showerror("Error","This is the wrong Password! Please try again")
        
#The code for asking if they want to enter the data to the Data file,if they want to see the saved data in the Data file, or if
#they want to clear all the data in the data file
def Start():
    Enter = tk.Button(ROOT, text="Enter Data", command=Enter_Data)
    Enter.pack(side=tk.LEFT)

    See = tk.Button(ROOT, text="See Data", command=See_Data)
    See.pack(side=tk.RIGHT)
    
    Clear = tk.Button(ROOT, text="Clear All Data", command=Clear_Data)
    Clear.pack(side=tk.TOP)
    
#Running the code
Start()
ROOT.mainloop()
