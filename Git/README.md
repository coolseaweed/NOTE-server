# Git 가이드
   [1. Github commands](#1.-Github-commands)

   [2. Gitlab commands](#2.-Gitlab-commands)



## 1. Github commands <a name="1.-Github-commands"></a>

   ### Github repository <--> local directory 
   ```bash  
   $ cd /to/your/project/dir/
   $ git init
   $ git remote add origin <git url>
   $ git push -u origin master
   ```

   ### Upload
   ```bash
   $ git status # check current status
   $ git add <file|directory> 
   $ git commit -m "message"
   $ git push 

   # commit cancel
   $ git reset HEAD^  
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


   ### ssh key <---> repo.
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   -------------------------------------------------------
   Generating public/private rsa key pair. 
   Enter file in which to save the key (/Users/Home/.ssh/id_rsa): /Users/Home/.ssh/id_rsa_${repo_name}
   -------------------------------------------------------
   ssh-add ~/.ssh/id_rsa_${repo_name}
   ```
   
   


---
  
  
  
  
  
  
  
