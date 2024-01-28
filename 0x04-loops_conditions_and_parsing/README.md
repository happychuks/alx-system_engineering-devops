# Bash Scripting: Loops, Conditions, and Parsing

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


