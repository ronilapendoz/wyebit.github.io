---
layout: post
title: Fundamental Access Control
date: 2022-10-01
categories: ["mysql", "tutorial", "assignment", "database security", "acl"]
---

In the fields of physical security and information security, access control (AC) is the selective restriction of access to a place or other resource, while access management describes the process. The act of accessing may mean consuming, entering, or using. Permission to access a resource is called authorization.
Locks and login credentials are two analogous mechanisms of access control.  
### Mandatory Access Control  
In MAC, users do not have much freedom to determine who has access to their files. For example, security clearance of users and classification of data (as confidential, secret or top secret) are used as security labels to define the level of trust.
Example on MySQL:
There are 3 roles exist in a MySQL database system, every role has pre-determined privilege given by the administrator, the higher the level, the more they gained privilege. In this case, we are using 3 level, start from the highest level is level 1.  

| Role    | Privilege                                                                               | Analogy |
| ------- | --------------------------------------------------------------------------------------- | ------- |
| Level 1 | Global level privilege – can access all things in MySQL                                 | ↑ ❌     | ↓ ✔️ |
| Level 2 | Database level privilege – can only access database that been given permission by admin | ↑ ❌     | ↓ ✔️ |
| Level 3 | Table level privilege – can only access table that been given permission by admin       | ↑ ❌     | ↓ ✔️ |

Level 1:  
![mac](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/mac.png?raw=true)  
Could do anything in MySQL, literally.  
Level 2:  
![mac-2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/mac-2.png?raw=true)  
Could do anything in `classicmodels` database.  
Level 3:  
![mac-3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/mac-3.png?raw=true)  
Could do anything in `customers` table of `classicmodels` database.
Each role could be assigned to the desired user, but be cautious, the higher the level they have, the more control they have, so we need to be extra careful with role assigning.  
### Discretionary Access Control  
In DAC, the data owner determines who can access specific resources. For example, a system administrator may create a hierarchy of files to be accessed based on certain permissions.  
Example on MySQL:  
As we can see, the data owner in MySQL is the administrator itself, so it depends on administrator which data could be shared. It’s the same as we did before, we are giving privilege to roles that exist in MySQL.  
If the administrator wanted to share a data, admin could just give a privilege to some roles or user.  
![dac](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/dac.png?raw=true)  
### Role Based Access Control  
RBAC allows access based on the job title. RBAC largely eliminates discretion when providing access to objects. For example, a human resources specialist should not have permissions to create network accounts; this should be a role reserved for network administrators.  
Example on MySQL:  
So, we are going to assign roles that we created before in MAC section. There are 3 roles, that is level 1, level 2, and level 3. Let’s hit it up!  

| User                             | Role    |
| -------------------------------- | ------- |
| Michael as a Data Administrator  | Level 1 |
| John as a Database Administrator | Level 2 |
| Richard as an Office Worker      | Level 3 | 

Roles Assigning and User Creation:  
![rbac](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/rbac.png?raw=true)  
![rbac-2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/rbac-3.png?raw=true)  
Level 1 User:  
![rbac-3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/rbac-3.png?raw=true)  
Level 2 User:  
![rbac-4](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/rbac-4.png?raw=true)  
Level 3 User:  
![rbac-5](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-10-01-fundamental-access-control/rbac-5.png?raw=true)  

References:  
- Wikipedia contributors. (2022, August 17). _Access control_. Wikipedia. Retrieved October 1, 2022, from [https://en.wikipedia.org/wiki/Access_control](https://en.wikipedia.org/wiki/Access_control)
- Sverdlov, E. (2022, March 18). _How To Create a New User and Grant Permissions in MySQL_. DigitalOcean Community. Retrieved October 1, 2022, from [https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)
- _MySQL :: MySQL 8.0 Reference Manual :: 6.2.10 Using Roles_. (n.d.). Retrieved October 1, 2022, from [https://dev.mysql.com/doc/refman/8.0/en/roles.html#mandatory-roles](https://dev.mysql.com/doc/refman/8.0/en/roles.html#mandatory-roles)
- _MySQL :: MySQL 8.0 Reference Manual :: 13.7.1.6 GRANT Statement_. (n.d.). Retrieved October 1, 2022, from [https://dev.mysql.com/doc/refman/8.0/en/grant.html#grant-global-privileges](https://dev.mysql.com/doc/refman/8.0/en/grant.html#grant-global-privileges)
- _MySQL :: MySQL 8.0 Reference Manual :: 13.7.1.8 REVOKE Statement_. (n.d.). Retrieved October 1, 2022, from [https://dev.mysql.com/doc/refman/8.0/en/revoke.html](https://dev.mysql.com/doc/refman/8.0/en/revoke.html)
- _MySQL :: MySQL 8.0 Reference Manual :: 13.7.1.4 DROP ROLE Statement_. (n.d.). Retrieved October 1, 2022, from [https://dev.mysql.com/doc/refman/8.0/en/drop-role.html](https://dev.mysql.com/doc/refman/8.0/en/drop-role.html)
  
Thanks! 🙏
