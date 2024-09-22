Most recently, I was trying to get git and github working on my linux machine so that I can edit these projects in the terminal and not have to deal with them through something like VSCode.
While I have done this in the past, I forget the steps I need to take quickly because I don't practice them as much.
Hopefully these projects increase the frequeny with which I have to do these things.

One of the things I did that differ from many other times is that I used something known as "gh auth login".

According to a section of the [github manual](https://cli.github.com/manual/gh_auth_login):

```
gh auth login [flags]
```
>Authenticate with a GitHub host.
>
>The default authentication mode is a web-based browser flow. After completion, an authentication token will be stored securely in the system credential store. If a credential store is not found or there is an issue using it gh will fallback to writing the token to a plain text file. See gh auth status for its stored location.

I thought this would allow me to perform git actions on my github repo without configuring git with a global email and username, but it seems like, based on my approach, that was not the case.

Regardless, in order to document my mistakes, I will list the order in which I did things, edited to be slightly more correct.

1. `sudo apt install gh`
2. `gh auth login -w`
- I pass the -w flag to open a web browser for the github authentication
3. `gh auth status`
- To verify that I am authenticated 

4. `git status`
- TO see what changes were mamde and what branch I'm on

5. `
    git config --global user.email "noreply@github.com"
    git config --global user.name "[name]"
   `

6. Note: Learn more about ssh-keygen
`ssh-keygen -t ed25519 -C "your_email@example.com"`
- Save the key in a good place
- Add the public key to github account settings
- Email must match one of the emails associated with the github account, or a noreply email provided by github

7. `gh auth setup-git`

8. `git add .`
- To stage all the changes in the repo
9. `git commit -m "[Message]`
10. `git push origin main`


I ran into some issues regarding publishing private email addresses, so I had to fix this by doing
`git commit --amend --author="Author Name <noreply@github.com>"`

Then everything seemed to work okay.
I'm still not sure if `gh auth` did anything meaningful.
