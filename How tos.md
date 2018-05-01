#add employees

To add an employee to the system, type the following command:
>>> add()

The system will prompt the user to enter the details of the employee. Once inputted, the system will generate a
unique password and the employee will be added to the database. The hourly rates for employees of certain age groups
are recorded in the system.
Note: Status refers to the job title of the employee (defaulted as employee upon creation).

Here is the function that defines the above:

>>> def add():
...     import string
...     import random
    
...     def password_generator(size=8, chars=string.ascii_uppercase + string.digits):
...         return ''.join(random.choice(chars) for i in range(size))
...     def username_generator(size=7, chars=string.digits):
...         return "E"+''.join(random.choice(chars) for i in range(size))

...     status = "Employee"
...     username = username_generator()
...     password = password_generator()
...     name = input('Enter the name: ')
...     while True:
...         try:
...             age = int(input('Enter the age: '))
...         except ValueError:
...             print("Invaild value.")
...             continue
...         else:
...             break
...     category = "A"
...     if age > 65:
...         category = "C"
...     if age < 25:
...         category = "H"
...     if age < 21:
...         category = "M"
...     if age < 16:
...         category = "X"
...     while True:
...         try:
...             phonenum = int(input('Enter the phone number: '))
...         except ValueError:
...             print("Invaild value.")
...             continue
...         else:
...             break

...     f = open("employee.txt","a+")
...     f.write(username + "-_-" + password + "-_-" + name + "-_-" + str(age) + "-_-0" + str(phonenum) + "-_-" + status + "-_-" + category + "\n")
...     f.close()
...     print("Added: " + name + "\n" + "Status: " + status + "\n" + "Log-in Username: " + username + "\n" + "Log-in Password: " + password)


#log in

To log in to the system, type the following:

>>> log_in()

The system will then prompt the user to input their name and password. If the details entered correspond to
any single employee's data already in the system, then that user will be logged in. The system will then record the
time that the user logged in. 

Using the function a second time will prompt the user to enter their details again. 
This will log the user out and cause the system to record the time again. When the payslip is calculated, it 
accumulates all hours recorded and the corresponding amount of money appears on the payslip.

Here is the function that defines the above:

>>>def login():
>>>    import datetime
    
>>>    username = input('Enter the username: ')
>>>    password = input('Enter the password: ')
>>>    log = ""
>>>    f1 = ""
>>>    with open("employee.txt") as f:
...        for line in f:
...            a,b,c,d,e,u,l = line.split("-_-")
...            l,p = l.split("\n")                
...            if (a == username and b == password):
...                t = datetime.datetime.now().strftime("%y-%m-%d-%H-%M")
>>>    f.close()
>>>    with open("log.txt") as r:
...        for line in r:
...            a1,b1,c1,d1,e1,f1 = line.split(",") 
...            f1,w = f1.split("\n")
...            if (a1 == a and b1 == c):
...                if f1 == "LogIn":
...                    log = "LogOut"
...                else:
...                    log = "LogIn"
>>>    g = open("log.txt","a+")
>>>    g.write(a + "," + c + "," + d + "," + l + "," + t + "," + log + "\n")
>>>    g.close()
>>>    if u == "Employee":
...        if log == "LogIn":
...            print("Employee Logged in.")
...        else:
...            print("Employee Logged out.")
>>>    else:
...        if log == "LogIn":
...            print("Logged in.")
...        else:
...            print("Logged out.")





#view all employees


Here is how to view all the employees' data together:

>>> view()

This will list the attributes associated to every employee in the system.

Here is the function that defines the above:

>>>def view():
>>>    with open("employee.txt") as f:
...    for line in f:
...        z,x,c,v,b,n,m = line.split("-_-")
...        print("\n" + "Name: " + c + "\n" + 
...                 "Username: " + z + "\n" +
...                 "Password: " + x + "\n" +
...                 "Age: " + v + "\n" +
...                 "Phone Number: " + b + "\n" +
...                 "Status: " + n + "\n" +
...                 "Category: " + m + "\n")




#edit details

To edit the details of any existing employee, type the following command:

>>> edit()

This will prompt the user to enter their login details in order to edit information already stored in the 
system. 

Here is the function that defines the above:

def edit():

>>>    username = input('Enter the username: ')
>>>    password = input('Enter the password: ')
>>>    search = username + "-_-" + password
>>>    new_name = input('Please leave blank if you want to keep any of the information the same.' + "\n" + 'Enter the new name: ')
>>>    new_age = input('Enter the new age: ')
>>>    new_phonenum = input('Enter the new phone number: ')
>>>    new_status = input('Enter the new status: ')
>>>    new_category = input('Enter the new category: ')
>>>    with open("employee.txt") as f:
...        for line in f:                
...            if search in line:
...                n = line
...                uname,passwords,name,age,num,sta,cate = n.split("-_-")
...                if new_name == "":
...                    new_name = name
...                if new_age == "":
...                    new_age = age
...                if new_phonenum == "":
...                    new_phonenum = num
...                if new_status == "":
...                    new_status = sta
...                if new_category == "":
...                    new_category = cate
>>>    f.close()
 
