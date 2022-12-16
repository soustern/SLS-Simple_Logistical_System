# SLS - Simple Logistical System

#### Video Demo:  https://www.youtube.com/watch?v=pSxkruwjchE

#### Description: A simple logistical system that has the ability to create, edit, show, search (with multiple criteria) and remove items of three possible categories. It also has the capability to create and showcase useful reports, having fully implemented account features (login, creation and removal) as well as a complete a intuitive manual and various security/quality of life implementations. The user can control usage by having access to two different types of accounts, limited (Only vizualization) and admin (all features).

# DOCUMENTATION

# FILES 

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

This files contains all functions associated to functionalities present at accounts of "admin" type. Here we can find an assortment of global variables and data tables of all struct data types.

###### int count_numerical_quantity_employee()

This function traverses an hash table wich has all employees (present at database) loaded. For every employee found, an increment variable goes up one. At last, the function returns the resulting integer.

###### int count_numerical_quantity_product()

This function traverses an hash table wich has all products (present at database) loaded. For every product found, an increment variable goes up one. At last, the function returns the resulting integer.

###### int count_numerical_quantity_dealer()



  
 




