## Bash Cookbook

Iterating over a text line by line:
```bash
echo -e "$text" | while read line ; do
   echo === $line ===
done
```
Getting last character of a string:
```bash
echo "${text: -1}"
```
Incrementing a variable value:
```bash
count=$((count+1))
```
