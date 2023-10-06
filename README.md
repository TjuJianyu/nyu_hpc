# nyu HPC tricks
about ssh connection, jupyter connection, sublime text, slurm, etc.

## Jupyter Notebook (with jumpter and slurm)

Network architecture: 
```Laptop A --> jumpter (gw.hpc.nyu.edu) --> hpc login node (greene.hpc.nyu.edu) --> hpc computation node (e.g. gr059, etc)```

- Step 1: Open a terminal on ```Laptop A```
  - ssh connect to ```hpc login node```,
  - require an internactive ```computation node``` by slurm (Let's assume the name of the ```computation node``` as ```gr059```).
- Step 2: Open another terminal on ```Laptop A```
  - Type in ```ssh -t -t -J <username>@gw.hpc.nyu.edu <username>@greene.hpc.nyu.edu -L <port>:localhost:<port> ssh <computation node name> -L <port>:localhost:<port>```
  - Replace ```<username>``` by your username, ```<port>``` by a number (e.g. 1025 ~ 32768), ```<computation node name>``` by the name of Step1 required node name.
- Step 3: On ```<computation node name>```
  - Start a jupyter notebook by typing in ```jupyter notebook --no-browser --port <port>```
  - Replace ```<port>``` by the port number in Step2.
  - It will output some URLs, like ```http://127.0.0.1:9099/?token=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx```
- Step 4: on ```Laptop A``` browser,
  - Copy and paste the URL.

  
