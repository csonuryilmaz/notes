### Subversion Client with Github

GitHub repositories can be accessed from **subversion** clients. Github uses a subversion bridge to communicate svn commands to GitHub. So for those, who are familiar with subversion clients, will use github easily with **svn** commands like me.

Checkout repository root:
```
$ svn co --depth empty https://github.com/user/repo
```
Get the **trunk** branch. The Subversion bridge maps trunk to the Git HEAD branch (which is usually **master**):
```
$ cd repo
$ svn up trunk
```
#### Working with Branches

To get an empty checkout of the branches directory. This is where all of the non-HEAD branches live, and where you'll be making feature branches.
```
$ svn up --depth empty branches
```
You can use **svn copy** to create a new branch:
```
$ svn copy trunk branches/more_awesome
```

You can use other subversion commands as you used before. [Here](https://www.cheatography.com/davechild/cheat-sheets/subversion/) is a subversion cheatsheet if you need to remember some of them.

Happy coding!
