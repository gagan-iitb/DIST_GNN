# DIST_GNN - Tutorial on Distributed Graph Neural Networks
<!--img src="https://github.com/user-attachments/assets/c8a0e3bf-626f-4e61-908a-b9fd16b7900f" alt="distgnn" width="500"/-->
<!-- img src="https://github.com/user-attachments/assets/f985dc3a-1ef3-4211-9d75-b80fcd0075c7" alt="distgnn1" width="500"/-->


https://github.com/user-attachments/assets/cbdff8e3-42e2-4958-bcec-b97ac6289934




## Code Repo
The code used in the tutorial is available on [Github](https://github.com/Anirban600/EAT-DistGNN)

## Setup
The setup assumes you have docker installed on your system. If docker is not installed then install docker using the following links: 

[Linux](https://docs.docker.com/engine/install/) | [Windows](https://docs.docker.com/desktop/setup/install/windows-install/) | [Mac](https://docs.docker.com/desktop/setup/install/mac-install/).

**Please watch this [video](https://drive.google.com/file/d/1Fd8MbXWvKfukSE-p5EZ9dOzxRPLa-VnA/view?usp=drive_link) on environment setup. 
Doing this setup beforehand is recommended so you can follow along in the hands-on during the tutorial.**
The code has all the required files for setup.

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
Here is a visualization of how different classes are distributed among different partitions for the flickr dataset:

![image](https://github.com/user-attachments/assets/ebefb871-7526-4d0f-8b9b-339eafbab7be)


## Training
Here is a quick [video](https://drive.google.com/file/d/1EBU9Lnn6CkRWdiTiMeK6NwbjOrSPyINn/view?usp=sharing) on distributed training using our code.
Run this command if you are following the hands-on
``` [bash]
./deploy_trainers.sh -G flickr -P metis -n 7 -p 1.0 -d 0.5 -s 15 -v default -e 10 -c 1
```

Here a some results after the training finishes:

![image](https://github.com/user-attachments/assets/d506e0be-1f42-4c48-8276-2b55fb101dab)
