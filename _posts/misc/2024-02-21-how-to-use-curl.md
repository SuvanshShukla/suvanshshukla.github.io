---
title: How to use cURL
categories: [misc]
tags: [misc, cURL]
---

# cURL is basically a command line utility to send API requests 

useful note on how to write shell scripts to run curl commands : [[Bash-Scripting#Writing your cURL command script|Writing your cURL command script]] 

Useful Link on CURL - [Using Curl to make REST API requests](https://linuxize.com/post/curl-rest-api/)

Example command 
```powershell
$ curl -X POST -d "USR_0" http://localhost:9090/clovek/super-admin/resend/signup/email
```

## How to use cURL actually 
- you will need to use the BASH shell 
- you need to know how to write multi line commands in BASH 
- here's how you write multiline commands : 
- write the command's start like so : 
```bash 
curl -X 'POST' \
```
- notice how I add a `space` and a `\` at the end of the line 
- this will open up, what I call a 'sub-mode' while entering a command 
- now press enter and you'll get `>` where you can continue on the next part of your command 
- after you have successfully finished the command and all the quotes and brackets match your command will run once you hit enter 

here's an example of a payload that worked for me : 
```bash 
$ curl -X 'POST' \
> -H 'Content-Type: application/json' \
> -d '{
> "userId" : "USR_236"
> }' \
> 'http://localhost:5000/clovek/get/clientRiskProfile'
```
> [!NOTE] 
> Notice how there are only `\` at the end of an option of the command not in-between. This is why we can simply use single-quote `'` to start and continue the payload, and then put `\`after the closing single-quote `'` 

## Putting the payload into a `.json` file and using it in cURL 
- you can put the payload into a separate `.json` file if you think that it is too large to write out in the terminal 
- and then mention the file (using its absolute path) in the command 
- for example 
```bash 
$ curl -X 'POST' \
> -H 'Content-Type: application/json' \
> -d @payload.json \
> 'http://localhost:5000/clovek/get/clientRiskProfile'
```
notice how I didn't need to mention the absolute path, this is because the file was already present in the directory from where I was hitting this command 
- here's an example using absolute path : 
```bash
$ curl -X 'POST' \
> -H 'Content-Type: application/json' \
> -d @C:/Users/suvansh.shukla/Documents/Scratch-Buffers/test/payload.json \
> 'http://localhost:5000/clovek/get/clientRiskProfile'
```
#### On Writing Bash Scripts 
- see this [note on Bash Scripting]({% post_url 2024-02-21-bash-scripting %})