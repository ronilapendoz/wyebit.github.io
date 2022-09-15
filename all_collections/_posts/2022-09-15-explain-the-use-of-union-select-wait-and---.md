---
layout: post
title: Explain the Use of UNION, SELECT, WAIT and --
date: 2022-09-15
categories: ["wordpress", "mysql", "tutorial", "assignment", "database security"]
---

1.	`UNION`  
The `UNION` operator is used to combine the result-set of two or more `SELECT` statements.
- Every `SELECT` statement within `UNION` must have the same number of columns
- The columns must also have similar data types
- The columns in every `SELECT` statement must also be in the same order  
![1](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-15-explain-the-use-of-union-select-wait-and---/1.png?raw=true)
2.	`SELECT`  
The `SELECT` statement is used to select data from a database. The data returned is stored in a result table, called the result-set  
![2](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-15-explain-the-use-of-union-select-wait-and---/2.png?raw=true)
3.	`WAIT`  
Hmm, about `WAIT`, we’re going to use `SLEEP` because `WAIT` command is not available in MySQL. `SLEEP` is a command to put a delay on an output before it gets returned.  
![3](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-15-explain-the-use-of-union-select-wait-and---/3.png?raw=true)
4.	`--`  
`--` is one of three comment styles that available in MySQL  
![4](https://github.com/wyebit/wyebit.github.io/blob/main/assets/images/posts/2022-09-15-explain-the-use-of-union-select-wait-and---/4.png?raw=true)

Thanks!:clap:
