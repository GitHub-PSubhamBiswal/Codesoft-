#1 Task One (to_do_list) 
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
   
 #Task 2 my_calculator 
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
  
 Task 3  
 #password generator 
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
  
 Task 4 rock paper scissors  
 import random 
  
 def get_user_choice(): 
     user_choice = input("Please choose: rock, paper, or scissors. ").lower() 
     while user_choice not in ['rock', 'paper', 'scissors']: 
         print("Invalid choice. Please choose rock, paper, or scissors.") 
         user_choice = input().lower() 
     return user_choice 
  
 def get_computer_choice(): 
     return random.choice(['rock', 'paper', 'scissors']) 
  
 def determine_winner(user_choice, computer_choice): 
     if user_choice == computer_choice: 
         return "It's a tie!" 
     elif (user_choice == 'rock' and computer_choice == 'scissors') or \ 
          (user_choice == 'scissors' and computer_choice == 'paper') or \ 
          (user_choice == 'paper' and computer_choice == 'rock'): 
         return "You win!" 
     else: 
         return "You lose!" 
  
 def play_game(): 
     user_score = 0 
     computer_score = 0 
  
     while True: 
         user_choice = get_user_choice() 
         computer_choice = get_computer_choice() 
  
         print(f"\nYou chose {user_choice}, and I chose {computer_choice}.") 
  
         result = determine_winner(user_choice, computer_choice) 
         print("Result:", result) 
  
         if result == "You win!": 
             user_score += 1 
         elif result == "You lose!": 
             computer_score += 1 
  
         print(f"Score - You: {user_score}, Computer: {computer_score}\n") 
  
         play_again = input("Do you want to play again? (Yes/No) ").lower() 
         if play_again != 'yes': 
             print("Thanks for playing! Final scores:") 
             print(f"You: {user_score}, Computer: {computer_score}") 
             break 
  
 play_game() 
  
  
 #Task 5  
 #Contact Book  
 class Contact: 
     def __init__(self, name, phone_number, email, address): 
         self.name = name 
         self.phone_number = phone_number 
         self.email = email 
         self.address = address 
  
 class ContactBook: 
     def __init__(self): 
         self.contacts = [] 
  
     def add_contact(self, contact): 
         self.contacts.append(contact) 
         print("Contact added successfully!") 
  
     def view_contact_list(self): 
         print("\nContact List:") 
         for contact in self.contacts: 
             print(f"Name: {contact.name}, Phone: {contact.phone_number}") 
  
     def search_contact(self, query): 
         results = [contact for contact in self.contacts if query.lower() in contact.name.lower() or query in contact.phone_number] 
         if results: 
             print("\nSearch Results:") 
             for contact in results: 
                 print(f"Name: {contact.name}, Phone: {contact.phone_number}") 
         else: 
             print("No matching contacts found.") 
  
     def update_contact(self, name, new_phone_number, new_email, new_address): 
         for contact in self.contacts: 
             if contact.name.lower() == name.lower(): 
                 contact.phone_number = new_phone_number 
                 contact.email = new_email 
                 contact.address = new_address 
                 print("Contact updated successfully!") 
                 return 
         print("Contact not found.") 
  
     def delete_contact(self, name): 
         for contact in self.contacts: 
             if contact.name.lower() == name.lower(): 
                 self.contacts.remove(contact) 
                 print("Contact deleted successfully!") 
                 return 
         print("Contact not found.") 
  
 def main(): 
     contact_book = ContactBook() 
  
     while True: 
         print("\nContact Book Menu:") 
         print("1. Add Contact") 
         print("2. View Contact List") 
         print("3. Search Contact") 
         print("4. Update Contact") 
         print("5. Delete Contact") 
         print("6. Exit") 
  
         choice = input("Enter your choice (1-6): ") 
  
         if choice == '1': 
             name = input("Enter name: ") 
             phone_number = input("Enter phone number: ") 
             email = input("Enter email: ") 
             address = input("Enter address: ") 
             new_contact = Contact(name, phone_number, email, address) 
             contact_book.add_contact(new_contact) 
  
         elif choice == '2': 
             contact_book.view_contact_list() 
  
         elif choice == '3': 
             query = input("Enter name or phone number to search: ") 
             contact_book.search_contact(query) 
  
         elif choice == '4': 
             name = input("Enter name of contact to update: ") 
             new_phone_number = input("Enter new phone number: ") 
             new_email = input("Enter new email: ") 
             new_address = input("Enter new address: ") 
             contact_book.update_contact(name, new_phone_number, new_email, new_address) 
  
         elif choice == '5': 
             name = input("Enter name of contact to delete: ") 
             contact_book.delete_contact(name) 
  
         elif choice == '6': 
             print("Exiting Contact Book. Goodbye!") 
             break 
  
         else: 
             print("Invalid choice. Please enter a number from 1 to 6.") 
  
 if __name__ == "__main__": 
     main()