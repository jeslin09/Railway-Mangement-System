from tkinter import *
from tkinter import messagebox
from tkinter import ttk
import mysql.connector

root=Tk()
root.geometry("300x150")
root.title("Login Form")

mid=StringVar()
mpwd=StringVar()
mtno=StringVar()
mtname=StringVar()
msre=StringVar()    
mdest=StringVar()  
mdept=StringVar()   
marrt=StringVar()
mfacs=IntVar()
msacs=IntVar()
mtacs=IntVar()
msls=IntVar()
mfacf=IntVar()
msacf=IntVar()
mtacf=IntVar()
mscf=IntVar()
def save():

   TNo=E1.get()
   TrainName=E2.get()
   source=E3.get()
   destination=E4.get()
   departureTime=E5.get()
   arrTime=E6.get()
   FACS=E7.get()
   SACS=E8.get()
   TACS=E9.get()
   SLS=E10.get()
   FACF=E11.get()
   SACF=E12.get()
   TACF=E13.get()
   SFS=E14.get()
   
   con=mysql.connector.connect(host="localhost",user="root",passwd="jeslin123",database='railways')
   mycur=con.cursor()
   mycur.execute("insert into trains values('%s','%s','%s','%s','%s','%s',%s,%s,%s,%s,%s,%s,%s,%s)" % (TNo,TrainName,source,destination,departureTime,arrTime,FACS,SACS,TACS,SLS,FACF,SACF,TACF,SFS))
   con.commit()
   messagebox.showinfo("information","Record Added")

def store():
   

   global E1,E2,E3,E4,E5,E6,E6,E7,E8,E9,E10,E11,E12,E13,E14
   new=Tk()
   new.geometry("600x600")
   new.title("TICKET RESERVATION")
   lblt=Label(new,text="add train info",fg="yellow",bg="grey",font="Tahoma")
   lblt.place(x=100,y=10)

   lbl1=Label(new,text="Train number")
   lbl1.place(x=50,y=50)
   E1=Entry(new,textvar=mtno)
   E1.place(x=180,y=50)

   lbl2=Label(new,text="Train name")
   lbl2.place(x=50,y=70)
   E2=Entry(new,textvar=mtname)
   E2.place(x=180,y=70)

   lbl3=Label(new,text="Source")
   lbl3.place(x=50,y=90)
   E3=Entry(new,textvar=msre)
   E3.place(x=180,y=90)

   lbl4=Label(new,text="Destination")
   lbl4.place(x=50,y=110)
   E4=Entry(new,textvar=mdest)
   E4.place(x=180,y=110)

   lbl5=Label(new,text="Departure time")
   lbl5.place(x=50,y=130)
   E5=Entry(new,textvar=mdept)
   E5.place(x=180,y=130)

   lbl6=Label(new,text="Arrival time")
   lbl6.place(x=50,y=150)
   E6=Entry(new,textvar=marrt)
   E6.place(x=180,y=150)

   lbl7=Label(new,text="First class AC seats")
   lbl7.place(x=50,y=170)
   E7=Entry(new, textvar=mfacs)
   E7.place(x=180,y=170)

   lbl8=Label(new,text="Second class AC seats")
   lbl8.place(x=50,y=190)
   E8=Entry(new, textvar=msacs)
   E8.place(x=180,y=190)

   lbl9=Label(new,text="Third class AC seats")
   lbl9.place(x=50,y=210)
   E9=Entry(new,textvar=mtacs)
   E9.place(x=180,y=210)

   lbl10=Label(new,text="Sleeper seats")
   lbl10.place(x=50,y=230)
   E10=Entry(new,textvar=msls)
   E10.place(x=180,y=230)

   lbl11=Label(new,text="First class AC fare")
   lbl11.place(x=50,y=250)
   E11=Entry(new,textvar=mfacf)
   E11.place(x=180,y=250)

   lbl12=Label(new,text="Second class AC fare")
   lbl12.place(x=50,y=270)
   E12=Entry(new,textvar=msacf)
   E12.place(x=180,y=270)

   lbl13=Label(new,text="Third class AC fare")
   lbl13.place(x=50,y=290)
   E13=Entry(new,textvar=mtacf)
   E13.place(x=180,y=290)

   lbl14=Label(new,text="Sleeper class fare")
   lbl14.place(x=50,y=310)
   E14=Entry(new,textvar=mscf)
   E14.place(x=180,y=310)

   B2=Button(new,text="Save",command=save)
   B2.place(x=100,y=560)
   