>>>    with open("employee.txt","r+") as f:
...        new_f = f.readlines()
...        f.seek(0)        
...        for line in new_f:
...            if search not in line:
...                f.write(line)
...            if search in line:
...                f.write(uname + "-_-" + passwords + "-_-" + new_name + "-_-" + new_age + "-_-" + new_phonenum + "-_-" + new_status + "-_-" + new_category + "\n")
...        f.truncate()



#payslip

Here is how to generate a payslip to later be printed; type:

pay()

The system then prompts you to enter the username and password of the employee before continuing. Once the details
are entered, the payslip is created in an excel file.
Note 1: Our system creates a file that must be opened externally (using Microsoft Excel) that can then be saved and 
printed on any computer.
Note 2: Income taxes based on wages and national insurance are accumulated. The payslip deducts the tax and provides
a net income.



>>>def pay():
...    from re import sub
...    from decimal import Decimal
...    import pandas as pd
...    import datetime

...    l = []
...    n = input('Enter the username of the person that you want pay: ')
...    with open("log.txt") as f:
...        for line in f:
...            if n in line:
...                l.append(line)
...            if len(l) == 2:
...                d1,d2,d3,d4,d5,d6,d7,d8,d9,d10,d11,d12 = str(l).split(",")
...                y1,m1,dt1,h1,s1 = d5.split("-")
...                y2,m2,dt2,h2,s2 = d11.split("-")
...                if int(y1) == int(y2):
...                    if int(m1) == int(m2):
...                        if int(dt1) == int(dt2):
...                            hr1 = int(h1)
...                            hr2 = int(h2)
...                            hr = hr2 - hr1
...                            if int(d3) >= 25:
...                                with open("payrates.txt") as f:
...                                    for line in f:
...                                        if "25" in line:
...                                            a,b = line.split(",")
...                            if int(d3) >= 21:
...                                with open("payrates.txt") as f:
...                                    for line in f:
...                                        if "21" in line:
...                                            a,b = line.split(",")
...                            if int(d3) >= 18:
...                                with open("payrates.txt") as f:
...                                    for line in f:
...                                        if "18" in line:
...                                            a,b = line.split(",")
...                            if int(d3) < 18:
...                                with open("payrates.txt") as f:
...                                    for line in f:
...                                        if "U18" in line:
...                                            a,b = line.split(",")
...                            if d3 == "APP":
...                                with open("payrates.txt") as f:
...                                    for line in f:
...                                        if "APP" in line:
...                                            a,b = line.split(",")
...                            b = ''.join(b.split("\n"))
...                            pay = Decimal(b)*hr
...                            NatI = 0
...                            if d4 == "A":
...                                NI1 = 0.12
...                                NI2 = 0.2
...                            if d4 == "B":
...                                NI1 = 0.0585
...                                NI2 = 0.2
...                            if d4 == "C":
...                                NI1 = 0
...                                NI2 = 0
...                            if d4 == "H":
...                                NI1 = 0.12
...                                NI2 = 0.2
...                            if d4 == "J":
...                                NI1 = 0.2
...                                NI2 = 0.2
...                            if d4 == "M":
...                                NI1 = 0.12
...                                NI2 = 0.2
...                            if d4 == "X":
...                                NI1 = 0
...                                NI2 = 0
...                            if d4 == "Z":
...                                NI1 = 0.2
...                                NI2 = 0.2
...                            if pay > 40.5:
...                                NatI = pay*NI1
...                            if pay > 223:
...                                NatI = pay*NI2
...                            tax = float(pay)*0.2
...                            net = float(pay) - (tax + NatI)
...                            w = pd.Series([d2, d3, d4, hr, dt1+"/"+m1+"/"+y1,b, float(pay),tax,NatI,net], index=["Name","Age","National Insurance Category","Number of Hours Worked","Date","Pay Rate(based on age)","Gross Pay","Income Tax","National Insurance","Net Pay"])
...                            w.to_excel(n + datetime.datetime.now().strftime("%y-%m-%d-%H-%M") + '.xlsx',  sheet_name='Sheet1')
...                            print(w)


#delete user

To delete a particular user from the system, type:

>>> delete()

Then the system will ask you to enter your username and password of the user you wish to delete.
Note: The passwords for every employee is listed in the view section.

>>>def delete():

>>>    username = input('Enter the username: ')
>>>    password = input('Enter the password: ')
>>>    search = username + "-_-" + password
>>>    with open("employee.txt") as f:
...        for line in f:                
...            if search in line:
...                n = line
>>>    f.close()

>>>    with open("employee.txt","r+") as f:
...        new_f = f.readlines()
...        f.seek(0)
...        for line in new_f:
...            if n not in line:
...                f.write(line)
...            else:
...                print("Removed:" + line)
...        f.truncate()





