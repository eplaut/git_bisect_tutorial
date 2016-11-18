# `git bisect` Tutorial

Hi There!

Welcome to git bisect toturial, this repository is based on [A beginner's guide to GIT BISECT - The process of elimination](http://www.metaltoad.com/blog/beginners-guide-git-bisect-process-elimination) by [Tony Rasmussen](http://www.metaltoad.com/people/tony) and the [Git official documentation](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git). 

### What should I do?

In this repo you will find the file `test.txt`. To make sure the repo is not broken you must ensure that `test.txt` contains the word "boat".

We marked the first good commit, where `test.txt` contains the word "boat" for the first time as `v1.0`, so you can state it as `good`.

Now, we want you to check if `test.txt` contains the word "boat". Please open it in your favorite editor and search for it.

### It not there... well, that was expected ;)

Now you have the option to use `git bisect` to find the broken commit where the "boat" disappeared.


To start a binary search for the broken commit, you will have to run:

```bash
$ git bisect start
```

It will start bisect wizard, which will keep changing commits (yes, on your working directory) until you will find the broken commit. If you want to stop it you must run `git bisect reset` if you want to avoid ending up in a weird state.

You will need to state each commit as `good` or `bad`, and the bisect wizard will change to the next commit. For now we know that the curent commit is `bad` and "v1.0" is `good` (yes, you can give tags as well as commits), so you just run:

```bash
$ git bisect bad
$ git bisect good v1.0
```

Git bisect change your working directory for the first time, check the file again. If it contains "boat" run `git bisect good`, else run `git bisect bad`. Now, do it until git bisect will tells you it found the commit.

On the broken commit you will find an easter egg for how to automated bisect, Good Luck!

### Thanks

@chenl and @eliadl for all the great work!