def update():
    tno=E1.get()
    tname=E2.get()
    source=E3.get()
    destination=E4.get()
    departureTime=E5.get()
    arrTime=E6.get()
    FACS=E7.get()
    SACS=E8.get()
    TACS=E9.get()
    SLS=E10.get()
    FACF=E11.get()
    SACF=E12.get()
    TACF=E13.get()
    SFS=E14.get()
    con=mysql.connector.connect(host="localhost",user="root",passwd="jeslin123",database='railways')
    mycur=con.cursor()
    mycur.execute("update trains set TrainName='%s',source='%s',destination='%s',departureTime='%s',ArrTime='%s',FACS=%s,SACS=%s,TACS=%s,SLS=%s,FACF=%s,SACF=%s,TACF=%s,SCF=%s where TNo='%s'" % (tname,source,destination,departureTime,arrTime,FACS,SACS,TACS,SLS,FACF,SACF,TACF,SFS,tno))
    con.commit()
    messagebox.showinfo("updated")

def modifyInfo():
   global E1,E2,E3,E4,E5,E6,E7,E8,E9,E10,E11,E12,E13,E14
   
   new=Tk()
   new.geometry("600x600")
   new.title("Train Info")
   lblt=Label(new,text="Modify Train Info",fg="yellow",bg="grey",font="Tahoma")
   lblt.place(x=100,y=10)

   lbl1=Label(new,text="Train No.")
   lbl1.place(x=50,y=50)
   E1=Entry(new,textvar=mtno)
   E1.place(x=180,y=50)

   lbl2=Label(new,text="Train name")
   lbl2.place(x=50,y=70)
   E2=Entry(new,textvar=mtname)
   E2.place(x=180,y=70)

   lbl3=Label(new,text="Source")
   lbl3.place(x=50,y=90)
   E3=Entry(new,textvar=msre)
   E3.place(x=180,y=90)

   lbl4=Label(new,text="Destination")
   lbl4.place(x=50,y=110)
   E4=Entry(new,textvar=mdest)
   E4.place(x=180,y=110)

   lbl5=Label(new,text="Departure time")
   lbl5.place(x=50,y=130)
   E5=Entry(new,textvar=mdept)
   E5.place(x=180,y=130)

   lbl6=Label(new,text="Arrival time")
   lbl6.place(x=50,y=150)
   E6=Entry(new,textvar=marrt)
   E6.place(x=180,y=150)

   lbl7=Label(new,text="First class AC seats")
   lbl7.place(x=50,y=170)
   E7=Entry(new, textvar=mfacs)
   E7.place(x=180,y=170)

   lbl8=Label(new,text="Second class AC seats")
   lbl8.place(x=50,y=190)
   E8=Entry(new, textvar=msacs)
   E8.place(x=180,y=190)

   lbl9=Label(new,text="Third class AC seats")
   lbl9.place(x=50,y=210)
   E9=Entry(new,textvar=mtacs)
   E9.place(x=180,y=210)

   lbl10=Label(new,text="Sleeper seats")
   lbl10.place(x=50,y=230)
   E10=Entry(new,textvar=msls)
   E10.place(x=180,y=230)

   lbl11=Label(new,text="First class AC fare")
   lbl11.place(x=50,y=250)
   E11=Entry(new,textvar=mfacf)
   E11.place(x=180,y=250)

   lbl12=Label(new,text="Second class AC fare")
   lbl12.place(x=50,y=270)
   E12=Entry(new,textvar=msacf)
   E12.place(x=180,y=270)

   lbl13=Label(new,text="Third class AC fare")
   lbl13.place(x=50,y=290)
   E13=Entry(new,textvar=mtacf)
   E13.place(x=180,y=290)

   lbl14=Label(new,text="Sleeper class fare")
   lbl14.place(x=50,y=310)
   E14=Entry(new,textvar=mscf)
   E14.place(x=180,y=310)

    
   B1=Button(new,text="Modify",command=update)
   B1.place(x=100,y=390)         



