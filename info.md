
						#################
						#  Information  #
						#################





#The project is updated as far as possible.
#The project contains information about my experience in using various technologies and commands.
#In the file, you can find brief information, instructions, commands, tips and descriptions of technologies in your own words.

#Now there are 3 branches in the file: Git, AD, Linux.
#In the future, I plan to add information about: BASH, PowerShel, Anseble, Doker, Requests QSL, HTML and CSS.





						#######
						# Git #
						#######

#Git is a VCS - Version Control System. Git takes a snapshot of the files and keeps track of the difference between changes.


--install git
	sudo apt install git


--patch settings config
/etc/gitconfig  - contains global settings
~/.gitconfig   or   ~/.config/git/config  -  contains user local settings.





--first settings git
Add user name
	git config --global user.name "Nikolay Miroshnichenko"
Add user email
	git config --global user.email merikboss@gmail.com
Add core editor
	git config --global core.editor nano

--Add git alias
	git config --global alias.br branch
	git config --global alias.ci commit
	git config --global alias.st status
	git config --global alias.last 'log -1 HEAD'
	git config --global alias.visual "!gitk"





--Start in git.
	git init

# Status
--Check Status comands:
	git status
Chech Changes: (--staged or --cached comparison of indexed files)
	git diff
Comparison in the graphic utility
	git difftool
Show Changes in tag
	git show NAME_TAG	
Show commit on hash
	git show "a21e1d"
Show hash commit
	git rev-parse NAME_BRENCH
Show history commands
	git reflog
Show commit N ago
	"git show HEAD@{2.months.ago}
Show perent commit
	git show HEAD^	or git show HEAD~
#Merge commit have 2 perent. "HEAD^" "HEAD^1"








--Log
	git log
	git show NAME_COMMITE

Log: 
(--patch -1|-p 1 			show diff between commits
 -(n)					show last number of commits
 --shortstat 				show short statistics 
 --pretty=oneline =format 		сhoosing the format for providing statistics
 --graph 				graphic display

 --since 				shows commits after the specified date.
 --after 				

 --committer				show all commits of a committer or commiter 

 --until				shows the author of the commit
 --before

 --grep "TEXT_FOR_GREP"			show text in logs					
 -S 					show commits with the right mention
 --name-only				show list of changes after commit
 --name-status				shows a list of files that have been added/changed/removed
 --abbrev-commit			shows the abbreviated check-sum SHA-1
 --relative-date			show date in format
)

#Status file: commited, modified, staged, untracked, unmodified.

Show commit From To
	git log BRENCH1..BRENCH2 

Show alles commits From commit A B C bat not D
	git log ^refA refD	or	git log refB --not refD

Show commits in A brench and brench B.
	git log master...experiment 	or	got log --left-right BreanchA...BreanchB

--GREP
	git grep
{
-n	number line
-c	count file
-p	count function	

--and
--or	Logic operators
--not

--breake	Add breake in line
--heading	Show name files above found lines
}
	" git grep --break --heading -n -e '#TEXT1' --and \(-e TEXT2 -e TEXT3 \) NAME_TAG "



--Binary found

	git bisect start
	git bisect bad
	git bisect good NAME_TAG

	git bisect reset

	git bisect start HEAD TAG_NAME
	git bisect run SCRIPT.SH	-	run script





--Working with index
	git add "FILE_NAME"

--interactive mod
	git add -i

Stash
	git stash 
	git stash apply --index
Stash + .ignore
	git stash --include-untracked
Stash interactive mod
	git --patch
Create stash breanch
	git  stash branch NAME_BRANCH

Dell stash
	git stash pop



--Commit

	git commit -m "You commit"
	git commit -a -m "You commit fast ADD file"
	git commit -v "ADD IN COMMIT - DIFF"

--Substitution or rename commit
	git commit --amend




# Tags

#There are two kinds of tags.

# - Lightweight - have name tag
# - Annotated - have name tag, date, info changes, name author, commit.

	git tag
Tag list
	git tag -l
Add tag in commit
	git tag -a NAME_TAG HASH_COMMIT
-m 					add messege in tag

--Tags in remote
	git pust NAME_REMOTE --tags

Delete local tag 
	git tag -d TAG_NAME
Delete remote tag
	git push NAME_REMOTE --delete TAG_NAME





