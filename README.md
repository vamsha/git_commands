# git_commands

A few general things to remember before you push to develop.
1.	Squash your commits to a single commit before merging to develop.
2.	Keep the commit message to a single line if possible. Add more info in the Jira. Include the Jira number in the commit message. A sample below
      "<JIRA_number>: <message>"

A typical sample work flow looks like below.

	* Branch off from origin/develop
    		* git fetch origin
    		* git checkout -b <new_branch_name> origin/develop
	* Make your changes in <new_branch_name>. Commit as often as you want
	* Run nose tests, pylint etc.
	* When you are ready for pushing to remote, squash your commits to a single commit
    		* git rebase -i <commit_id_of_origin_develop>
	* But origin/develop may have shifted to a new commit since someone else may have made a checkin. So fetch it and rebase
    		* git fetch origin develop
    		* git rebase origin/develop
	* Now you should see your single commit on top of latest commit in origin/develop
	* git push origin <new_branch_name>
	* Request PR
