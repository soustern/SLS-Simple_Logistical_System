# SLS - Simple Logistical System 1.0

## Video Demo:  https://www.youtube.com/watch?v=pSxkruwjchE

## Description: 

A simple logistical system that has the ability to create, edit, show, search (with multiple criteria) and remove items of three possible categories. It also has the capability to create and showcase useful reports, having fully implemented account features (login, creation and removal) as well as a complete a intuitive manual and various security/quality of life implementations. The user can control usage by having access to two different types of accounts, limited (Only vizualization) and admin (all features).

SLS puts great enphasis in user friendly design, best practices, security and control. This allows a very gentle leraning curve and the possibility of hierarchy in its usage.

Made entirely in C language.

## What can be found in this README:

This README goes trough a comprehensible transcript of the program manual, serving as a great "how to use" guide.

It, then, delves into a feature rich documentation wich details and explains in depth each file, function and choice made during the creation of SLS.

# MANUAL: HOW TO USE

The following content is a compilation of transcripts taken from the official SLS manual.

## ACCOUNTS

In SLS version 1.0, there are two types of accounts. 


###### Admin

These accounts have full access to SLS features. 

Accounts with this profile are able to add new items to the system as well as view, edit and delete them.

It is only possible to register new accounts to the system with the features of an admin account.

###### Limited

These accounts have access only to the tools for viewing, searching items and reports.

You can access the manual with both account types.

## FIRST STEPS

If this is the first time you are using the system, the current loged account is of "ADMIN" type.

This means all system functionalities are currently available.
The first Step is adding a new item.

SLS 1.0 has three different 'modalities' of items that can be registered:

+ 1 - PRODUCT
+ 2 - PROVIDER
+ 3 - EMPLOYEE

## ITEM MODALITIES

###### Products

Items in the 'PRODUCT' format have the following categories:

**Name:** A generic name assigned to the product.

**Quantity:** Generic assignment to the quantity of the product
referring to the criterion used to measure it.
It is possible that the quantity refers to a unit value
or a value in meters, centimeters, etc.
In any case, you must assign only an integer
and not say anything else.
Correct: 2 | Wrong: 2cm

**Unit value:** Specification of how much each unit of the product is worth.
This information must comply with the metric criteria that is used
in particular for different types of products.
Ex: If I inform you that the unit value of a copper wire is 2.00
I will be informing you that they are 2.00 every 10 cm.

**Total value:** Product of multiplying the quantity and unit value of the product.

###### Providers

Items in the 'SUPPLIER' format have the following categories:

**Name:** A generic name assigned to the product.

**Owner name:** Name of the person who is responsible for
communication and/or intermediation at the time of contact.

**City:** Where the supplier is located.

**Type of service:** Generic assignment to the type of service that"
that that supplier offers.
Ex: Builder, Electrician, Construction materials and etc.

**Contact:** Supplier contact number."

**Email:** Supplier contact email.

###### Employees

Items in the 'EMPLOYEE' format have the following categories:

**Name:** Name of the employee.

**Position:** Position/Area of activity of the employee.

**Salary:** Employee's salary amount.
Real numbers must represent the places after the comma separated
by the character '.'

**Hire Date:** Date when the employee was hired/hired.

## CREATING AN ITEM

To register an item just type the key '1
and press ENTER.

From this moment on, the following options will appear on the screen:

+ 1 - Register PRODUCT
+ 2 - Register SUPPLIER
+ 3 - Register EMPLOYEE

By typing the number referring to the type of item that must be registered"
and press ENTER, a new screen will appear and will ask to be typed"
the information referring to the specified category."
Ex: City: (The user must type the city referring to that item).

## VIEWING AN ITEM

To view an item, simply type the number referring to the 'View Item' tool"
and press ENTER.

From this moment on, the following options will appear on the screen:

+ 1 - View PRODUCT
+ 2 - View SUPPLIER
+ 3 - View EMPLOYEE

By typing the number referring to the product modality that must be registered
and press ENTER, a new screen will appear and will ask to be selected
a visualization mode.

In SLS 1.0, you can select two views:

**View all:** In this mode, the program will display all items on the screen"
of that modality present in the respective database"
without any specific sequence.

**Search:** In this mode, it will be possible to select a list of options,
specific to the selected item modality, and enter a related search
that criterion that will return one or more items
(A specific message will be displayed if no item is found in the search).

# DOCUMENTATION

Extensive and complete documentation.

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

As a mean of achieving componentization, all function are named following previsible naming conventions consistently throughout the file.

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

###### EMPLOYEE functions XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

###### void sigunp_employee()

This function, at first, declares a new struct variable of type "createemployee". After that, the user is propted to tell all the associated information and stores everything in the previously declared variable.

At the end, the "save_employee" function is called with the values of the varible being passed to it.

A lot of caution is taken to remove any trailing newline (\n) character remaining. The strcspn function is used to achieve this level of optimization.

