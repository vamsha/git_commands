# git_commands

Team,
  A few general things to remember before you push to develop.
1.	Squash your commits to a single commit before merging to develop.
2.	Keep the commit message to a single line if possible. Add more info in the Jira. Include the Jira number in the commit message. A sample below
      "<JIRA_number>: <message>"

A typical sample work flow looks like below. Say you are working on Jira AP-1187. 

1.	Branch off from origin/develop
	      git fetch origin
  	    git checkout -b <new_branch_name> origin/develop
2.	Make your changes in <new_branch_name>. Commit as often as you want
3.	Run nose tests, pylint etc.
4.	When you are ready for pushing to remote, squash your commits to a single commit
        git rebase -i <commit_id_of_origin_develop>
5.	But origin/develop may have shifted to a new commit since someone else may have made a checkin. So fetch it and rebase
        git fetch origin develop
      	git rebase origin/develop
6.	Now you should see your single commit on top of latest commit in origin/develop
7.	git push origin <new_branch_name>
8.	Request PR
