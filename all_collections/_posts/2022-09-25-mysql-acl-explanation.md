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
- **Global privileges** apply to all databases on the server. Administrative privileges fall into the global group because they enable a user to manage operations of the MySQL server and aren't specific to a particular database.
- **Database privileges** apply to specific databases in your MySQL instance and all of the objects within those databases (e.g. tables, columns, and views). You can also grant database privileges globally.
- **Proxy privileges** allow a user to act as if they have the privileges granted to another user.
- **Privileges for database objects** (tables, columns, stored routines, views, etc.) can apply to all objects of one type within a particular database or to specific objects, such as a certain table or view. You can also grant database object privileges globally.  
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
![cases](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/cases.png?raw=true)
1. Case 1  
I’m granting a privilege to user1 to do anything in the databases except modifying privileges on another user.  
![case1](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case1.png?raw=true)  
Tried to delete a database and it’s done:  
![case1-2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case1-2.png?raw=true)  
Tried to create a new database, and it is done too:  
![case1-3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case1-3.png?raw=true)  
So, that’s how global level privilege works, it could do anything to MySQL except privileges alteration:  
![case1-4](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case1-4.png?raw=true)
2. Case 2  
Right now, we are trying to apply database level privileges to user2. I have been given privilege to user2 to take all control of database named classicmodels:  
![case2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case2.png?raw=true)  
Let’s try to do something to database classicmodels, I have created a new table with columns in it. And when I tried to execute `SHOW DATABASE` it’s only showing the database that user2 could read:  
![case2-2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case2-2.png?raw=true)  
Tried to delete a table, and it runs perfectly:  
![case2-3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case2-3.png?raw=true)  
But when I tried to create user, user2 could not do that, because user2 only have permission to do anything in a database that have been specified before:  
![case2-4](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case2-4.png?raw=true)  
That’s how database level privileges work, it could do anything inside database it been assigned to, but it can not do anything outside of the database.
3. Case 3  
Before, we tried to apply database level privileges, now we’re going to apply table level privileges which it will be more specific than before. We are going to apply it to user3 in this part:  
![case3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case3.png?raw=true)  
User3 has been given privileges to execute `SELECT` and `INSERT` statement to offices table in classicmodels database. Right now, we are going to try to execute statements and see what the result is:  
![case3-2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case3-2.png?raw=true)  
As we can see from picture above, it displays us that we can only access database named classicmodels and table named offices inside the DB, because root user only gave user3 two privileges to only accessing DB and table mentioned.
That’s how table level privileges work.
4. Case 4  
We are going to jump right into column level privilege, we applied it to user4 this time. Statements given are `SELECT` and `INSERT` to columns in employees table in classicmodels DB:  
![case4](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case4.png?raw=true)  
It displayed that we can’t show all of the columns in employees table, because user4 only have access to lastName column when using `SELECT` statement:  
![case4-2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case4-2.png?raw=true)  
![case4-3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-25-mysql-acl-explanation/case4-3.png?raw=true)  

## Source
- [](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html)
- [](https://www.strongdm.com/blog/mysql-create-user-manage-access-privileges-how-to)  

Thanks!🙏