###### void save_employee(createemployee employee)

This function declares a pointer o type FILE, opens the correct database and goes over a fprintf() to store at the database the passed "employee" values. It, then, closes the opened file.

###### void show_employee_database_all()

This function load the employee database (using the load_employee_databases() function) and navigates the hashtable (vertically and horizontally) printing every existing employee in a formated and organized manner. The objective of this function is to print all existing employees.

A increment functionality exists to showcase at screen at waht position said employee was printed (for organizational reasons).
At the end, the database is unloaded (using thew unload_employee_database() function).

###### bool load_employee_databases()

This function has the important task of reading all data present at the employee database file, storing is data in a buffer (using fgets()) and coping the buffer content to the correct place in node pointer of type "employee" (strcpy function is used to achieve this).

At the end, all opened files are closed and all allocated is freed. The function returns true if no "return false" condition is met (normally this may happen at the moment a file is opened or a chunck of memory is allocated.

###### bool unload_employee_databases()

Navigates the hash table properly freeing its content.

###### void show_employee_database_detailed()

This function is responsible for powering the search functionality. It takes a chosen and specific to employee data type criteria and navigates the correct hashtable. Using strcasecmp(), any found match of information and user input is printed on-screen.
 
###### void remove_employee()
 
This function receives user input and search the correct hashtable, removing the associated item if a match occurs. 

It is responsiBle for rearanging the hashtable as well overwriting the database file to store the now modified data (A for loop going around MINTABLESIZE times is used to achieve this).

To achive this, the database file is opened at first with a write ("w") mode (This is necessary for the content of the file to be erased), setlinebuf() is called on the file to make sure it is line buffered (This makes it so we can write onto the file while the program is runnin. Otherwise, we would have to wait until the program is closed).

The file is, then, closed an reopened again in append ("a") mode (This makes sure information is not overwriten but appears one after the other).

###### void edit_employee()

The same "Modus operandi" of "remove_employee", but, insted of removing, it prompts the user to write new information concerning that specific item (If a match occurs, that is).

###### PRODUCT functions XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

###### void signup_product()

This function, at first, declares a new struct variable of type "createproduct". After that, the user is propted to tell all the associated information and stores everything in the previously declared variable.

At the end, the "save_prodcut" function is called with the values of the varible being passed to it.

A lot of caution is taken to remove any trailing newline  (\n) character remaining. The strcspn function is used to achieve this level of optimization.

###### void save_product(createproduct product)

This function declares a pointer o type FILE, opens the correct database and goes over a fprintf() to store at the database the passed "product" values. It, then, closes the opened file.

###### void show_product_database_all()

This function load the product database (using the load_product_databases() function) and navigates the hashtable (vertically and horizontally) printing every existing employee in a formated and organized manner. The objective of this function is to print all existing products.

A increment functionality exists to showcase at screen at waht position said product was printed (for organizational reasons).
At the end, the database is unloaded (using thew unload_product_database() function).

###### bool load_product_databases()

This function has the important task of reading all data present at the product database file, storing is data in a buffer (using fgets()) and coping the buffer content to the correct place in node pointer of type "product" (strcpy function is used to achieve this).

At the end, all opened files are closed and all allocated is freed. The function returns true if no "return false" condition is met (normally this may happen at the moment a file is opened or a chunck of memory is allocated.

###### bool unload_product_databases()

Navigates the hash table properly freeing its content.

###### void show_product_database_detailed()

This function is responsible for powering the search functionality. It takes a chosen and specific to product data type criteria and navigates the correct hashtable. Using strcasecmp(), any found match of information and user input is printed on-screen.

###### void remove_product()

This function receives user input and search the correct hashtable, removing the associated item if a match occurs. 

It is responsiBle for rearanging the hashtable as well overwriting the database file to store the now modified data (A for loop going around MINTABLESIZE times is used to achieve this).

To achive this, the database file is opened at first with a write ("w") mode (This is necessary for the content of the file to be erased), setlinebuf() is called on the file to make sure it is line buffered (This makes it so we can write onto the file while the program is runnin. Otherwise, we would have to wait until the program is closed).

The file is, then, closed an reopened again in append ("a") mode (This makes sure information is not overwriten but appears one after the other).

###### void edit_product()

The same "Modus operandi" of "remove_product", but, insted of removing, it prompts the user to write new information concerning that specific item (If a match occurs, that is)

###### DEALER functions XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

###### void signup_dealer()

This function, at first, declares a new struct variable of type "createdealer". After that, the user is propted to tell all the associated information and stores everything in the previously declared variable.

At the end, the "save_dealer" function is called with the values of the varible being passed to it.

A lot of caution is taken to remove any trailing newline (\n) character remaining. The strcspn function is used to achieve this level of optimization.

###### void save_dealer(createdealer dealer)

This function declares a pointer o type FILE, opens the correct database and goes over a fprintf() to store at the database the passed "dealer" values. It, then, closes the opened file.

###### void show_dealer_database_all()

This function load the dealer database (using the load_dealer_databases() function) and navigates the hashtable (vertically and horizontally) printing every existing dealer in a formated and organized manner. The objective of this function is to print all existing dealers.

A increment functionality exists to showcase at screen at waht position said dealer was printed (for organizational reasons).
At the end, the database is unloaded (using thew unload_dealer_database() function).

###### bool load_dealer_databases()

This function has the important task of reading all data present at the dealer database file, storing is data in a buffer (using fgets()) and coping the buffer content to the correct place in node pointer of type "dealer" (strcpy function is used to achieve this).

At the end, all opened files are closed and all allocated is freed. The function returns true if no "return false" condition is met (normally this may happen at the moment a file is opened or a chunck of memory is allocated.

###### bool unload_dealer_databases()

Navigates the hash table properly freeing its content.

###### void show_dealer_database_detailed()

This function is responsible for powering the search functionality. It takes a chosen and specific to dealer data type criteria and navigates the correct hashtable. Using strcasecmp(), any found match of information and user input is printed on-screen.

###### void remove_dealer()
 
This function receives user input and search the correct hashtable, removing the associated item if a match occurs. 

It is responsiBle for rearanging the hashtable as well overwriting the database file to store the now modified data (A for loop going around MINTABLESIZE times is used to achieve this).

To achive this, the database file is opened at first with a write ("w") mode (This is necessary for the content of the file to be erased), setlinebuf() is called on the file to make sure it is line buffered (This makes it so we can write onto the file while the program is runnin. Otherwise, we would have to wait until the program is closed).

The file is, then, closed an reopened again in append ("a") mode (This makes sure information is not overwriten but appears one after the other).

###### void edit_employee()

The same "Modus operandi" of "remove_dealer", but, insted of removing, it prompts the user to write new information concerning that specific item (If a match occurs, that is).

## functions_general.c

In this file, functions, hashtables and global variables that are used in both types of accounts are located. 

Quality of life components are also present.

###### void clear()

Simple function that can clear the terminal screen.

###### void boilerplate()

Calls clear() and proceeds to print on-screen usual boilerplate that is present in (almost) every screen.

###### bool check_lenght(char *credential)

Function responsible to check if a give credential is of correct lenght, returning true if so and false otherwise.

###### bool check_password(char *password, char *password)

Receives a password and a confirmation, checks if both are equal matching each character of the array. At each match, a increment variable goes up.

In the end, if the value of increment is equal to the lenght of the original password (strlen(password)), true is returned, false otherwise.

###### void press_to_continue()

Function responsible to wait until the user presses enter to escape an while loop.

###### bool load_account_databases()

This function has the important task of reading all data present at the account database file, storing is data in a buffer (using fgets()) and coping the buffer content to the correct place in node pointer of type "account" (strcpy function is used to achieve this).

At the end, all opened files are closed and all allocated is freed. The function returns true if no "return false" condition is met (normally this may happen at the moment a file is opened or a chunck of memory is allocated.

###### int hash_index(char *subject)

Receives a subject and returns a hash value based on that.

Makes sure the returned number does not surpass the constant value of MINTABLESIZE.

###### void login()

Checks database to check if given credentials exists.

It also checks the type of the given account and routes accordingly.

At this function, the global variables:

+ char current_account[MAXMAXSIZE]
+ char current_account_type[MAXMAXSIZE]

Both receives the associated information to keep track of what account is currently being used (strcpy() is used to copy from input to the variables).

###### bool check_login()

Function responsible to comparing values at hashtable with given credential (case sensitive: strcmp()), returning true if a password and username match occurs.

This functions uses the hash_index() function to receive an array index jump to the correct location at the corresponding hashtable instantly.

###### bool check_username(char *username)

Receives an username ans checks if it already exists in the database (using strcmp), returning false if so.

###### bool unload_account_databases()

Navigates the hash table properly freeing its content.

###### void menu_show_items()

Menu exposing all options avaible at the "view items" tool.

Calls answer_show_items() at the end.

###### void answer_show_items()

Multiple switch case condition nested onto each other to deal with the complexity of "search" and "view all" tools. 

Ordinary answer router.

###### bool check_if_current_account(char *username)

Receives an username and see if it matches with the value present at "char current_account[MAXMAXSIZE]" global array.

If so, that means the username is already being used, false is returned.

###### bool remoce_account()

Ordinary removal from database.

###### void menu_manual_admin() and menu_manual_limited()

redundantly segregated functions ta print the same menu, but call different functions at the end.

###### void answer_manual_admin() and answer_manual_limited()

Answer routers tha have the diffence of returning to different menus when done.

###### int check_account_type()

This function returns 1 if the value present at "char current_account_type[MAXMAXSIZE]" is equal to "limited" (strcmp() is used to achieve this).

0 is returned if account type is "admin"

###### void report()

Receives report information and prints it in a formated and organized manner.














  
 




