# Number-Gussing-Game
from tkinter import Label,Button,Entry,Tk,StringVar
import random

window=Tk()
window.geometry("600x500")
window.title("Number Guessing Game")

n=random.randint(0,100)
attempt=10
def Check():
    global attempt
    global text
    attempt-=1
    guess=int(entry.get())
    if n==guess:
        text.set("You win! Congratulations!")
        b1.pack_forget()
    elif attempt==0:
        text.set("You are out of attempts!")
        b1.pack_forget()
    elif n>guess:
        text.set("Incoorect! You have "+str(attempt)+" attempts remaining- Go Higher!!")
        svalue.set("")
        entry.update()
    elif n<guess:
        text.set("Incoorect! You have "+str(attempt)+" attempts remaining- Go Lower!!")
        svalue.set("")
        entry.update()
label1=Label(window,text="Hello, Play And Enjoy This Game", font='times 24 bold italic')
label1.pack()

label2=Label(window,text="Enter a number Between 1 to 100 ", font='times 14 bold italic')
label2.pack()

svalue=StringVar()
svalue.set("")

entry=Entry(window,textvar=svalue,width=40,borderwidth=4)
entry.pack()

b1=Button(window,text="Check", command=Check)
b1.pack()

b2=Button(window,text="Quit", command=window.destroy)
b2.pack()

text=StringVar()
text.set("You have 10 attempts remaining! Good Luck")

guess_attempts=Label(window,textvariable=text)
guess_attempts.pack()

window.mainloop()
