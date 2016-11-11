# `git bisect` Automation Tutorial

Hi Again!

Wellcome to git bisect toturial, this repository based on [A beginner's guide to GIT BISECT - The process of elimination](http://www.metaltoad.com/blog/beginners-guide-git-bisect-process-elimination) by [Tony Rasmussen](http://www.metaltoad.com/people/tony) and the [Git official documentation](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git). 

### How can I automate bisect?

You surely know how to use `git bisect`, but won't it be easy if you can find it without checking each commit and mark it as "good" or "bad"?

Well, it is easy than you may thought. Have a look in `test.sh` file we added here.

```bash
$ cat test.sh
#!/bin/bash -e
grep -q 'boat' test.txt
```

This simple script returns success code (return code 0) when it finds "boat" in `test.txt` file, else it will fail (non-zero return code).

You can start bisect session in one line `git bisect start HEAD v1.0` (first you put the first known bad, then the last known good). Now, you can tell bisect to run the test script

```bash
$ git bisect run ./test.sh
```

You will find the broken commit in less than a second.

Don't forget to end bisect session with `git bisect reset`
