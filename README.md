# My little git tutorial v.01  
[TOC]
  
++**Goal:**++  
  - Explain on exmples how to use git  
  - Show usage of the tool  
Not goal:  
  - sell git and tell how awesome it it  
  - make another useless tutorial leaving you in bush  
  
#### -1) Remember:  
Git has awesome built in readme, use "git <command> help" to get info   
even before googling it out. ( ls and / in it will help you a lot)  
  
#### 0) What is that?  
Git is a system control version. You will find more on wiki.  
  
##### 0.1) What do I need to know:  
It's a distributed controll version system. Which means you work on your local  
repository copy all the time till you do not execute this three commands:  
- push  
- pull  
- fetch ( partially )  
That means as long as you do not execute this commands ( and delete .git dir )  
all the changes you make are revertible - by whole, or partially  
  
#####0.2) So what is hard?  
From my perspective the most useful and easiest in long term is to use git  
from commandline. Why? Because you clearly see what happens, you just don't  
when you use it from Tortoise or SourceTree - which Gui programs leave you  
with some magic happening.  
  
#####0.3) What about this magic?  
No magic really, once you grasp the basics you see that everything is in place.  
  
#####0.4) Finally, how:  
How it's always done - by step by step learning. Normally you do it by yourself  
thrown on deep water with some help from others, or none. This time? you do it  
by solving tasks.  
  
So lets the show begin.  
  
####1) Command: $git init  
  
This command initializes repository in directory you started it.  
It doesn't add any files etc. just creates empty repo. Now you can   
start using it. Another way to create repo is: git clone  
Which will be explained further  
```  
TASK:  
Initialize a repository in folder Start  
```  
>Additional info:  
>You see the repo with "ls -a"  
>You can get into .git dir with cd and look what's there  
  
####2) Command: $git add <something>  
  
That commands adds fields to be tracked by repository.  
When file is tracked, that doesn't mean that changes are tracked.  
  
~~~  
Warning:  
By default git doesn't track file setup - this mean your files will  
loose executable flag if you do not specify otherwise!  
Warning2:  
Windows git command shell adds executable flag for all checked out bats and execs etc.  
~~~  
  
<TODO>  
  
Examples:  
`git add *.cpp`  
`git add .`  
`git add <file name>`  
  
~~~  
Task:  
create file named main.cpp in Start catalog.  
In line 1: write "Hello Git", and add it to repo.  
~~~  
  
####3) Command: $git status  
  
One of the most used git commands, without that you would never know where  
you are!   
  
~~~  
Task:  
Check git status of repository in folder Start  
~~~  
  
>You should see that main.cpp is added to the repository, yet  
>changes are unstaged.  
  
####4) Command: git commit  
When you made your changes you have to commit that it's really what you want.  
This adds a traceable moment in git history - which means that you can always use  
code from that point, compare to it, know what exactly was changed and more.  
#####4.1)  
	When commit is being made you have to add note to it. It''s always seen as good  
    practice to mark your commit with short info, and after two newlines a longer one  
    if needed. fe:  
    `[Develop/bugfix-123] Communication problem solved`  
#####4.2)  
	You can either write "git commit" and use default git editor ( vim ), change  
    git default editor to other, or write  
    `git commit -m <Your message>`  
  
Examples:  
`git commit`  
`git commit -m`  
  
```  
Task:  
Commit your work in catalog Start  
```  
  
####5) Command: $git branch  
With initialized repository we have only one default branch - master.   
What's essential: There are two "types" of branch - remote and local,   
remote ones are being used for synchronization, and checking them out causes...  
literally cut of HEAD. ( good enough it can be stitched back just with branch   
creating ), local ones are for your casual - you create them, by default   
you have one called "master" ( the same as trunk in SVN )  
FIY: branches are being used to easily switch between different task, and not  
do that all at once. Also to model your code history.   
For more information I suppose you would love to read "merge vs rebase".  
For now we just want to have our branch to work on!  
  
>Branches are lightweight - these do not cost you, so use them (wisely)  
  
Usage:  
#####5.1) `git branch`  
    Shows all local branches in that repository, besides remote branches.  
#####5.2) `git branch -a`  
    Shows literally all branches, this means remote too. Really important  
    when you will want to work on branch you didn't have before and was  
    from another repository.  
#####5.3) `git branch -vv`  
	Shows branches with its parents  
  
Task:  
See how many branches you have in folder Start  
  
####6) Git clone  
Creating new repository is a rather seldom thing, you can be so happy only  
occasionally, more often you work with bunch of people in dispersed  
centralized way ( dispersed because in fact all of you have complete repo  
locally ) fe with some help of stash, github or maybe gerrit. For downloading  
someones repository git clone is being used - it copies the repository and  
connects it as a remote one - the origin. You can have many remotes, but  
origin is only one. You can manage all the connections etc. ofc.  
  
