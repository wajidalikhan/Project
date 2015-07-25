The project is meant for testing the Git repositories 
and some of the basic commands are listed. Please feel free to 
add more commands with some short explanation and don't hesitate 
to create a pull request. 
============================
  
  To initialize a local working copy 
  -- git init
  
  To add a file 
  -- git add <filename>
  
  To commit changes 
  -- git commit -m "first commit"
  
  To select the remote server to push your changes
  -- git remote add origin git@github.com:wajidalikhan/Project.git
  
  To check the remote server
  -- git remote -v

  To push your changes to the selected remote server
  -- git push -u origin master
  
  Always update your working directory to get the last code
  -- git pull
        
  In case,something goes wrong you can replace local changes using the e.g.,
  -- git checkout README.txt 

  To create a branch 
  -- git checkout -b new_branch

  To switech to newly created branch
  -- git checkout new_branch

  To list the number of branches 
  -- git branch -r

  To push the changes in a specific branch
  -- git push --set-upstream origin new_branch  OR 
  -- git push origin new_branch

  To Delete a branch
  -- git branch -d new_branch

  To mergre two branches
  -- git merge origin/new_branch

  To view log 
  -- git log
  
  To unstage the commit
  -- git reset HEAD <file>           
  
  To check the status of your working copy
  -- git status  
  
  To creat a pull request
  -- mkdir Testing
  -- cd Testing
  -- git init
  
  Now search git e.g., wajidalikhan/Project and fork this directory 
  then clone this forked directory form your git 

  -- git clone git@github.com:wajidalikhan/Project.git
  -- git remote -v
  
  You should have some thing like 
  -- origin git@github.com:YOUR_USERNAME/Project.git (fetch)
  -- origin git@github.com:YOUR_USERNAME/Project.git (push)
  
  Now add new remote from where we forked the repo 
  -- git remote add upstream git@github.com:wajidalikhan/Project.git
  -- git remote -v 
  
  You should now have something like this

  -- origin git@github.com:YOUR_USERNAME/Project.git (fetch)
  -- origin git@github.com:YOUR_USERNAME/Project.git (push)
  -- upstream git@github.com:wajidalikhan/Project.git (fetch)
  -- upstream git@github.com:wajidalikhan/Project.git (push)
  
  Now copy/create or write any file here like
  -- touch anytextfile.txt
  -- git add anytextfile.txt 
  -- git commit -m "Testing"
  -- git push origin

  You can just creat a pull request from the git hub page
             
