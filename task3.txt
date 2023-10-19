import random
import string
from tkinter import *
from tkinter import ttk

root1 = Tk()

frm1 = ttk.Frame(root1, padding=300)
frm2 = ttk.Frame(root1,padding=300)
user= StringVar()
password_length = StringVar()


randomcharlist = []
characters = string.ascii_letters + string.digits + string.punctuation
for i in range(len(characters)):
    X = randomcharlist.append(characters[i])


def password():
    password_length_string = password_length.get()

    random_password_list = random.choices(randomcharlist, weights=None, cum_weights=None, k= int(password_length_string))
    random_password = ''.join(random_password_list)

    root2 = Toplevel(root1)
    frm2 = ttk.Frame(root2, padding=300)
    frm2.grid()
    ttk.Label(frm2, text= "Password: " + random_password, font=("Arial", 20)).grid(column=0, row=0)
    ttk.Button(frm2, text="Quit", command=root2.destroy).grid(column=0, row=1)



frm1.grid()

ttk.Label(frm1, text=f"\tEnter a password length: ", font=("Arial", 20)).grid(column=0, row=3)
ttk.Entry(frm1, textvariable= password_length).grid(column = 0, row = 4)
ttk.Button(frm1, text="Quit", command=root1.destroy).grid(column=0, row=5)
ttk.Button(frm1, text="Enter", command=password).grid(column=1, row=5)
frm2.grid()
ttk.Label(frm1,text=f"Enter user name:",font=("Arial",20)).grid(column=0, row=0)
ttk.Entry(frm1,textvariable= user).grid(column= 0,row=1)

mainloop()