Usage:  
`git clone <link>`   
fe: `git clone https://www.github.com/someone/branch TODO`  
fe2: `git clone ../Start`  
  
Task:  
Clone Start to newly made Second beside it ( in Start type: mkdir ../Second)  
  
  
#### 7) Git checkout   
To move between branches and create new we use checkout command. It is greatly  
common but less than status.  
  
Usage:  
#####7.1)  
    `git checkout <from_branch> -b <to_branch>`  
    means from branch to_branch copy everything to newly made from_branch and  
    start working on it  
  
#####7.2)   
    `git checkout -b <to_branch>`  
    From branch I now do the same that in 7.1  
  
#####7.3)   
    `git checkout <to_branch>`  
    Switch from whatever branch I am in to to_branch  
#####7.4)   
    `git checkout -- <file>`  
    Revert changes in tracked file  
  
#####7.5)  
    `git checkout -- .`  
    Revert changes in all tracked files  
  
#####7.6)   
    `git checkout -- *.cpp`  
    Revert changed in all tracked cpp files ( <- as you see wild cards can be used)  
  
>Beware - you can not switch if you have unsaved work, because what git shall do   
>with it? Drop it? Save it somewhere? Or maybe send to space? You are the one to  
>decide!  
  
~~~  
Task:  
create new branch named Bugfix in repository in Start  
add second line to main.cpp "My work on Bugfix"  
Do not commit, and try to checkout to other branch - see what happens  
revert changes in main.cpp with checkout --  
Try to switch branches ( and get back to Bugfix)  
again add second line "My work on Bugfix"  
Commit your change ( git add -u | git commit -m "Your message" )  
Create new file lol.txt and do not add it to repository  
~~~  
  
####8) Git clean  
Many, many times you create temporary files in repository, this files (and uncommitted  
changes) will stop you from checking out to different branches. While you can delete  
them by hand - you do not need to. You can just clean the repo to state from last  
bare commit.  
  
Usage: ( My favorite)  
    `git clean -fd`  
    remove all unused files and catalogs from repository, have in mind that this  
    command does not work in global repository, but down from your actual  
    localization. You can decide to create branch or check status anywhere, but  
    if you clean from some top catalogs do not expect that some catalogs down  
    will be clean too.  
  
~~~  
Task:  
Clean your temporary files ( which is lol.txt ) in Start repository.  
Go into Second, to cloned Start repository  
~~~  
  
####9) Git pull  
Pull is used to actualize your repository to your origin ( or remotes if you specify TODO)  
If any tracked branch will be in conflicted state - you will have to merge that changes.  
This is not something you want to do always - that's why if that scenario happens it's better  
to not do that, but use git fetch - which will only update branches tracking remotes ( seen  
only with git branch -a as you remember )  
  
Pull will always fail when you have uncommitted changes! Commit, or drop changes before pulling.  
( Or stash )  
  
Usage: git pull  
  
~~~  
Task:  
Pull your recent changes in fatherly Start to Start you cloned.  
In cloned start check branches with git branch - what do you see?  
Now check with git branch -a  
Now add new origin/Bugfix branch as your own with: git checkout <bname> -b <bname2>  
If you do not know how - see git checkout again  
Add new change to main.cpp - change last word to "Bugmade" - commit it   
Go to parent Start repository, change last word to "Bugsiolololo" - commit it.  
~~~  
  
####10) Git merge : One big point worth of chapter  
So you happen to have two repositories, with the same files, and new different changes in it.  
Maybe you, and your colleague worked on the same bug, or needed the same functionality.  
So when you will try to update your repository it's only natural that three way difference  
will be shown, this three way difference is a natural cause of three way merge - when user has  
to decide what changes shall stay in his repository ( or even made new ones ).  
After merge is complete merge commit has to be made as a memorial to this fatal occasion.  
  
>Remember:  
>#####10.1) When you start merge you can always pause it - it will stop merging procedure, but  
>it won't change repository state. To continue merge:  
>        `$git merge --continue`  
>and to abort merge:  
>        `$git merge --abort`  
>After merge abortion you might want to clean your repository  
  
>#####10.2) Merging binary files is most often a mess, it's better to select one from "theirs" of "ours"  
>#####10.3) Merge ends with merge commit. That means that you can merge and merge again one  
>file as many times as you wish. It also means that you can add manual changes to the code.   
>Fe: #warning During merge I might broke something"  
>#####10.4) Use mergetool - it will nicely show you what are the changes, and automatically solve   
>many conflict. You have to browse it though - machines also makes mistakes. (Although you will  
>see the problems during compilation most often).  
  
