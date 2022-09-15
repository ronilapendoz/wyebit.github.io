---
layout: post
title: Create 2 VM, 1 VM with 3 wordpress inside, and 1 VM with 3 databases inside
date: 2022-09-15
categories: ["wordpress", "mysql", "tutorial", "assignment", "database security"]
---

## Prerequisites:
Windows OS
- [Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads) 
- [Ubuntu Server ISO file](https://ubuntu.com/download/server) 
- [Apache](https://directory.apache.org/studio/download/download-linux.html)
- [MySQL](https://dev.mysql.com/downloads/mysql/)
- [Wordpress package](https://wordpress.org/download/)

1.	Preserve all of the requirements I have mentioned above
2.	Install the Oracle VM VirtualBox app, and get it done. About how to install it step by step, I would point you to an article that provide more details; https://www.virtualbox.org/manual/ch02.html
3.	Install the Ubuntu Server ISO file on Oracle VM VirtualBox app. As usual I won’t tell you how to do it, instead I could offer an article about it, because it will be cost me more time and space, also it’s not our main objective right here. Here’s the article; https://adinusa.id/content/post/blogs/panduan-install-ubuntu-server-di-virtualbox/
4.	Make 2 VMs by following instructions from number before, one for the web server and one for the database server
5.	In this section, we’re going easy with these stuff by installing LAMP (Linux, Apache, MySQL, PHP), a bundle that include all of those program that we needed. The full instructions could be discovered here; https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04, we’re doing this for both VM
6.	After all of those stuff have been installed, we’re going to setup the databases in its server, we could go into a website; https://www.digitalocean.com/community/tutorials/install-wordpress-on-ubuntu, make 3 databases and its user, get it done, and we’re continuing to next step  

7.	Done with the databases, go for the wordpress CMS installation, I have mentioned the instructions link at number 6, make it well, and then proceed to the next step  

8.	Here it is, the preview of multiple wordpress in one host  

9.	Done installing the wordpress CMS, next we’re going to connect wordpress VM to databases VM, here’s the reference; https://www.linode.com/docs/guides/configure-wordpress-remote-database/ 
10.	This is how it looks when it done having a connection between wordpress VM and database VM  

11.	Continue the site registration and then try to login to admin page, afterwards we’re going to costumize the site based on our preferences  

12.	Here they are, the 3 websites I have been configured with theme, they are all usable and ready for further development.  

13.	Voila!
