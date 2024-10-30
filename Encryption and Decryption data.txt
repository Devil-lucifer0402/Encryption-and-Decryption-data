from tkinter import *
from tkinter import messagebox
import base64

# Screen
screen = Tk()
screen.geometry("420x420")
screen.title("caesar cipher")
screen.configure(bg="light grey")


def encrypt():
    password=pw.get()
    if password=="123":
        screen1=Toplevel(screen)
        screen1.title("Data encrypt")
        screen1.geometry("400x250")
        screen1.configure(bg="pink")

        message=text1.get(1.0,END)
        encode_message = message.encode("ascii")
        base64_bytes = base64.b64encode(encode_message)
        encrypt = base64_bytes.decode("ascii")

        Label(screen1,text="Code is Encrypted",font="arial 10 bold",bg="light green").place(x=140,y=6)
        text2 = Text(screen1,font="30",bd=4,wrap=WORD)
        text2.place(x=2,y=30,width=390,height=180)
        text2.insert(END,encrypt)

    elif(password==""):
        messagebox.showerror("Error","Please enter the secret key")
    elif(password!="123"):
        messagebox.showerror("oops","Invalid secret key")

def decrypt():
    password = pw.get()
    if password == "123":
        screen2 = Toplevel(screen)
        screen2.title("Data Decrypt")
        screen2.geometry("400x250")
        screen2.configure(bg="green")

        message = text1.get(1.0, END)
        encode_message = message.encode("ascii")
        base64_bytes = base64.b64decode(encode_message)
        encrypt = base64_bytes.decode("ascii")

        Label(screen2, text="Code is Decrypted", font="arial 10 bold", bg="light pink").place(x=140, y=6)
        text2 = Text(screen2, font="30", bd=4, wrap=WORD)
        text2.place(x=2, y=30, width=390, height=180)
        text2.insert(END, encrypt)

    elif (password == ""):
        messagebox.showerror("Error", "Please enter the secret key")
    elif (password != "123"):
        messagebox.showerror("oops", "Invalid secret key")

def reset():
    text1.delete(1.0,END)
    pw.set("")
#label
Label(screen, bd=5,text="Enter The Text For Encryption and Decryption",font="arial 13 bold", bg="khaki").place(x=20,y=10)


#Text
text1=Text(screen, bd=4,font="20",bg="misty rose")
text1.place(x=5,y=45, width=410,height=120)

#Label
Label(screen,bd=3,text="Enter secret key", font="arial 12 bold").place(x=140,y=180)

#entry
pw=StringVar()
Entry(textvariable=pw,bd=4,font="20", show="*").place(x=110,y=220)

#Button
Button(screen,text="Encrypt",font="arial 15 bold ",bg="red",fg="white",command=encrypt).place(x=40,y=280,width=150)
Button(screen,text="Decrypt",font="arial 15 bold ",bg="Green",fg="white",command=decrypt).place(x=230,y=280,width=150)
Button(screen,text="Reset",font="arial 15 bold ",bg="light Blue",fg="black",command=reset).place(x=110,y=350,width=200)


mainloop()
