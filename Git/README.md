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
   $ git reset HEAD ^  
   ```





   ### Configuration
   ```bash
   $ git config --global user.name "coolseaweed"
   $ git config --global user.email "jeellato@gmail.com"
   $ git config --list # can be changed at ~/.gitconfig
   ```



   
   ### Ignore
   ```bash
   $ echo '<ignore_filenane>' >> .gitignore 
   $ git add .gitignore
   ```


---
  
  
  
  
  
  
  
