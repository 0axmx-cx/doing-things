In doing the simple
```
git add .
git commit -m "[Message]"
git status
git push origin main
```
I ran into an issue with not fetching first, causing the pish to get rejected due to remote changes.
I didn't remember making any remote changes, but I did git pull, which wanted me to deal with the divergent branches.
I want to merge in these cases at the moment, so I did `git config pull.rebase false` which is the default.

Here was the full hint for context:
>hint: You have divergent branches and need to specify how to reconcile them.
>hint: You can do so by running one of the following commands sometime before
>hint: your next pull:
>hint: 
>hint:   git config pull.rebase false  # merge (the default strategy)
>hint:   git config pull.rebase true   # rebase
>hint:   git config pull.ff only       # fast-forward only
>hint: 
>hint: You can replace "git config" with "git config --global" to set a default
>hint: preference for all repositories. You can also pass --rebase, --no-rebase,
>hint: or --ff-only on the command line to override the configured default per
>hint: invocation.
>fatal: Need to specify how to reconcile divergent branches.

After changing this, I did 
```
git pull
git fetch
git status
```
To see if things were okay. They seemed okay now.

Then I did `git diff origin..main` just to see what the difference was.
I knew what the difference was, but I wanted to practice to see what the output was.

Finally, I did `git push`, and everything was resolved.
