# MinerAgent

The miner proxy is installed on the mining machine to delegate the I/O between the mining kernel and the upper-level mining pool ensuring connection stability.

This agent software is impool specific.

Our website address: https://www.impool.io/


# Download

[Download here](https://github.com/impoolofficial/ImpoolProxy/releases)

## Port


The miner proxy uses the following ports, which is not necessarily to be public:

3301: stratum protocol port, used for mining kernel connection.

8001: http port, used to require proxy information.


## Feature

* Supports Windows & Linux.


## CMD Option

Options :

    daemon              starts as a daemon

    --pool-host         upper-level mining pool address，required, for example: eth.impool.io:6333

    --stratum-port      proxy stratum protocol port, default 3301

    --api-port          proxy api port, default 8001

    --debug             enable debug log, true: enable, false: disable, default: false


## Install Usages

### Linux

- **Unzip miner-agent-linux64-\*\*\*.tar.gz to get the following file:**
  
        tar -zxvf miner-agent-linux64-***.tar.gz

- **Change the linux_start.sh script to miner proxy address: eth.impool.io:6333:**

        vim linux_start.sh

- **Run the linux_start.sh script to start the service:**

        bash linux_start.sh

- **Check whether the miner proxy is set up successfully, 3301 is the stratum protocol port by default:**

        netstat -pln | grep 3301

- **Once you have the setup ready, you can run the kernel to connect port 3301 for mining, namely: tcp://127.0.0.1:3301:**

        damominer -P stratum1+tcp://CP_damo01.workname01@127.0.0.1:3301 -A eth

- **Run the linux_stop.sh script to stop the service:**

        bash linux_stop.sh


### Windows

- **Unzip miner-agent-win64-\*\*\*.tar.gz to get the following file:**

        tar -zxvf miner-agent-win64-***.tar.gz

- **Change the win_start.bat script miner proxy address and the current file address: eth.impool.io:6333**


- **Run the win_start.bat script with administrator privileges to start the service.**


- **Once you have the setup ready, you can run the kernel to connect port 3301 for mining, namely: tcp://127.0.0.1:330**

        damominer -P stratum1+tcp://CP_damo01.workname01@127.0.0.1:3301 -A eth

- **Run the win_stop.bat script with administrator privileges to stop the service。**



## API Reference

    # Get proxy information
    curl http://localhost:8001/api/proxy
    {
    	"code": 200,
    	"result": {
    		"login_name": "CP_damo01",
    		"worker_name": "workname01",
    		"sub_mit_num": 1,
    		"url_list": [
    			"eth.impool.io:6333"
    		],
    		"version": "7d37ea1"
    	},
    	"msg": ""
    }

    # Get mining machine information
    curl http://localhost:8001/api/proxy
    {
    	"code": 200,
    	"result": [
    		{
    			"name": "workname01",
    			"ip": "127.0.0.1",
    			"login": "CP_damo01",
    			"submit_num": 1,
    			"hash": 0,
    			"conn_time": 1645671624
    		}
    	],
    	"msg": ""
    }


## History

### V1.0.0 (20220224)

    Supports Windows & linux.

