If you don't **nohup** a job when it begins, you can use **disown** to modify a running job.

**1.** Press **Ctrl+Z** in order to stop (pause) the program and get back to the shell. 

**2.** List active jobs with process IDs in addition to the normal information. (process ID is in 2nd column)
```
$ jobs -l
```
**3.** Run **disown** command with the number of job which is listed in the output of **job** command. Let's assume we want to disown first job in the list:
```
disown -h %1
```
**4.** Now the stopped (paused) job is disowned and it won't be affected when you close your terminal. You can resume the process by using **bg** command or ```kill -CONT <PID>```