#Delete
Delete git file

Delete file in index
	git rm FILE_NAME	or	git restore --staged NAME_FILE
Deleting a file if it is added to the index
	git rm -f FILE_NAME
Seve file and add to ignore
	git rm --cached FILE_NAME


	


#Move and rename
Move or rename files
	git mv OLD_FILE_NAME NEW_FILE_NAME





# Work with Remote

Clone
	git clone PROJECT_LINK
Show remote list
	git remote -v
Add remote
	git remote add NAME_REMOTE PROJECT_LINK
Fetch - take new version project
	git fetch NAME_REMOTE
Pull - push my new version project
	git push NAME_REMOTE NAME_BRANCH
Show new version project
	git remote show NAME_BRANCH

Get the changes from the remote repository to the newly created branch.
	git checkout NAME_REMOTE/NAME_REMOTE_BRANCH -b NAME_NEW_BRANCH

Remote rename
	git remote rename OLD_NAME_REMOTE NEW_NAME_REMOTE





# Work with branch

#Default branch - master
#Default remote - origen


Create new branch
	git switch -c NAME_BRANCH 
	git checkout -b NAME_BRENCH
Switch on new branch
	git switch NAME_BRANCH
	git checkout NAME_BRANCH

# Commit have in hash sum:
# commit 
# tree
# perent
# author 
# committer

# Tree have blob - hash cum files


Filter-branch - can delete file in project.
	git filter-branch --tree-filter 'rm -f FILE_NAME.TXT' HEAD


# script edit email in project #

	git filter-branch --commit-filter '
#	if [ "$GIT_AUTHOR_EMAIL" = "VasyPupkin@localhost" ];
#	then
#		GIT_AUTHOR_EMAIL="DanilNePupkin";
#
#	GIT_AUTHOR_EMAIL="DanilNePupkin";
#		git commit-tree "$@";
#	else
#		git commit-tree "$@";
#	fi' HEAD





# Work with Branches
	git branch NAME_BRANCH

--merge
#There are two ways to merge:
#Fast-Forvord - (_A_)---(_B_) <HEAD

#Recursive - (_A_)---(_B_) <HEAD OLD ---(_D_) <HEAD NEW
#	        \			 /
#		 \			/
#		(_C_)-------------------


	"git checkout MASTER"
	git merge LAST_BRANCH

--delete merge commit 
	git reset --hard HEAD~
--cancel commit
	git revert -m 1 HEAD






--remote merge
	git merge REMOTE_NAME/REMOTE_BRANCH

# Work with Rebase

#	     (_A_)---(_B_) <HEAD OLD ---(_D_)' <HEAD NEW
#               \                        *
#                \                      *
#               (*C*)******************* (Delete)


	git rebase A B

	"git rebase --onto A B C"
	"git checout MASTER"
	"git merge C"

Interactive mod
	git rebase -i HEAD~3

{
p - use commit
r - use commit and edit the commit message
e - use commit, but stop for amending
s - use commit, but meld into previous commit
f - like S but, discard this commit`s log
x - using shell 
}




# Huks


--patch hooks
.git/hooks

# Class huks: Server, Client.

# Huks have levels: per-commit, prepare-commit-msg, commit-msg

# pre-commit 
# - Runs before the commit message.
# - You can perform simple code checks: simple tests, code style, and more. 
# - Ingnored by the flag - --no-verify:
	'git commit --no verify'



# prepare-commit-mgs
# - Fires before the message editor is called, but after the standard message has been created.
# - Allows you to change the standard commit messages.



# commit-msg
# - Takes as input the path to a temporary file with a commit message.
# - Allows you to validate a commit message based on patterns.



# Email huks: applypatch-msg, pre-applypatch, post-applypatch.
# And more: pre-rebase, post-rewrite, post-checkout, post-merge, pre-push.

# pre-rebase
# - may prevent rebase


# pre-rewrite
# - run "git commit --amend" and "git rebase"
# - may prevent rebase


# post-checkout
# - may prevent pust




# Server huks:

# pre-receive
# - Works when receiving data from the clien
# - Unchecks all changes
# - Quick code check or commit message


# update
# - Works when receiving data from the clien all branch
# - Unchecks changes in Branches
# - Checking user permissions to push to a branch!

# post-receive
# - Notification of external services 




----------------------------------------------------------------


