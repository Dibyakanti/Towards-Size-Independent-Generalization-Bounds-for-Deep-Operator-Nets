# Towards Size-Independent Generalization Bounds for Deep Operator Nets

This repository contains the official code for the paper : [Towards Size-Independent Generalization Bounds for Deep Operator Nets (TMLR, 2024)](https://openreview.net/forum?id=21kO0u6LN0&noteId=R8EOCZXPfz).

```
@article{
gopalani2024towards,
title={Towards Size-Independent Generalization Bounds for Deep Operator Nets},
author={Pulkit Gopalani and Sayar Karmakar and Dibyakanti Kumar and Anirbit Mukherjee},
journal={Transactions on Machine Learning Research},
issn={2835-8856},
year={2024},
url={https://openreview.net/forum?id=21kO0u6LN0}
}
```

## 0. Prerequisites

### 0.1. Local 
To install the required libraries run `pip install -r requirements.txt` and then follow the instructions in Training and Analysis section below.

### 0.2. Docker

We have used the Nvidia docker image for JAX  `nvcr.io/nvidia/jax:24.04-py3`. If you have don't have docker installed you can check the following [link](https://www.docker.com/get-started/) to get that set up.

If docker is already set up then you can follow these steps to set up your environment.

1. Pull the docker image : `docker pull nvcr.io/nvidia/jax:24.04-py3`
2. Docker build :
   - To run a docker container with `bash` shell, use *line 9* instead of *line 10* in the Dockerfile and execute : `docker build -t jax_don`
   - To run a persistent docker container that runs just the main.py file and train the models, then use *line 10* in the Dockerfile and execute : `docker build -t jax_don_persist`
3. Docker run : 
    - To run bash : `docker run --gpus all -it --rm -v $(pwd):/workspace jax_don`
    - To run persistent container : `docker run --gpus all -d --rm -v $(pwd):/workspace persist_jax_don`

Note : Please refer to docker documentation linked above for more information about what each of these commands.

## 1. Setting the Config Files

The `config/<pde-name>Config.yaml` file can be used for setting the branch_layers, trunk_layers, loss_type, huber_delta, x0, y0 T_lim, kappa, N_train,P_train, num_fourier_terms, N_test and P_test.

## 2. Training

The `scripts\train\<pde-name>Train.py` contains the scripts for training the models

Note : The bias in the DeepONet needs to be disabled before calculating the Rademacher bound

## 3. Analysis

The `scripts\analysis\<pde-name>Analysis.py` contains the scripts for analyzing the models
