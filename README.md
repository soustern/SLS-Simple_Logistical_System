# SLS - Simple Logistical System

## Video Demo:  https://www.youtube.com/watch?v=pSxkruwjchE

## Description: 

A simple logistical system that has the ability to create, edit, show, search (with multiple criteria) and remove items of three possible categories. It also has the capability to create and showcase useful reports, having fully implemented account features (login, creation and removal) as well as a complete a intuitive manual and various security/quality of life implementations. The user can control usage by having access to two different types of accounts, limited (Only vizualization) and admin (all features).

SLS puts great enphasis in user friendly design, best practices, security and control. This allows a very gentle leraning curve and the possibility of hierarquy in its usage.

Made entirely in C.

# DOCUMENTATION

## FILES 

A one by one analisis of all the files present at the project.

## functions.h

This is the header file. Serving the purpose of making possible the componentization of functions, structs, etc. to be used throughout SLS, functions.h contains all function promisses, constant values and the following structs:

+ createaccount
+ account
+ createemployee
+ employee
+ createproduct
+ product 
+ createdealer
+ dealer

## functions_admin.c

This files contains all functions associated to functionalities present at accounts of "admin" type. Here we can find an assortment of global variables and data tables of all struct data types (hashtables).

###### int count_numerical_quantity_employee()

This function traverses an hash table wich has all employees (present at database) loaded. For every employee found, an increment variable goes up one. At last, the function returns the resulting integer.

###### int count_numerical_quantity_product()

This function traverses an hash table wich has all products (present at database) loaded. For every product found, an increment variable goes up one. At last, the function returns the resulting integer.

###### int count_numerical_quantity_dealer()

This function traverses an hash table wich has all dealers (present at database) loaded. For every dealer found, an increment variable goes up one. At last, the function returns the resulting integer.

###### float calculate_total_money_amount_employee()

This function converts all information present at the database regarding employee salaries from string to float (using atoi() function). It, them, calculates the total value of all salaries combined with a addition operation.

###### float calculate_medium_money_amount_employee()

This function returns the returned valor of count_numerical_quantity_employee divided by the returned valor of calculate_total_money_amount_employee. The result is a medium of all salaries.

###### float calculate_total_money_amount_product()

This function converts all information present at the database regarding products total value from string to float (using atoi() function). It, them, calculates the total value of all products combined with a addition operation.

###### float calculate_medium_money_amount_product()

This function returns the returned valor of count_numerical_quantity_product divided by the returned valor of calculate_total_money_amount_product. The result is a medium of all total values.

###### float count_item_total()

Returns the total quantity of all items present at database. (all total amount added to each other)

###### void signup_admin()

This function loads the accounts database receives user input for username and password, deals with all validations (Username doesnt already exists, password confirmation is equal to first input, etc.) and stores all received values in a storage struct of type "createaccount". At the end, it calls the save_account_admin() and passes the createaccount storage to store at account database a newly created admin account.
All allocated memory is freed in the end and the database is closed.

###### void signup_limited()

This function loads the accounts database receives user input for username and password, deals with all validations (Username doesnt already exists, password confirmation is equal to first input, etc.) and stores all received values in a storage struct of type "createaccount". At the end, it calls the save_account_limited() and passes the createaccount storage to store at account database a newly created limited account.
All allocated memory is freed in the end and the database is closed.

###### void save_account_admin(createaccount account)

This function declares a pointer o type FILE, opens the correct database and goes over a fprintf() to store at the database the passed "account" values. It, then, closes the opened file. The "admin" identifier is the last stored value.

###### void save_account_limited(createaccount account)

This function declares a pointer o type FILE, opens the correct database and goes over a fprintf() to store at the database the passed "account" values. It, then, closes the opened file. The "limited" identifier is the last stored value.

###### void menu_admin()

This functions prints at the screen all avaible tools for an admin account. At the end it call answe_admin() function

###### void answer_admin()

Establishes a switch case conditional to route to the various tools avaible for an admin account. It does so receiving a char using scanf(). The received char is treated vi a tolower() call on it.
The default switch case scenario is tha of an invalid answer.

###### void menu_register_item()

Prints at screen all option avaible inside the "create item" tool. It also calls answer_register_item() at the end.

###### void answer_register_item()

Using a switch case condition, routes the answer to the appropriate function. This is possible doe to the enphasis on componentization, wich made possible a high amount of flexibility. It is also necessary do to the presence of three different types of item, each with its own struct ad associated database.

