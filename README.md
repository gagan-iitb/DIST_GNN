# DIST_GNN - Tutorial on Distributed Graph Neural Networks
<!--img src="https://github.com/user-attachments/assets/c8a0e3bf-626f-4e61-908a-b9fd16b7900f" alt="distgnn" width="500"/-->
<!-- img src="https://github.com/user-attachments/assets/f985dc3a-1ef3-4211-9d75-b80fcd0075c7" alt="distgnn1" width="500"/-->
<iframe src="https://drive.google.com/file/d/16kLSTE0Il_Y3DYY9wtbomcqCykCqZnA3/preview" width="640" height="480" allow="autoplay"/>


## Code Repo
The code used in the tutorial is available on [Github](https://github.com/Anirban600/EAT-DistGNN)

## Setup
Please watch this [video](https://drive.google.com/file/d/1Fd8MbXWvKfukSE-p5EZ9dOzxRPLa-VnA/view?usp=drive_link) on environment setup. 
Doing this setup beforehand is recommended so you can follow along in the hands-on during the tutorial.
The code has all the required files for setup.

## Partitioning
Run this command if you are following the hands-on
``` [bash]
python3.9 partition_code/partition_default.py \
                      --dataset flickr \
                      --num_parts 4 \
                      --balance_train \
                      --balance_edges \
                      --output partitions/flickr/metis
```
Add some visualization for partitioning

## Training
Run this command if you are following the hands-on
``` [bash]
./deploy_trainers.sh -G flickr -P metis -n 7 -p 1.0 -d 0.5 -s 15 -v default -e 10 -c 1
```

Here a some results after the training finishes

![image](https://github.com/user-attachments/assets/d506e0be-1f42-4c48-8276-2b55fb101dab)