######Mergetools:  
~~~  
I personally used: kdiff, meld, vimdiff. (first two window programs, last one terminal program )  
kdiff: installation on windows automatically connects everything you want, that means you have  
it added to path, and added to .gitconfig. On Ubuntu installation adds it to path, it even adds   
it to .gitconfig.  
kdiff has a really neat conflicts solver and is easy to navigate through, conflict postprocessing  
is awful though ( major con: look for <ctrl-z> )  
meld: much nicer window than in kdiff - in comparison, an eye candy, also nice when it comes to  
automerging, postprocessing is better  
vimdiff: well... no automate, but it's great to edit difficult merges and for small daily updates  
it has all the cons and pros of vim - you have to be a bit perverted to use it :) ALso you need  
a special colors setup just for it in .vimrc , because your standard one won't look good here  
~~~  
  
Setting mergetool:  
If you do not have mergetool set, you have to edit your .gitconfig and add:  
[merge]  
    tool = <your_tool_of_choice>  
  
If you really need to do that in notepad you will see files with:  
`<<<<<<<`  
`<code >`  
`=======`   
`<code2>`  
  
  
You want to know what it is? google ;)  
  
Commands:  
Merge other branch to ours  
`$git merge <other_branch_name>`  
Cancel this madness:  
`$git merge --abort`  
Restore file to state form before merge (while you did not commit the change )  
`$git checkout -m <file>`  
When you solved conflicts:  
`$git merge --continue`  
When you solved conflicts, there are no more things to merge, and are happy with the result  
`$git add -u && git commit`  
  
~~~  
Tasks:  
1: Create conflict in between: Second/Start/main.c and Start/main.c if you didn't yet.  
TIP: both have to have a new commit which the other one doesn't have.  
2: Install and configure your mergetool of choice, I would suppose kdiff for windows and meld on linux  
3: Pull one repo to another ( Second/Start: git pull will work right out of the box - as it has remote  
origin set ). You will expect merge, and conflict.  
4: Solve conflicts  
5: Commit your changes  
~~~  
  
######Important notice:  
When you merge stuff it's very important that before you commit and push your changes to other  
repositories to check if it still, at least, compiles. Better - passes code tests you obviously  
write :)  
  
####11) Git push:  
You can pull stuff, merge changes, so now you need ability to push your changes to another repository.  
To that you: have to have this repository added ( added by default if you cloned it ) and it's most often  
nice to have remote branches pinned to your actual branches (these are if you created them from origin/<brachname>  
Push changes the remote repository, always use with caution, never use with -f (force). ( With some exceptions)  
  
Command:  
`$git push`  
`$git push <where> <localbranch>:<remoteone>`  
fe: `git push origin LocalMess:Mess will create Mess branch on the remote`  
You delete branches on remote that way to:  
`$git push <where> --delete <branchname>`  
But to delete you can use:  
`$git push <where> :<branchname>`  
  
Task:  
After merge you have conflicts solved in one branch, but not in other -   
push changes from Second/Start/ to Start/ repository.   
  
####12) Git fetch  
Fetch is a way to first load changes from repository and than decide what to do with them.  
You know that you can merge them into, you do not yet know that you can rebase them ( warning - unsafe operation )  
But in general - its always better to decide what you add today, and what another time.  
In general: fetch updates only remote contents  
Usage:  
$`git fetch`  
  
####11) Git stash  
It quite often happens that you forgot to switch to the actuall branch you want to  
work on, do not want to make some funny merge, or think that this changes are nice,  
but want to check something other on that branch. For that reason you can use stash.  
  
`git stash`  
`git stash message`  
`git stash list`  
`git stash pop`  
`git stash pop stash@{2}`  
`git stash add stash@{1}`  
  
####14) Git rebase  
Rebase is a great command, but has to be used with caution. By rule of thumb - never rebase branch  
on which works more than one person. Rule of thumb two: use rebase on dialy basic to update your  
work branch to keep that branch updated. It doesn't generate a commit the way like merge, and   
rewrites history - adds commits from remote and write your commits on top of them. When you have  
conflict needing merge, and have more than one commit locally it's nearly always better to merge   
instead rebase that changes.  
First warning:  
You and colegue work on branch, one of you updates that branch if there are conflicts to solve   
and you use merge - merge will be done only once, if you decide for rebase - first one of you will rebase  
then other will have conflicts when he pulls your shared branch!  
But:  
When you work alone on functionality, than instead of constant merges (and it's commits) with master  
its more comfortable to rebase it. ( and avoid 3 merge commits for 6 commits in branch total )  
Finally:  
Rebase needs -f on push to the remote, which means it's a terribly unsafe operation. Fe. you can...  
remove your colleague changes from remote because you didn't check that your branch is still behind, and  
rebased to whatever else. He will have conflict on history, and when he decides that maybe he broke  
his branch so he will stash changes, delete local branch and download remote anew instead clean start  
he will have a huge mess.  
