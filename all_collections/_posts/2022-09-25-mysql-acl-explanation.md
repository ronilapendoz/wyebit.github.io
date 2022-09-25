---
layout: post
title: MySQL Access Control List Explanation
date: 2022-09-15
categories: ["mysql", "tutorial", "assignment", "database security", "acl"]
---

## Objective
Do trial and error on MySQL ACL, and make a report about it
## Description
When we are talking about ACL (Access Control List), we could refer it to authorization process. So, we are going to play a bit with authorization process that is available in MySQL. Authorization is a function of specifying access rights/privileges to resources, which is related to general information security and computer security, and to access control in particular.
There are 4 privileges level exist on MySQL database based on this website:
- *Global privileges* apply to all databases on the server. Administrative privileges fall into the global group because they enable a user to manage operations of the MySQL server and aren't specific to a particular database.
- *Database privileges* apply to specific databases in your MySQL instance and all of the objects within those databases (e.g. tables, columns, and views). You can also grant database privileges globally.
- *Proxy privileges* allow a user to act as if they have the privileges granted to another user.
- *Privileges for database objects* (tables, columns, stored routines, views, etc.) can apply to all objects of one type within a particular database or to specific objects, such as a certain table or view. You can also grant database object privileges globally.
These are some of common privileges we will be using:
- `ALL PRIVILEGES`: The user is granted all privileges except GRANT OPTION and PROXY.
- `ALTER`: The user can change the structure of a table or database.
- `CREATE`: The user can create new databases and tables.
- `DELETE`: The user can delete rows in a table.
- `INSERT`: The user can add rows to a table.
- `SELECT`: The user can read rows from a table.
- `UPDATE`: The user can update rows in a table.
So, we are mainly going to use GRANT and REVOKE statement in this session to play with ACL.
## Cases
We are going to run some trials and errors with ACL in this section, I’m creating 4 users to be used for cases later:
 
1. Case 1
I’m granting a privilege to user1 to do anything in the databases except modifying privileges on another user.
 
Tried to delete a database and it’s done:
 
Tried to create a new database, and it is done too:
 
So, that’s how global level privilege works, it could do anything to MySQL except privileges alteration:
 
2. Case 2
Right now, we are trying to apply database level privileges to user2. I have been given privilege to user2 to take all control of database named classicmodels:
 
Let’s try to do something to database classicmodels, I have created a new table with columns in it. And when I tried to execute `SHOW DATABASE` it’s only showing the database that user2 could read:
 
Tried to delete a table, and it runs perfectly:
 
But when I tried to create user, user2 could not do that, because user2 only have permission to do anything in a database that have been specified before:
 
That’s how database level privileges work, it could do anything inside database it been assigned to, but it can not do anything outside of the database.
3. Case 3
Before, we tried to apply database level privileges, now we’re going to apply table level privileges which it will be more specific than before. We are going to apply it to user3 in this part:
 
User3 has been given privileges to execute `SELECT` and `INSERT` statement to offices table in classicmodels database. Right now, we are going to try to execute statements and see what the result is:
 
As we can see from picture above, it displays us that we can only access database named classicmodels and table named offices inside the DB, because root user only gave user3 two privileges to only accessing DB and table mentioned.
That’s how table level privileges work.
4. Case 4
We are going to jump right into column level privilege, we applied it to user4 this time. Statements given are `SELECT` and `INSERT` to columns in employees table in classicmodels DB:
 
It displayed that we can’t show all of the columns in employees table, because user4 only have access to lastName column when using `SELECT` statement:
 
 

