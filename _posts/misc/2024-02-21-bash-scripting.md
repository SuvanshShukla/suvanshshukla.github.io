---
title: Notes on writing Bash Scripts
tags: [misc, bash]
categories: [misc]
---

I was experimenting with writing curl commands as I wanted to find the easiest way to hit any API that I was testing 

#### Good Link on learning shell scripting : [Shell Scripting for Beginners – How to Write Bash Scripts in Linux](https://www.freecodecamp.org/news/shell-scripting-crash-course-how-to-write-bash-scripts-in-linux/)


I then stumbled on how to maybe just skip writing the `-X 'POST'` and `-H 'Content-Type: application/json'` 
and this [stackoverflow answer](https://stackoverflow.com/questions/8829167/use-curl-with-a-file-of-commands) talked about how to use a bash script to run the command instead which I felt would be kind of cool 

## Pre-requisites
1. you need to know the location of your bash shell 
2. use the following command to find out where it is : 
```bash 
which bash 
```
3. write your actual shell script 
4. I use `vim` so basically start your script like this : 
```bash 
vim try.sh
```
5. then write your script with the start like this :
```bash
! /usr/bin/bash
or 
! /bin/bash
```
whatever is the output of `which bash` will come after `! <space>` 


## Writing your cURL command script
write it like this : 
```bash 
#! /usr/bin/bash
curl -X 'POST' \
'http://localhost:5000/clovek/get/clientRiskProfile' \
-H 'Content-Type: application/json' \
-d '{
"userId" : "USR_64"
}'
```
then save-quit (by `:wq` or `ZZ`, i.e. capital Z and capital Z)

## Running the shell script 
We need to first give this file run permission like so : 
```bash
chmod u+x try.sh
```

then run the shell like so :
```bash
./ try.sh
```
