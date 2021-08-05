# Git guide
   [1. Github](#1.-Github)

   [2. Gitlab](#2.-Gitlab)



## 1. Github <a name="1.-Github"></a>

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


   ### Repository deploy key (ssh-key)
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
   
   #### multi repository in same server
   
   ### ** Trouble shooting
   `Could not open a connection to your authentication agent` 라고 권한 문제가 생길경우
   ```bash
   eval $(ssh-agent)
   ```
   


---
  
  
  
  
  
  
  
