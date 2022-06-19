						#################
						#  Information  #
						#################

#The project is updated as far as possible.
#The project contains information about my experience in using various technologies and commands.
#In the file, you can find brief information, instructions, commands, tips and descriptions of technologies in your own words.

						#######
						# Git #
						#######

#Git is a VCS - Version Control System. Git takes a snapshot of the files and keeps track of the difference between changes.



--install git
	sudo apt install git


--settings patch
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




--Git start comand.
	git init


--Check Status comands:
	git status
Chech Changes: (--staged or --cached comparison of indexed files)
	git diff
Comparison in the graphic utility
	git difftool
Show Changes in tag
	git show NAME_TAG



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



Status file: commited, modified, staged, untracked, unmodified.

--Working with index
	git add "FILE_NAME"




--Commit

	git commit -m "You commit"
	git commit -a -m "You commit fast ADD file"
	git commit -v "ADD IN COMMIT - DIFF"





Substitution or rename commit
	git commit --amend

Status file: modified, commited, staged, untracked, unmodified.

--Tags

#There are two kinds of tags.

# - Lightweight - have name tag
# - Annotated - have name tag, date, info changes, name author, commit.


	git tag
Tag list
	git tag -l
Add tag in commit
	git tag -a NAME_TAG HASH_COMMIT
-m 					add messege in tag

Tags in remote
	git pust NAME_REMOTE --tags

Delete local tag 
	git tag -d TAG_NAME
Delete remote tag
	git push NAME_REMOTE --delete TAG_NAME
Create new branch
	git switch -c NAME_BRANCH 
Switch on new branch
	git switch NAME_BRANCH
	git checkout NAME_BRANCH



--Delete git file

Delete file in index
	git rm FILE_NAME	or	git restore --staged NAME_FILE
Deleting a file if it is added to the index
	git rm -f FILE_NAME
Seve file and add to ignore
	git rm --cached FILE_NAME

--Move and rename
Move or rename files
	git mv OLD_FILE_NAME NEW_FILE_NAME

--Remote

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

--Work with branch

Default branch - master
Default remote - origen


# Commit have in hash sum:
# commit 
# tree
# perent
# author 
# committer

# Tree have blob - hash cum files


Branch
	git branch NAME_BRANCH



----------------------------------------------------------------


