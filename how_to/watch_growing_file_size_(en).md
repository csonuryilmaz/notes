Let's assume that you have growing file on your file system. For example, dumping a database with mysqldump. You want to watch its size with a duration. How can we do?

When you want to check file size at a moment, you execute something like this:

```
ls -lh db_dump.sql
```

and it prints out something like this:

```
-rw-r--r-- 1 root root 452M Oca  4 22:14 db_dump.sql
```

We will use **awk** to get file size from output. Why is AWK? Because it is an excellent filter and report writer. Many UNIX utilities generates rows and columns of information. AWK is an excellent tool for processing these rows and columns, and is easier to use.

When we pipe this output to **awk**,it splits the record delimited by whitespace character by default and stores it in the $n variables. If the line has 4 words, it will be stored in $1, $2, $3 and $4. $0 represents whole line.

Final version of our command will be this:

```
ls -lh db_dump.sql | awk '{print $5}'
```

When you execute, it will only print file size:

```
452M
```

Then we will pass this command as a parameter to **watch** command. It executes a program periodically and shows  output fullscreen.

```
watch -n 5 "ls -lh db_dump.sql | awk '{print \$5}'"
```

Above command will show you file size every 5 seconds.

Happy hacking!