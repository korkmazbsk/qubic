# Linux apoolminer Tutorial

## Configuration 
### 1. First modify the configuration file miner.conf and change the account to your own.

<u>If you need to adjust other parameters, remove the # comment and modify the corresponding values according to the parameter description.</u>
```
algo=qubic
account= my_sub_account
pool=qubic1.hk.apool.io:3334
#worker=my_worker
#cpu-off=false
#thread=4
#gpu-off=false
#gpu=0,1,2
#mode=1
```
### 2. apoolminer miner.conf Parameter Description
| Param      | Description |
| --------------------- | ------------------------------------------------------------ |
| algo=&lt;qubic/aleo&gt;      | Specify algorithm, default configuration is qubic ,   **  Required**  |
| account=&lt;string&gt; | Specify you sub-account(CP_xxx) in pool mining or Specify you wallet address in solo mining,   ** Required**                     |
| pool=&lt;url:port&gt;     | Specify the  proxy address,   ** Required in pool mining ** |
| solo=&lt;url:port&gt;     | Specify the  proxy address,   ** Required in solo mining** |
| worker=&lt;name&gt;       | Specify the worker name. The name consists of numbers and letters and cannot exceed 15 characters in length |
| gpu=&lt;indexes&gt;             | Specify the index of GPU. If you're only running on specific GPUs, please spell out explicitly, example: gpu=0,1,2, If you run all GPUs, you don't need to configure them.|
| thread=&lt;num&gt;            | Specify the number of CPU thread [default: 0, use all threads] |
| cpu-off=&lt;true/false&gt;        | If you don't want to use CPU, please configure it to True.   |
| gpu-off=&lt;true/false&gt;        | If you don't want to use GPU, please configure it to True.  |
| mode=&lt;0/1&gt;           | Mining mode, 0 is normal mode, 1 is hybrid mode [default: 0],please make sure that the system has enough memory configuration in mode 1. |
#### Configuration file example
- Configuration files for mining with GPU and CPU (Recommended mining configuration for all resources)
  
  ```
  algo=qubic
  account=my_sub_account
  pool=qubic1.hk.apool.io:3334
  ```
  
  
  
- Configuration files for mining with GPU only
  
  ```
  algo=qubic
  account=my_sub_account
  pool=qubic1.hk.apool.io:3334
  cpu-off=true
  ```
  
- Configuration files for mining with CPU only
  ```
  algo=qubic
  account=my_sub_account
  pool=qubic1.hk.apool.io:3334
  gpu-off=true
  ```
- Configuration files for mining with GPU and open hybrid mode
  ```
  algo=qubic
  account=my_sub_account
  pool=qubic1.hk.apool.io:3334
  cpu-off=true
  mode=1
  ```
-  Configuration files for mining with CPU and specify the number of CPU thread
  ```
  algo=qubic
  account=my_sub_account
  pool=qubic1.hk.apool.io:3334
  gpu-off=true
  thread=8
  ```

## Run and shutdown
### 1. Select the execution script according to your needs
- [ ] Autoupgrade Start command

- 
If you want to run an automatic upgrade of apoolminer, you can execute the upgrade_and_run.sh script
```shell
sudo nohup bash upgrade_and_run.sh 2&gt;&1 &
```
- [ ] Manually operated Start command


- 
If you do not need to automatically upgrade apoolminer, you can execute the run.sh script
```shell
sudo bash run.sh
```

### 3. View apoolminer log
```shell
sudo tail -f qubic.log
```



### 4.shutdown apoolminer command
```shell
sudo killall -9 apoolminer
```
### 5.shutdown autoupgrade script

If you are running an automatic upgrade script, use the following command to shutdown and it will no longer be upgraded.
```
for i in $(ps aux|grep "upgrade_and_run"|grep -v grep |awk '{print $2}'); do sudo kill -9 $i; done
```

## Login in apool.io web

#####  wait a few minutes Watch the Statistics and earn QU's on Apool
