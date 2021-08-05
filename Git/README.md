# Git guide
   [Deploy key](#content1)
   
   [Push & Pull](#content2)

   [.gitignore](#content3)


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
   
---

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

---

## .gitignore <a name="content3"></a>
   ```bash
   touch .gitignore # write down unwanted file list
   ----------------------------------------------------
   __pycache__
   log
   temp
   db.sqlite3
   . . .
   ----------------------------------------------------
   git add .gitignore
   ```

---
   
   

   ### Github repository <--> local directory 
   ```bash  

   $ git init
   $ git remote add origin <git url>
   $ git push -u origin master
   ```


---
  
  
  
  
  
  
  
