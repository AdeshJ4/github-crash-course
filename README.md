version control system 
-> It is used to track and manage software code changes.
-> eg. git, Apache SubVersion, Piper(used by Google)

-> git is a free and open source distributed version control system.


-> Local changes(Modified) -> Staging area(git add .) -> commit(git commit -m "")


git --version
git version 2.32.0.windows.2

 
1. git init
2. git add index.js
3. git add .
4. git commit -a -m "commit-1"
5. git rm --cached .\index.js
6. git diff
7. git log
8. git log --oneline
9. git show 562f7a5
10. git blame index.js
11. git reset --hard 2717dd9  (revert commit)  -> all commits after this commit will disappear
12. git revert 562f7a5  -> This will do opposite of this commit(if you add something or remove something then it will do opposite) 
and will create new commit.
13. git revert -m 1 ac04681 -> This is merge commit
14. git push -f   -> forcefully push 
15. git branch  -> list all branches
16. git branch b1 -> Create new branch called b1.
17. git checkout b1 -> Switch to branch b1 
18. git checkout -b "feature-1"  -> Shortcut (directly create and switch to branch)
19. git checkout feature_Name
20. git merge feature_Age

Delete:
21. git branch -d branch_name   -> local branch
22. git push origin --delete branch_name  -> server branch


git stash:
you are working on your task and you want latest code but you don't want to "git add" ot commit you current task how you can do this?
for this situations we can use stash.
23. git stash
24. git pull
25. git stash apply





on server -> git pull request -> merge my b1 branch into master branch
Pull request successfully merged and closed

on local machine -> git pull -> whatever changes inside server master will be downloaded inside local master.






Branch naming conventions: 
=========================
-> Use grouping tokens (words) at the beginning of your branch names
-> Use slashes to separate parts of your branch names
-> Avoid long descriptive names for long-lived branches.

Group tokens

Use "grouping" tokens in front of your branch names.

group1/foo
group2/foo
group1/bar
group2/bar
group3/bar
group1/baz

The groups can be named whatever you like to match your workflow. I like to use short nouns for mine. Read on for more clarity.

-> Short well-defined tokens

Choose short tokens so they do not add too much noise to every one of your branch names. I use these:

wip       Works in progress; stuff I know won't be finished soon
feat      Feature I'm adding or expanding
bug       Bug fix or experiment
junk      Throwaway branch created to experiment

eg: 

git branch "feat/user-profile"
git branch "feat/payment-integration"
git branch "bug/fix-login-issue"
git branch "bug/404-page"
git branch "junk/experiment-css"
git branch "junk/temporary-test"

1. wip/: For branches representing works in progress that are not expected to be finished soon, you could use prefixes like wip/ 
followed by a descriptive name. For example:
wip/new-feature
wip/refactor-login

2. feat/: For branches representing features being added or expanded, you could use prefixes like feat/ followed by a descriptive 
name. For example:
feat/user-profile
feat/payment-integration

3. bug/: For branches representing bug fixes or experiments related to fixing bugs, you could use prefixes like bug/ followed by a 
descriptive name. For example:
bug/fix-login-issue
bug/404-page

4. junk/: For throwaway branches created for experimentation or testing purposes, you could use prefixes like junk/ followed by a 
descriptive name. For example:
junk/experiment-css
junk/temporary-test









git have only one job which is to manage commits. like git pull, git push.


Github -> Single source of truth -> Remote Server -> Kind of machine that runs 24/7 -> have installed git on it -> server have public 
IP Address / domain 
A sever where we can push or pull changes.
Github is free. 
Internally it is a server but it also gives us useful features.



name of the server is "origin" and its address is "git@github.com:AdeshJ4/github-crash-course.git"


we can add multiple remote. 
1st remote : origin -> git@github.com:AdeshJ4/github-crash-course.git
2nd remote : xyz -> git@github.com:AdeshJ4/vidly-course.git
multiple remotes are useful when you are doing open contribution.


PS E:\z Placement\GitHub\GitProj> git remote add origin git@github.com:AdeshJ4/github-crash-course.git
PS E:\z Placement\GitHub\GitProj> git remote -v
origin  git@github.com:AdeshJ4/github-crash-course.git (fetch)
origin  git@github.com:AdeshJ4/github-crash-course.git (push)
PS E:\z Placement\GitHub\GitProj> git push -u origin main   -> by default have master branch in my s code
error: src refspec main does not match any
error: failed to push some refs to 'github.com:AdeshJ4/github-crash-course.git'
PS E:\z Placement\GitHub\GitProj> git push -u origin master
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.




How to solve this problem: 
Generating a new SSH key and adding it to the ssh-agent
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights


Your identification has been saved in C:\Users\user/.ssh/id_ed25519.    private key
Your public key has been saved in C:\Users\user/.ssh/id_ed25519.pub.	public key


PS E:\z Placement\GitHub\GitProj> cat ~/.ssh/id_ed25519.pub 
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGLmn/z+rDIV3VyCMu+prM/GNzc8bzql8u4mS2BX8ykq adejad1234@gmail.com


how SSH keys work:

1. **Key Pair Generation:** SSH (Secure Shell) uses public-key cryptography. When you create an SSH key pair, you generate two keys: 
a public key and a private key. These keys are mathematically related, but information encrypted with one key can only be decrypted 
with the other.

2. **Public and Private Keys:** The public key is shared with other parties, while the private key is kept secret and stored securely 
on your local system.

3. **Authentication:** When you attempt to connect to a remote server using SSH, the server requests your public key. You provide 
your public key, and the server uses it to encrypt a challenge message.

4. **Challenge Response:** The server sends the encrypted challenge message back to you. You use your private key to decrypt the 
message and return the result to the server.

5. **Verification:** The server verifies that the response matches the original challenge. If it does, the server grants access to 
the user associated with the public key.

6. **Security:** Since the private key is never shared and is kept securely on your local system, SSH provides a secure way to 
authenticate and establish encrypted communication channels over unsecured networks, such as the internet.

In summary, SSH keys provide a secure method for authenticating and establishing encrypted connections between clients and servers, 
ensuring confidentiality and integrity of data transmitted over the network.



