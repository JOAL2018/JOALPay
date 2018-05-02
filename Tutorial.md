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



```
If you need to change something later such as their phone number 

