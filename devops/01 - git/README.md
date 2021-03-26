## Prerequsite

* Git 2.28 or greater

## Tasks

* fork the current repository

* clone it, find the commit "failed changes commit, revert me" and revert them! 

*Please note that after completing this task, the number of folders with tasks must change!*

* after passing all the questions from all folders, make a pull-request with the results of the task and the tag Done-current date (e.g. `Done-01-01-2021`)


## Questions

1. What command can I use to view the commit history?  
A(nswer):  
	git log  

2. What command can I use to undo the last commit?  
A:  
	Local keeping uncommitted source: 	git reset --soft HEAD~1  
	Local deleting uncommitted source: 	git reset --hard HEAD~1  
	Remote: 				git revert HEAD  

3. What command can I use to create a new branch and a new tag?  
A:  
	Create new branch: 	git checkout -b BranchName  
	Create new tag:		git tag -a vVersion -m "Message"  

4. How do I exclude a file / folder from a commit?  
A:  
	I generally use .gitignore file to specify exclusion list

5. In case of a merge conflict, what commands can be used to resolve it?  
A:  
	Find a conflict: 			git status  
	Resolve conflict in a text editor: 	joe, nano, etc.  
	Commit:					git commit -am "conflict resolution description"  
	Push:					git push  

6. `*` What are pre-commit hooks and post-commit hooks, and what are they for?
A:  
	These are event handlers for pre and post commit for running custom scripts for actions like verification and/or notification, etc.

7. `*` How do I change the last commit without adding a new commit?
A:  
	git commit --amend
	