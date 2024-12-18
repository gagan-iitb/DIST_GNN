# DIST_GNN - Tutorial on Distributed Graph Neural Networks
<!--img src="https://github.com/user-attachments/assets/c8a0e3bf-626f-4e61-908a-b9fd16b7900f" alt="distgnn" width="500"/-->
<!-- img src="https://github.com/user-attachments/assets/f985dc3a-1ef3-4211-9d75-b80fcd0075c7" alt="distgnn1" width="500"/-->


https://github.com/user-attachments/assets/cbdff8e3-42e2-4958-bcec-b97ac6289934




## Code Repo
The code used in the tutorial is available on [Github](https://github.com/Anirban600/EAT-DistGNN)

## Setup
The setup assumes you have docker installed on your system. If docker is not installed, then install docker using the following links: 

[Linux](https://docs.docker.com/engine/install/) | [Windows](https://docs.docker.com/desktop/setup/install/windows-install/) | [Mac](https://docs.docker.com/desktop/setup/install/mac-install/).

**Please watch this [video](https://drive.google.com/file/d/1Fd8MbXWvKfukSE-p5EZ9dOzxRPLa-VnA/view?usp=drive_link) on environment setup. 
You should do this setup beforehand so you can follow along in the hands-on during the tutorial.**
The code has all the required files for setup.
## Follow these commands and run these commands on the command line one by one 
```
git clone https://github.com/Anirban600/EAT-DistGNN.git
```
Update the path of the folder in the docker-compose.yml file(Remember the path should be the absolute path of EAT-DistGNN)
```
cd EAT-DistGNN
sudo docker-compose build
sudo docker-compose up -d
sudo docker ps
sudo docker exec -it container1 bash
```
Run this command to add the public key on container1 
```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa -N ""
cat /root/.ssh/id_rsa.pub
```
Paste this generated public key in ssh_key_setup.sh file
Now follow these commands for ssh all the containers. Please change the container number(1,2,3,4)
```
sudo docker exec -it container1 bash
cd ~/EAT-DistGNN
chmod +x ssh_key_setup.sh
./ssh_key_setup.sh
exit
```
Now go to container 1 and SSH into all the other containers. Please change the SSH IPs one by one till 192.168.1.5
```
sudo docker exec -it container1 bash
ssh 192.168.1.3
exit
```
Now container1 can ssh all the four containers and run the training command  

Change to the EAT_DistGNN folder before running the below commands.
```
cd ~/EAT-DistGNN
```

## Partitioning
Here is a quick [video](https://drive.google.com/file/d/1h5YLllBwgyFLWIfj7rM10rNWFsexO8uU/view?usp=sharing) on partitioning using our code.
Run this command if you are following the hands-on
``` [bash]
python3.9 partition_code/partition_default.py \
                      --dataset flickr \
                      --num_parts 4 \
                      --balance_train \
                      --balance_edges \
                      --output partitions/flickr/metis
```
Here is a visualization of how different classes are distributed among different partitions for the Flickr dataset:

![image](https://github.com/user-attachments/assets/ebefb871-7526-4d0f-8b9b-339eafbab7be)


## Training
Here is a quick [video](https://drive.google.com/file/d/1EBU9Lnn6CkRWdiTiMeK6NwbjOrSPyINn/view?usp=sharing) on distributed training using our code.
Run this command if you are following the hands-on
``` [bash]
./deploy_trainers.sh -G flickr -P metis -n 7 -p 1.0 -d 0.5 -s 15 -v default -e 10 -c 1
```

Here are some results after the training finishes:

![image](https://github.com/user-attachments/assets/d506e0be-1f42-4c48-8276-2b55fb101dab)
