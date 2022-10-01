---
layout: post
title: Fundamental Access Control
date: 2022-10-01
categories: ["mysql", "tutorial", "assignment", "database security", "acl"]
---

## Fundamental Access Control
In the fields of physical security and information security, access control (AC) is the selective restriction of access to a place or other resource, while access management describes the process. The act of accessing may mean consuming, entering, or using. Permission to access a resource is called authorization.
Locks and login credentials are two analogous mechanisms of access control.  
1. Mandatory Access Control  
In MAC, users do not have much freedom to determine who has access to their files. For example, security clearance of users and classification of data (as confidential, secret or top secret) are used as security labels to define the level of trust.
Example on MySQL:
There are 3 roles exist in a MySQL database system, every role has pre-determined privilege given by the administrator, the higher the level, the more they gained privilege. In this case, we are using 3 level, start from the highest level is level 1.  
**Role**|**Privilege**|**Analogy**
:-----:|:-----:|:-----:
Level 1|Global level privilege – can access all things in MySQL|↑❌↓✔️
Level 2|Database level privilege – can only access database that been given permission by admin|↑❌↓✔️
Level 3|Table level privilege – can only access table that been given permission by admin|↑❌↓✔️  

Level 1:  

Could do anything in MySQL, literally.  
Level 2:  
 
Could do anything in `classicmodels’ database.  
Level 3:  
 
Could do anything in `customers` table of `classicmodels` database.
Each role could be assigned to the desired user, but be cautious, the higher the level they have, the more control they have, so we need to be extra careful with role assigning.  
2. Discretionary Access Control  
In DAC, the data owner determines who can access specific resources. For example, a system administrator may create a hierarchy of files to be accessed based on certain permissions.  
Example on MySQL:  
As we can see, the data owner in MySQL is the administrator itself, so it depends on administrator which data could be shared. It’s the same as we did before, we are giving privilege to roles that exist in MySQL.  
If the administrator wanted to share a data, admin could just give a privilege to some roles or user.  
 
3. Role Based Access Control  
RBAC allows access based on the job title. RBAC largely eliminates discretion when providing access to objects. For example, a human resources specialist should not have permissions to create network accounts; this should be a role reserved for network administrators.  
Example on MySQL:  
So, we are going to assign roles that we created before in MAC section. There are 3 roles, that is level 1, level 2, and level 3. Let’s hit it up!  
**User**|**Role**
:-----:|:-----:
Michael as a Data Administrator|Level 1
John as a Database Administrator|Level 2
Richard as an Office Worker|Level 3  

Roles Assigning and User Creation:  
 
 
Level 1 User:  
 
Level 2 User:  
 
Level 3 User:  
 

References:  
https://en.wikipedia.org/wiki/Access_control
https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql
https://dev.mysql.com/doc/refman/8.0/en/roles.html#mandatory-roles
https://dev.mysql.com/doc/refman/8.0/en/grant.html#grant-global-privileges
https://dev.mysql.com/doc/refman/8.0/en/revoke.html
https://dev.mysql.com/doc/refman/8.0/en/drop-role.html  
Thanks! 🙏
