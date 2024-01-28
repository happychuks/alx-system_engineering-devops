# Bash Scripting: Loops, Conditions, and Parsing

## SSH Keygen
- Generate the SSH key using the following command: 
```bash
ssh-keygen -t rsa
```
- Save a Copy the public key generated using the following command:
```bash
cat ~/.ssh/id_rsa.pub > <filename>
```
Example format of a public key:
```bash
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC6e5yRWT/lTz7aW8HqQzDpVmOdo1Z++1hqIgY8PjjPRLlMjY1S4ti/A1VhWbnSdo6SIAf7FmbYL/F3Dv9FdBKfP2YItDuzA7Jq1i/lGKQRHJi/7sCcXvMf6sXdHUTURKUaZM7h1MWqGr3hMx2WymzJklNY3UjvOVvdRv0LsCzr1DgZJz0EwefGiGd5fgqWJsU2Lf8e+ctktVudKdBKG9ZZBYvyfDJWde+3GDRwQIsa/0CgX0NkUjv9FvEmeUbdZ5wFm7l7zGhtLpVx6VbYfbL3xQUTAa5yNNqz6u7FEdTobw2NzCl0pSGF6o2KLBC1g6yYOLpY2szIcWClY+wti8wY+aRYdKp9rRIJFkbl/KxNzTX6I2CnzpC0CCZTHNSxZvzZFC5ia3oBS28sXyp1AcCptzovvcf2q6J4MbSmfw9Nai5YF+RSL8Atp9qfVzzyhGW0Hr0LAVsd6VVX60= user@example.com
```
The public key is shared openly, while the private key is kept confidential. Together, they enable secure communication and verification in asymmetric key cryptography.

## Loops in Bash

### `for` Loop
The `for` loop in Bash is used for iterating over a sequence, such as a range of numbers or items in an array.

```bash
for item in {1..5}
do
  echo "Iteration: $item"
done
```

### `while` Loop
The `while` loop continues executing a set of commands as long as a specified condition is true.

```bash
counter=0
while [ $counter -lt 5 ]
do
  echo "Iteration: $counter"
  ((counter++))
done

```

## awk
`awk` is a powerful text processing tool in Unix and Unix-like operating systems. It is designed for pattern scanning and processing. awk allows you to search for specific patterns in text and perform specified actions based on those patterns. It is particularly useful for extracting and manipulating data from text files.

## parsing of logfiles
Apache is among the most popular web servers in the world, serving 50% of all active websites, no doubt that you will have to interact with it within your career.

As a Full-Stack Software Engineer, you have to master the art of parsing log files.
log files are saved in .log file format

Sample log parsing
Write a Bash script that displays the visitor IP along with the HTTP status code from the Apache log file.

Requirement:
Format: IP followed by HTTP_STATUS_CODE
output should be in a list format
```bash
awk '{print $1 " " $9}' apache-access.log
```
Sample output:
```bash
185.130.5.207 301
185.130.5.207 301
91.224.140.223 200
62.210.142.23 304
92.222.20.166 304
180.76.15.19 200
2.1.201.36 304
198.58.99.82 304
50.116.30.23 304
209.133.111.211 200
```

