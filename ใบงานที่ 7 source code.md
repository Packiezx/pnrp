ข้อที่ 1
from tkinter import *

def bt1_Click():
 x=int(et_weight.get())
 y=int(et_height.get())
 y=y/100
 z=float(x/(y*y))
 t_BMI.set(f'{z:.4f}')
 bt2_Click(z)

def bt2_Click(c):
    if c<18.7:
     t_Status.set(f'Underweight')
     lb8 = Label(root, text='', textvariable=t_Status,bg='white').grid(row=8,column=2,padx=(0,65))
    elif c<24.9:
     t_Status.set(f'Normal')
     lb8 = Label(root, text='', textvariable=t_Status,bg='green').grid(row=8,column=2,padx=(0,65))
    elif c<29.9:
     t_Status.set(f'Overweight')
     lb8 = Label(root, text='', textvariable=t_Status,bg='yellow').grid(row=8,column=2,padx=(0,65))
    else :
     t_Status.set(f'Obese')
     lb8 = Label(root, text='', textvariable=t_Status,bg='red').grid(row=8,column=2,padx=(0,65))
     
root = Tk()
root.geometry('280x350')
root.resizable(False, False)
root.title('Body-Mass Index(BMI)')
root.option_add('*font','Calibri 16')
root.configure(bg = '#E8B4F7')
et_weight = StringVar()
et_height = StringVar()
t_BMI = StringVar()
t_Status = StringVar()

lb1 = Label(root, text='Weight',bg = '#E8B4F7').grid(row=1, column=1,padx=(0,10))
lb2 = Label(root, text='Height',bg = '#E8B4F7').grid(row=2, column=1,padx=(0,10))
lb3 = Label(root, text='',bg = '#E8B4F7').grid(row=0, column=0)
et1 = Entry(root, textvariable=et_weight, width=9).grid(row=1, column=2,padx=(0,60))
et2 = Entry(root, textvariable=et_height, width=9).grid(row=2, column=2,padx=(0,60))
lb3 = Label(root, text='',bg = '#E8B4F7').grid(row=3, column=0)
btn1 = Button(root, text='คำนวณค่า', command=bt1_Click).grid(row=4,column=1,columnspan=2,padx=(0,20))
lb3 = Label(root, text='',bg = '#E8B4F7').grid(row=5, column=0)
lb4 = Label(root, text='ผลการคำนวณ',bg = '#E8B4F7').grid(row=6, column=1)
lb5 = Label(root, text='BMI      =',bg = '#E8B4F7').grid(row=7, column=1)
lb6 = Label(root, text='Status   =',bg = '#E8B4F7').grid(row=8, column=1)
lb7 = Label(root, text='', textvariable=t_BMI,bg = '#E8B4F7').grid(row=7,column=2,padx=(0,65))
lb8 = Label(root, text='', textvariable=t_Status,bg = '#E8B4F7').grid(row=8,column=2,padx=(0,65))

t_BMI.set("n/a")
t_Status.set("n/a")

root.mainloop()

ข้อที่ 2
from tkinter import *

eps = ""

def press(num):
    global eps
    eps = eps + str(num)
    equ.set(eps)

def equalpress():
    try:
        global eps
        total = str(eval(eps))
        equ.set(total)
        eps = total
 
    except:
        equ.set("Error")
        eps = ""

def clear():
    global eps
    eps = ""
    equ.set("0")
 
cal = Tk()
cal.title("Calculator")
cal.option_add('*font','Calibri 15')
cal.geometry('240x268')
cal.configure(bg = 'black')
cal.resizable(False,False)
equ = StringVar()

et = Entry(cal,textvariable=equ,width=22,borderwidth=10,justify = RIGHT).grid(row=0, column=0,columnspan=4)
button0 = Button(cal, text=' 0 ',width=11,command=lambda: press(0)).grid(row=5, column=0,columnspan=2)
button1 = Button(cal, text=' 1 ',width=5,command=lambda: press(1)).grid(row=4, column=0)
button2 = Button(cal, text=' 2 ',width=5,command=lambda: press(2)).grid(row=4, column=1)
button3 = Button(cal, text=' 3 ',width=5,command=lambda: press(3)).grid(row=4, column=2)
button4 = Button(cal, text=' 4 ',width=5,command=lambda: press(4)).grid(row=3, column=0)
button5 = Button(cal, text=' 5 ',width=5,command=lambda: press(5)).grid(row=3, column=1)
button6 = Button(cal, text=' 6 ',width=5,command=lambda: press(6)).grid(row=3, column=2)
button7 = Button(cal, text=' 7 ',width=5,command=lambda: press(7)).grid(row=2, column=0)
button8 = Button(cal, text=' 8 ',width=5,command=lambda: press(8)).grid(row=2, column=1)
button9 = Button(cal, text=' 9 ',width=5,command=lambda: press(9)).grid(row=2, column=2)

plus = Button(cal, text=' + ',width=5,height=3,command=lambda: press("+"),bg = '#F9C0C0').grid(row=2, column=3,rowspan=2)
minus = Button(cal, text=' - ',width=5,command=lambda: press("-"),bg = '#F6D6AD').grid(row=1, column=3)
multiply = Button(cal, text=' * ',width=5,command=lambda: press("*"),bg = '#FAFCC2').grid(row=1, column=2)
divide = Button(cal, text=' / ',width=5,command=lambda: press("/"),bg = '#CCF6C8').grid(row=1, column=1)
equal = Button(cal, text=' EN ',width=5,height=3, command=equalpress,bg = '#F97EC0').grid(row=4, column=3,rowspan=2)
clear = Button(cal, text='clr',width=5,command=clear,bg = '#76F6C8').grid(row=1, column=0)
decimal= Button(cal, text='.',width=5,command=lambda: press('.')).grid(row=5, column=2)

equ.set("0")
cal.mainloop()

