# Here is a full working example of the system running
### First import the JOAL library
```python
>>> import JOAL as j
JOAL IMPORTED
```
### Next you will need some employees
To add the employees information use the add() function
```python
>>> j.add()
Enter the name:
```
Now it has asked the user to enter the name of the employee so
enter an employee's name into the text box<br/>
For instance :
```python
>>> Jeff
Enter the age:
```
Now enter their age in the same way
```python
>>> 18
Enter the phone number:
```
Finally, enter their phone number
```python
>>> 01234567890
Added: Jeff
Status: Employee
Log-in Username: E4021512
Log-in Password: YQ85VZCZ
```
Looking at the output, a new employee has been created<br/>
Note the Username and Password as they are needed by the employee to login for work
### Now you can view this employee's information as well as anyone else you add 
To view the information on all of your employees, use the view() function<br/>
For example :
```python
>>> j.view()

Name: Jeff
Username: E4021512
Password: YQ85VZCZ
Age: 18
Phone Number: 01234567890
Status: Employee
Category: M
```
### Changing some of an employee's details
Jeff may change his phone number or name<br/>
Therefore you will want to update that information which can be done using the edit() function
```python
>>> j.edit()
Enter the username:
```
Here, you need to enter the username of the employee you want to edit<br/>
In this case it's 'Jeff"<br/>
Remember when Jeff was first added to the system, a username was generated<br/>
Enter this username :
```python
>>> E4021512
Enter the password:
```
Now enter the employee's password :
```python
>>> YQ85VZCZ
Please leave blank if you want to keep any of the information the same.
Enter the new name:
```
In the case of Jeff changing his phone number and nothing else, leave each field blank to make no changes<br/>
Since Jeff's name is not changing, leave this blank (press enter)<br/>
Do this until you are asked about the thing you want to edit
```python
>>> 
Enter the new age: 
>>> 
Enter the new phone number:
```
Now, you can enter the new phone number for the employee :
```python
>>> 08888888888
Enter the new status:
>>> 
Enter the new category:
>>>
```
(Note that you can also change the employee's status and National Insurance category)
The phone number has now been updated<br/>
You can check this using the view() function :
```python
>>> j.view()

Name: Jeff
Username: E4021512
Password: YQ85VZCZ
Age: 18
Phone Number: 08888888888
Status: Employee
Category: M
```
You can see that the changed information has been updated  
### Logging in for work
Once an employee's account has been made on the system they can login at the start of their shift and logout when they finish
For example, if Jeff had a 6 hour shift from 10am until 4pm then first at 10am Jeff would login using the login() function and their username & password :
```python
>>> j.login()
Enter the username:
>>> E4021512
Enter the password:
>>> YQ85VZCZ
Employee Logged in.
```
Now this employee is logged in<br/>
When Jeff finishes working at 4pm he can use the same function to logout :
```python
>>> j.login()
Enter the username:
>>> E4021512
Enter the password:
>>> YQ85VZCZ
Employee Logged out.
```
Now the time between logging in and out has been logged on the system so that the amount the employee should be payed can be calculated
### Paying an employee
To pay an employee, the pay() function is used<br/>
```python
>>> j.pay()
Enter the username of the person that you want pay:
```
In this example, Jeff can be paid (for the 4 hours he had worked) so you enter Jeff's username :
```python
>>> E4021512

Name                               Jeff
Age                                  18
National Insurance Category           M
Number of Hours Worked                6
Date                           02/05/18
Pay Rate(based on age)              5.9
Gross Pay                          35.4
Income Tax                         7.08
National Insurance                    0
Net Pay                           28.32
dtype: object
```
Now, you can see that Jeff should be paid a total of £28.32<br/>
##### Modifying amount to pay employees
# (WE WILL ADD A CUSTOM PAY OPTION)
If you think an employee should be taxed less or more, or paid differently then you can change this<br/>
Using the edit() function, you can change their 'National Insurance Category'<br/>
The payrates default to the minimum wage for an employee's age group, but you can change them to pay more than required if you have access to the code<br/>
You will have to modify the code in the file '__init__.py'<br/>
This is what the code looks like within this file : 
```python
from .addemployee import add
from .payemployee import pay
from .reademployee import login
from .deleteemployee import delete
from .editemployee import edit
from .viewemployee import view

with open("log.txt", "a+") as f:
    log = f.read() 
    f.write(log)

with open("employee.txt", "a+") as f:
    emp = f.read()
    f.write(emp)

with open("payrates.txt", "w") as f:
    f.write("25,7.83\n21,7.38\n18,5.9\nU18,4.2\nAPP,3.7")

print("JOAL IMPORTED")
```
The relevant part is :
```python
f.write("25,7.83\n21,7.38\n18,5.9\nU18,4.2\nAPP,3.7")
```
This contains the information for the payrates of each age group<br/>

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

### Deleting an employee's information
To remove an employee from the system use the delete() function<br/>
To delete Jeff in this example :
```python
>>> j.delete()
Enter the username: 
>>> E4021512
Enter the password:
>>> YQ85VZCZ
Removed:E4021512-_-YQ85VZCZ-_-Jeff-_-18-_-08888888888-_-Employee-_-M
```
Just enter their username and then password when prompted and the employee will no longer be on the system<br/>
To check they are gone use : 
```python
j.view()
```
If the information about the person you have tried to delete does not appear, then the removal was sucessful<br/>
In this example there is no output as Jeff was the only employee<br/>
