# Jupyter notebook 정리노트
   [1. 설명](#1.-설명)


## 1. 설명 <a name="1.-설명"></a>

  * ssh 터널링
  ```
  ssh -L [local_port]:localhost:[host_port] -p [router_port_num] [host]
  ```
  * jupyter 접속 and config 
  ```
  $ jupyter notebook --ip=0.0.0.0 --port=[port_num] --allow-root --generate-config
  
  or set
  ##### config: ~/.jupyter/jupyter_notebook_config.py #####
  c.NotebookApp.allow_root=True # sudo 
  c.NotebookApp.port = [host_port]
  c.NotebookApp.ip = '0.0.0.0'
  ```
  
