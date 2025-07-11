# FastGL: A GPU-Efficient Framework for Accelerating Sampling-Based GNN Training at Large Scale


Dear readers, we have provided the source code to reproduce the results of our paper. The framework of FastGL is developed upon Pytorch. To implement the **Memory-Aware** and **Fused-Map**
techniques, we build the dedicated CUDA operators in the folder of `cuda_operators/`. Then we 
construct the Fused-Map sampler in `FusedMapSampler.py`. We implement our **Match-Reorder** 
strategy in `MatchReorderServer.py`. `run_fig*/` provides the training scripts of our experiments.

We first list the dependencies of our code and then provide the commands to install this project and run the experiments mentioned in the Evaluation section of our paper. 

## Dependency

### Hardware Dependency

All our evaluations are performed on a GPU server that consists of two AMD EPYC 7532 CPUs (total $2\times 32$ cores), 512GB DRAM, and eight NVIDIA GeForce RTX 3090 (with 24GB memory) GPUs.
Also, you can run our FastGL on at least one GPU with 128GB DRAM of host memory.

### Software Dependency

`Ubuntu: 20.04`\
`CUDA: 11.0`\
`Python: 3.7.13`\
`Pytorch: 1.10.1`\
`Torch Geometric: 2.1.0`\
`DGL: 1.0.0`\
`OGB: 1.3.4`\
`Numpy: 1.21.5`\
`Scikit Learn : 0.24.2`\
`Matplotlib: 3.3.4`

The different versions of the software might have incompatible problems; please take care it when you install software.

## Installation

When the above dependencies are ready, we can install FastGL Pytorch Binding as follows:
* Run `python cuda_operators/setup.py install` to install the FastGL modules.

##  Evaluation and expected results

When running the experiments, please stop other programs on the GPU server.

In this section, we focus on introducing the methodology to reproduce the results of our framework FastGL in 
this paper. Given that the results of baselines (PyG, DGL, GNNAdvisor, and GNNLab) are 
obtained from their open-source 
implementations, for simplicity, 
we only provide the code and script to run experiments on DGL, and the experimental results on 
other frameworks can be obtained with minor changes to the scripts we provide. 

### Running main experiments on FastGL and DGL in Figure 9.
  * Run `run_fig9_fastgl.sh`.
  * Run `run_fig9_dgl.sh`.
### Running the scalability experiments on FastGL in Figure 15.

  * Run `run_fig15a_fastgl.sh`.
  * Run `run_fig15b_fastgl.sh`.
  * Run `run_fig15c_fastgl.sh`.
  * Run `run_fig15d_fastgl.sh`.

**Note: If a Permission Denied error raises, you can perform `chmod +x` on the 
specific `.sh` file to run successfully.**

The experimental results will be saved to the corresponding log files.
The log file is named in the format of 
'model-dataset-model\_layer-hidden\_dim-batch\_size-device\_num` to 
distinguish between different training setups.

More information is detailed in **AE appendix** of our publised paper "FastGL: A GPU-Efficient Framework for Accelerating Sampling-Based GNN Training at Large Scale" at ASPLOS'2024.


**Dataset Download**
```
https://drive.google.com/file/d/1Dhc1hEXcT6vgw23JtzuML28fx0wk-DCY/view
```