###### void menu_remove_item()

Prints at screen all option avaible inside the "remove item" tool. It also calls answer_remove_item() at the end.

###### void answer_remove_item()

Using a switch case condition, routes the answer to the appropriate function. This is possible doe to the enphasis on componentization, wich made possible a high amount of flexibility. It is also necessary do to the presence of three different types of item, each with its own struct ad associated database.

###### void menu_edit_item()

Prints at screen all option avaible inside the "edit item" tool. It also calls answer_edit_item() at the end.

###### void answer_edit_item()

Using a switch case condition, routes the answer to the appropriate function. This is possible doe to the enphasis on componentization, wich made possible a high amount of flexibility. It is also necessary do to the presence of three different types of item, each with its own struct ad associated database.

###### void menu_signup_account()

This function prints at the screen the three possible routes one may take when using the "create account" tool.
The options are: 

+ 1 - Create an "ADMIN" account
+ 2 - Create and "LIMITED" account
+ 3 - Know more (This one printes at screen the appropriate manual section to curb any confusion and/or possible mistake)

At the end, "answer_signuP_account" function is called.

###### void menu_signup_account()

This function receives an answer a routes to the appropriate function. The default switch case value is "invalid option".

###### void remove_account_menu_and_answer()

As the name suggests, this function acts as the "menu" (content printed on-screen) and "answer" (responsible to receive an answer and route to the appropriate function) for the "remove account" tool. It, at first, print useful information on-screen, wich reads as follows:

> So that it is possible to remove an account, You will need to enter its username. Once an account is successfully deleted, It will not be possible to retrieve it. It is impossible to delete the account that is currently being used.

It, then, prompts the user to either continue or go back. When continued, a do while loop is triggered and goes on for the amount of times "check_if_user_account(answer)" and "remove_account(answer" returns false.
The loop may break if the estipulated maximum ammount of tries is reached (A countdown at the screen lets the user know how many tries they have left).If the loop is exited by that mean, a message is printed on-screen making the user aware of what happened.
If the account is successfully removed, a message is printed saying so and the user is prompted to call the "menu_admin" function.

###### void sigunp_employee()

This function, at firstm declares a new struct variable of type "createemployee". After that, the user is propted to tell all the associated information and stores everything in the previously declared variable.
At the end, the "save_employee" function is called with the values of the varible being passed to it.
A lot of caution is taken to remove any trailing newline  (\n) character remaining. The strcspn function is used to achieve this level of optimization.

###### void save_employee(createemployee employee)

This function declares a pointer o type FILE, opens the correct database and goes over a fprintf() to store at the database the passed "employee" values. It, then, closes the opened file.

###### void show_employee_database_all()

This function load the employee database (using the load_employee_databases() function) and navigates the hashtable (vertically and horizontally) printing every existing employee in a formated and organized manner. The objective of this function is to print all existing employees.
A increment functionality exists to showcase at screen at waht position said employee was printed (for organizational reasons).
At the end, the database is unloaded (using thew unload_employee_database() function).

###### load_employee_database()

This function has the important task of reading all data present at the employee database file, storing is data in a buffer (using fgets()) and coping the buffer content to the correct place in node pointer of type "employee" (strcpy function is used to achieve this).
At the end, all opened files are closed and all allocated is freed. The function returns true if no "return false" condition is met (normally this may happen at the moment a file is opened or a chunck of memory is allocated.

###### show_employee_database_detailed()

This function is responsible for powering the search functionality. I takes a chosen and specific to employee data type criteria and navigates the correct hashtable. Using strcasecmp(), any found match of information and user input is printed on-screen.
 
###### remove_employee()
 
This function receives user input and search the correct hashtable, removing the associated item if a match occurs. 
It is responsiBle for rearanging the hashtable as well overwriting the database file to store the now modified data (A for loop going around MINTABLESIZE times is used to achieve this).
To achive this, the database file is opened at first with a write ("w") mode (This is necessary for the content of the file to be erased), setlinebuf() is called on the file to make sure it is line buffered (This makes it so we can write onto the file while the program is runnin. Otherwise, we would have to wait until the program is closed).
The file is, then, closed an reopened again in append ("a") mode (This makes sure information is not overwriten but appears one after the other).

###### edit_employee()




 














  
 




