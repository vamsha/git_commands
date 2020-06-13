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


***************************************


When you do a pull request on a branch, you can continue to work on another branch and make another pull request on this other branch.

Before creating a new branch, pull the changes from upstream. Your master needs to be up to date.

$ git pull
Create the branch on your local machine and switch in this branch :

$ git checkout -b [name_of_your_new_branch]
Push the branch on github :

$ git push origin [name_of_your_new_branch]
When you want to commit something in your branch, be sure to be in your branch. Add -u parameter to set-upstream.

You can see all the branches created by using :

$ git branch -a
Which will show :

* approval_messages
  master
  master_clean
Add a new remote for your branch :

$ git remote add [name_of_your_remote] [name_of_your_new_branch]
Push changes from your commit into your branch :

$ git push [name_of_your_new_remote] [url]
Update your branch when the original branch from official repository has been updated :

$ git fetch [name_of_your_remote]
Then you need to apply to merge changes if your branch is derivated from develop you need to do :

$ git merge [name_of_your_remote]/develop
Delete a branch on your local filesystem :

$ git branch -d [name_of_your_new_branch]
To force the deletion of local branch on your filesystem :

$ git branch -D [name_of_your_new_branch]
Delete the branch on github :

$ git push origin :[name_of_your_new_branch]
The only difference is the: to say delete, you can do it too by using GitHub interface to remove branch: https://help.github.com/articles/deleting-unused-branches.

If you want to change default branch, it's so easy with GitHub, in your fork go into Admin and in the drop-down list default branch choose what you want.

If you want create a new branch:

$ git branch <name_of_your_new_branch>
