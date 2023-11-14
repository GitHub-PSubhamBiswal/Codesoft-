# Codesoft-
Python internship 
task To DO List 1

import tkinter
import tkinter.messagebox
import pickle

window= tkinter.Tk()#tkinter window
window.title("MY TO DO LIST")

def task_adding():
    todo= task_add.get()
    if todo != "":
        todo_box.insert(tkinter.END,todo)
        task_add.delete(0,tkinter.END)
    else:
        tkinter.message.showwarning(title="Attention!",message="to add a task please enter some task")

def task_removing():
    try:
        index_todo = list_box.curselection()[0]
        list_box.delete(index_todo)
    except:
        tkinter.messagebox.showwarning(title="Attention!!",message="to delete a task, you must select a task ")    
                                    

list_box=tkinter.Frame(window)
list_box.pack()

todo_box = tkinter.Listbox(list_box, height=20, width=50 )
todo_box.pack(side=tkinter.LEFT)

scroller = tkinter.Scrollbar(list_box)
scroller.pack(side= tkinter.RIGHT, fill= tkinter.Y)


todo_box.config(yscrollcommand=scroller.set)


task_add= tkinter.Entry(window,width= 70)
task_add.pack()

add_task_button = tkinter.Button(window, text="CLICK TO ADD TASK",font= ("arial",20,"bold"),background="red",width=40,command= task_adding)
add_task_button.pack()

remove_task_button = tkinter.Button(window, text="CLICK TO DELETE TASK",font=("arial",20,"bold"),background="yellow",width=40,command= task_removing)
remove_task_button.pack()

window.mainloop()



Task no  2
calculator

print("MINI CALCULATOR")
a = float(input("enter the first no."))
b=float(input("enter the second no."))
#options
print("press 1 if you want to add the numbers")
print("press 2 if you want to sub. the numbers")
print("press 3 if you want to multiply the numbers")
print("press 4 if you want to div. the numbers")

choice=int(input("enter your choice from 1-4"))
#condition
if choice==1:
    print(a+b)
elif choice==2:
    print(a-b)    
elif choice==3:
    print(a*b)
elif choice==4:
    print(a/b) 
else:
    print("invalid choice")


Task no 3
password Generator


#first we will import the necessary modules

import random
#define data
lower_case= "abcdefghijklmnopqrstuvwxxyz"
upper_case= "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
num="1234567890"
special_characters="@#$&!{}()[]"

#combine the data
ans= lower_case+ upper_case + num + special_characters

#taking input length
len= int(input("enter the length of password"))
#using random
temp= random.sample(ans,len)

#generate password
password= "".join(temp)

#print password
print("password",password)