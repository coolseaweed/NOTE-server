# Git guide
   [Deploy key](#content1)
   
   [Push & Pull](#content2)


## Deploy key <a name="content1"></a>


   ### ssh-keygen
   ```bash
   ssh-keygen -t rsa -b 4096 -C ${your_e-mail}
   -------------------------------------------------------
   Generating public/private rsa key pair. 
   Enter file in which to save the key (/Users/Home/.ssh/id_rsa): /Users/Home/.ssh/id_rsa_${repo_name}
   ...
   -------------------------------------------------------
   
   ssh-agent -s
   ssh-add ~/.ssh/id_rsa_${repo_name}
   
   # add ~/.ssh/id_rsa_${repo_name}.pub to repositoy deploy key
   ```
   
   ### multi repository in same server
   ```bash
   touch ~/.ssh/config
   --------------------------------------
   # repo-1
   Host github.com
      HostName github.com
      User ${USER}
      AddKeysToAgent yes
      IdentityFile ~/.ssh/id_rsa_${repo-1-name}

   # repo-2
   Host github.com
      HostName github.com
      User ${USER}
      AddKeysToAgent yes
      IdentityFile ~/.ssh/id_rsa_${repo-2-name}
   
   ...
   ----------------------------------------------
   ```
   
   ### ** Trouble shooting
   `Could not open a connection to your authentication agent` 라고 권한 문제가 생길경우
   ```bash
   eval $(ssh-agent)
   ```
   


## Push & Pull <a name="content2"></a>

   ### Push
   ```bash
   git status # check current status
   git add <file|dir.> 
   git commit -m "message"
   git push 

   # commit cancel
   $ git reset HEAD <staged file|dir.>
   ```
   ### Pull
   ```bash
   git stash # save current changes
   git pull
   git stash apply 

   # confilct happend, resolve conflicts and commit again
   ```
   
   


   ### Github repository <--> local directory 
   ```bash  
   $ cd /to/your/project/dir/
   $ git init
   $ git remote add origin <git url>
   $ git push -u origin master
   ```







   ### Configuration
   ```bash
   $ git config --global user.name "coolseaweed"
   $ git config --global user.email "jeellato@gmail.com"
   $ git config --list # can be changed at ~/.gitconfig
   ```



   
   ### Ignore files
   ```bash
   echo -n > .gitignore # write down unwanted file list
   ----------------------------------------------------
   .idea/
   *.log
   db.sqlite3
   . . .
   ----------------------------------------------------
   git add .gitignore
   ```




---
  
  
  
  
  
  
  
