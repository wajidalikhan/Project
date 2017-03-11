  
  Please feel free to add more to it and please don't forget to creat a pull request.
  git clone git@github.com:wajidalikhan/Project.git
  -------------------------------------------------------
  
  Check your Kernal version
  -- uname -r
  
  Update the grub
  -- sudo update-grub
  
  Download the following:
  -- sudo apt-get install openafs-client
  -- sudo apt-get install openafs-modules-dkms
  -- sudo apt-get install openafs-krb5
  -- sudo apt-get install krb5-user
  -- sudo apt-get install krb5-config
 
  Generate the keytab
  -- ktutil
  -- ktuil: list
  -- ktutil: addent -password -p wajid@CERN.CH -k 1 -e aes256-cts
  -- ktutil: addent -password -p wajid@CERN.CH -k 1 -e arcfour-hmac-md5
  -- ktutil: wkt .keytab
  -- ktutil: q

  Check if the keytab works
  -- kinit -kt .keytab wajid

  If nothing appears in your prompt, it works. Move your .keytab 
  file to /etc/ and rename it to krb5.keytab.

  Use "cern.ch" as default AFS cell
  -- sudo echo "cern.ch" > /etc/openafs/ThisCell

  Setup kerberos5 authentication:
  -- sudo wget http://linux.web.cern.ch/linux/docs/krb5.conf -P /etc 

  Open the /etc/ssh/ssh_config
  HOST lxplus.cern.ch
    ForwardX11 yes
    ForwardX11Trusted no
    GSSAPITrustDNS yes
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials yes

  Renew your token automatically, Open the file /etc/crontab and add the following line:
  -- @daily ID=afstoken kinit --renew
  
  Kerberos only works if your computer clock is in close sync within 
  5 minutes with CERN time servers. 
  -- sudo ntpdate ntp.ubuntu.com

  Install the ntp daemon, which will continuously keep your clock in 
  accurate sync with the CERN time servers.
  -- sudo apt-get install ntp 

  Add the following lines to your /etc/ntp.conf file, and comment the 
  lines for ubuntu time servers:
  # CERN Client
  server 137.138.18.69 version 4 #IP-TIME-0
  server 137.138.16.69 version 4 #IP-TIME-1
  server 137.138.17.69 version 4 #IP-TIME-2
  #Disable remote access, but trust sources of time restrict default nomodify #noquery 
  
  restrict default nomodify noquery
  
  #Allow hosts to query stats and ask for the time.
  #eg restrict 123.123.123.123 nomodify
  #Allow localhost to do everything.
  restrict 127.0.0.1
  #logconfig=all

  Then restart the ntp service:
  -- sudo service ntp restart

<<<<<<< HEAD
  Make sure you have properly generated the SSK keys, if not please follow the link
=======
  Adding the following line in my .bash_aliases file: 
  -- alias afs="kdestroy && kinit -kt /etc/krb5.keytab wajid -l 7d -r 1d ; aklog CERN.CH"
   
  Debugging:
  -- Restart the console so your alias will work.
  -- Restart the AFS client: sudo service openafs-client restart.
  -- Login with the alias you chose (make sure you get ticket and token).
  -- Make sure the clocks are synced 
  
  Useful links:
  https://gist.github.com/wajidalikhan/dc71972a6b9332cf9871b9f0f859b75f
  http://akorneev.web.cern.ch/akorneev/howto/openafs.txt
  -------------------------------------------------------

  
  The project is meant for testing the Git repositories and some 
  of the basic commands are listed. Please feel free to add more 
  commands with some short explanation and then please don't forget 
  to create a pull request. 
  -------------------------------------------------------
  
  Make sure you have properly generate SSK keys, if not please follow the link
>>>>>>> 1a93d7660ad68d17564bcebf64ceb8cbcb749dd6
  https://help.github.com/articles/generating-ssh-keys/

  Generate the SSH keys
  -- ssh-keygen -t rsa -b 4096 -C wajid@cern.ch

  Check if the generated keys are present
  -- ls -al ~/.ssh   
 
  Start the ssh-agent in the background
  -- eval "$(ssh-agent -s)"

  Add them to ssh agent
  -- ssh-add ~/.ssh/id_rsa 

  Testing your SSH connection
  ssh -T git@github.com
	
  List of various topics from Github
  https://help.github.com/index.html
  
  To creat a git repo from command line
  -- curl -u 'wajidalikhan' https://api.github.com/user/repos -d '{"name":"Hello"}'

  Check if the git is installed if not, get it done like
  -- sudo apt-get install git

  Activate the colors:
  -- git config --global color.ui auto 
  
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
  
  Always update your working directory to get the latest code
  -- git pull

  To undo the changes in Index before committing
  -- git reset HEAD
  
  To rename a folder 
  -- mv oldfolder newfolder
  -- git add newfolder 
  -- git rm oldfolder
  
  Or 
  -- git mv oldfolder newfolder 

  To clean the untracked files from git
  -- git clean -f ( But beware ... there's no going back). Instead use 

  -- git clean -n (to preview the damage you'll do) 

  To remove directories 
  -- git clean -f -d or git clean -fd

  To remove ignored files 
  -- git clean -f -X or git clean -fX

  To remove ignored as well as non-ignored files
  -- git clean -f -x or git clean  -fx

  To fast-forward if you are behind 
  -- git merge --ff-only origin/master
 
  To detect differences between local repo and remote repo in git? 
  commit your changes on your own branch, totally unrelated to what's 
  going on in remote repositories.          
  -- git commit
  
  Get the contents of the remote repository, but keep them under 
  origin/branch branches. Your own code is unaffected at this point
  -- git fetch origin

  Merge origin/master which is the master branch of the remote 
  repository origin(which you fetched just now) with your current branch
  -- git merge origin/master
  -- git push origin: push back the commit and the merge to the remote repository
  
<<<<<<< HEAD
=======
  To answer your second question:
>>>>>>> 1a93d7660ad68d17564bcebf64ceb8cbcb749dd6
  -- git fetch origin: update origin/branch branches.
  
  To get the difference between your current branch and the branch origin/master:
  -- git diff origin/master

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
  -- origin git@github.com:wajidalikhan/Project.git (fetch)
  -- origin git@github.com:wajidalikhan/Project.git (push)
  
  Now add new remote from where we forked the repo 
  -- git remote add upstream git@github.com:wajidalikhan/Project.git
  -- git remote -v 
  
  You should now have something like this
  -- origin git@github.com:wajidalikhan/Project.git (fetch)
  -- origin git@github.com:wajidalikhan/Project.git (push)
  -- upstream git@github.com:wajidalikhan/Project.git (fetch)
  -- upstream git@github.com:wajidalikhan/Project.git (push)
  
  Now copy/create or write any file here like
  -- touch anytextfile.txt
  -- git add anytextfile.txt 
  -- git commit -m "Testing"
  -- git push origin

<<<<<<< HEAD
  Now, you can just creat a pull request from the git hub page
  ==========================
=======
  You can just creat a pull request from the git hub page
  -------------------------------------------------------
>>>>>>> 1a93d7660ad68d17564bcebf64ceb8cbcb749dd6
 
  Usefull Weblinks for Git usage:
  http://rogerdudler.github.io/git-guide/ 
  https://github.com/github/hub
  http://blog.trobrock.com/2011/11/17/git-hub-and-pull-requests-equals-awesome-daily-workflow.html