def disp():
   con=mysql.connector.connect(host="localhost",user="root",passwd="jeslin123",database='railways')
   mycur=con.cursor()
   mycur.execute("Select * from trains")
   data=mycur.fetchall()
   root=Tk()
   tree = ttk.Treeview(root, column=("c1", "c2", "c3","c4","c5","c6"), show='headings')

   tree.column("#1", anchor=CENTER)

   tree.heading("#1", text="TnO")
   tree.column("#2", anchor=CENTER)
   tree.heading("#2", text="TrainName")
   tree.column("#3", anchor=CENTER)
   tree.heading("#3", text="Source")
   tree.column("#4", anchor=CENTER)
   tree.heading("#4", text="Destination")
   tree.column("#5", anchor=CENTER)
   tree.heading("#5", text="departureTime")
   tree.column("#6", anchor=CENTER)
   tree.heading("#6", text="arrTime")
 
  
   tree.pack()
   for row in data:
      tree.insert("", END, values=row)

def delete_info():
   tno=E1.get()
   
   con=mysql.connector.connect(host="localhost",user="root",passwd="jeslin123",database='railways')
   mycur=con.cursor()
   mycur.execute("delete from trains where TNo=('%s')" %(tno))
   con.commit()
   messagebox.showinfo("information","information deleted")
def deltin():
   global E1
   
   new=Tk()
   new.geometry("300x300")
   new.title("delete train information")
   lblt=Label(new,text="delete info",fg="yellow",bg="grey",font="Tahoma")
   lblt.place(x=100,y=10)

   lbl1=Label(new,text="Train No.")
   lbl1.place(x=50,y=50)
   E1=Entry(new,textvar=mtno)
   E1.place(x=150,y=50)

      

   B1=Button(new,text="delete",command=delete_info)
   B1.place(x=100,y=150)


    



   
def check():
   con=mysql.connector.connect(host="localhost",user="root",passwd="jeslin123",database='railways')
   mycur=con.cursor()
   
   mycur.execute("Select * from login")
   data=mycur.fetchone()
   if data[0]==mid.get() and data[1]==mpwd.get():
      messagebox.showinfo("information","Correct Password")
      root.destroy()
      main=Tk()
      main.geometry("300x300")
      main.title("Main Menu")
      B1=Button(main,text="Add trains",command=store)
      B1.place(x=100,y=70)
      B2=Button(main,text="Modify info",command=modifyInfo)
      B2.place(x=100,y=110)
      B3=Button(main,text="Display train info",command=disp)
      B3.place(x=100,y=150)
      B4=Button(main,text="Delete info",command=deltin)
      B4.place(x=100,y=190)
      
      
   else:
       messagebox.showerror("information","InCorrect Password")

   

lblt=Label(root,text="LOGIN FORM",fg="yellow",bg="grey",font="Tahoma")
lblt.place(x=100,y=10)

lbl1=Label(root,text="ID")
lbl1.place(x=50,y=50)
E1=Entry(root,textvar=mid)
E1.place(x=150,y=50)

lbl2=Label(root,text="Password")
lbl2.place(x=50,y=70)
E2=Entry(root,textvar=mpwd)
E2.place(x=150,y=70)

B1=Button(root,text="Login",command=check)
B1.place(x=100,y=120)



