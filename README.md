# JOALPay
JOALPay is a library created with the programming language Python that calculates pay of employees for small businesses. Strings of characters and values are randomly created that correspond to usernames and passwords for individual employees using the "add" function. Employees can then log in and out of the system (log in when employee begins working; log out when employee finishes working) and record the number of hours worked by each employee logged in. Once required, the employer can use the "pay" function to calculate the pay of individual employees. The calculated pay takes into account average taxes (national insurance and income tax according to age) and deducts them from each employees' final pay.

## Installation
### 1. Firstly, you will need Anaconda to run the code. 
https://www.anaconda.com/download/
Once downloaded, run the installer and open the Anaconda Navigator. Launch Jupyter Notebook. Then, select New, followed by Python 3 notebook. From this notebook, you will be able to run all the code used in the system. <br/>
Note: The Jupyter Notebook can run Python code even without access to the internet. <br/>
### 2. Secondly, you will need to install our library.
Download the JOALPay files and extract the folder to wherever you wish. Open the Anaconda prompt (find it using the search tool on your computer) and redirect the prompt to the JOALPay folder using: <br/>
```
>>> cd *insert address of folder here* 
```
Now type into the prompt:
```
>>> python Setup.py develop 
```
After this point, the library will be successsfully implemented into your device and you can open the Jupyter Notebook to use the code.
### 3. You may want to view the [tutorial](https://github.com/JOAL2018/JOALPay/blob/master/Tutorial.md) or the howtos file located within the docs folder of the library. This will provide a detailed description of how to use our library.

