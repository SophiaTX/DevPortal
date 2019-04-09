---
title: Node Deploy script
position: 1
---


# Automatic node deploy

[Deploy Script](https://github.com/SophiaTX/SophiaTX/tree/develop/ciscripts/deploy) connects to the server and automatically deploys node binaries and stores previous version


Created file structure on server:
 
     ~                                          # home of specified user
     ├── ...                        
     ├── sophiatx_binaries                      # Binaries folder
     │   ├── sophiatx_#<NUM>.tar.gz             # SophiaTX archived binaries
     │   ├── sophiatx_#<NUM>.tar.gz.old         # Previous version of SophiaTX archived binaries
     │   ├── sophiatxd                          # SophiaTX demon
     │   └── sophia_app_data                    # Master data folder
     │       ├── configs                        # Configs data folder
     │       │   ├── testnet_config.ini         # SophiaTX demon config file
     │       │   ├── testnet_config.ini.old     # Previous version of SophiaTX demon config file
     │       │   └── ...
     │       └── ...
     └── ... 
    

## Usage

./deploy-node.sh -h host -u user [-s sourceUrl] [-r]

#### Arguments description:

-h host         : host(server), where node binaries should be deployed into
  
-u user         : user to be used to connect to the host. This user has to have id_rsa.pub imported on host
  
[-s sourceUrl]  : sourceUrl from which are the the binaries downloaded. optional. In case it is not specified, latest binaries(devnet) are downloaded.
  
[-r]            : replay-blockain flag. It is used when starting sophiatxd. optional 


## Requirements

For using automatic deploy script, you have to install Ansible on your machine:

$ sudo apt-get update   
$ sudo apt-get install software-properties-common   
$ sudo apt-add-repository ppa:ansible/ansible   
$ sudo apt-get update   
$ sudo apt-get install ansible**