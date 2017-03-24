Find users (list only usernames!)

```bash
awk -F':' '{ print $1}' /etc/passwd
```

You can also filter specific user by piping output to grep:

```bash
awk -F':' '{ print $1}' /etc/passwd |grep onur
```
