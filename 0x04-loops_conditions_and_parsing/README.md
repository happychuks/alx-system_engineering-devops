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


