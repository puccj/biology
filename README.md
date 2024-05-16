# Biology project: AlphaFLOW

Project for the Course "Physical Methods of Biology": Using [AlphaFLOW](https://github.com/bjing2016/alphaflow) to simulate some protein structures

## Prerequisites

- Conda (Miniconda is fine too)
- Python >= 3.9
- CUDA-capable hardware
- CUDA >= 11.6

## Installation

- Create a virtual environment: `conda create -n [name] python=3.9 cuda-version=11.6`
- Activate it: `conda activate [name]`
- [Optional] If during inference you get an error stating that a certain function is not implemented on CPU, it's probably due to the fact that openfold has been installed on CPU. Since you are using a conda environment, you might need to have these env variables set, so that it correctly points to the environment's CUDA directories:  
  Note that you need to have these **before** installing openfold, as briefly explained [in this issue](https://github.com/aqlaboratory/openfold/issues/293#issuecomment-2058255494).
  ```
  export CUDA_HOME=$CONDA_PREFIX
  export CUDA_PATH=$CONDA_PREFIX
  export LIBRARY_PATH=$CONDA_PREFIX/lib:$LIBRARY_PATH
  export LD_LIBRARY_PATH=$CONDA_PREFIX/lib:$LD_LIBRARY_PATH
  ```

- Install AlphaFLOW as instructed in [its repository](https://github.com/bjing2016/alphaflow?tab=readme-ov-file#installation):
  ```
  pip install numpy==1.21.2 pandas==1.5.3
  pip install torch==1.12.1+cu113 -f https://download.pytorch.org/whl/torch_stable.html
  pip install biopython==1.79 dm-tree==0.1.6 modelcif==0.7 ml-collections==0.1.0 scipy==1.7.1 absl-py einops
  pip install pytorch_lightning==2.0.4 fair-esm mdtraj wandb
  pip install 'openfold @ git+https://github.com/aqlaboratory/openfold.git@103d037'
  ```
- Clone [AlphaFLOW repository](https://github.com/bjing2016/alphaflow) in order to have the required python code: `git clone https://github.com/bjing2016/alphaflow`

## Usage

- Download the desired model weights (see links below). For instance, to get AlphaFLOW-PDB_distilled via wget you can run:
  ```
  wget https://alphaflow.s3.amazonaws.com/params/alphaflow_pdb_distilled_202402.pt
  ```
- Follow [_Running inference_ instructions](https://github.com/bjing2016/alphaflow?tab=readme-ov-file#running-inference) on AlphaFLOW repository.

### AlphaFlow models
| Model|Version|Weights|
|:---|:--|:--|
| AlphaFlow-PDB | base | https://alphaflow.s3.amazonaws.com/params/alphaflow_pdb_base_202402.pt |
| AlphaFlow-PDB | distilled | https://alphaflow.s3.amazonaws.com/params/alphaflow_pdb_distilled_202402.pt |
| AlphaFlow-MD | base | https://alphaflow.s3.amazonaws.com/params/alphaflow_md_base_202402.pt |
| AlphaFlow-MD | distilled | https://alphaflow.s3.amazonaws.com/params/alphaflow_md_distilled_202402.pt |
| AlphaFlow-MD+Templates | base | https://alphaflow.s3.amazonaws.com/params/alphaflow_md_templates_base_202402.pt |
| AlphaFlow-MD+Templates | distilled | https://alphaflow.s3.amazonaws.com/params/alphaflow_md_templates_distilled_202402.pt |

### ESMFlow models
| Model|Version|Weights|
|:---|:--|:--|
| ESMFlow-PDB | base | https://alphaflow.s3.amazonaws.com/params/esmflow_pdb_base_202402.pt |
| ESMFlow-PDB | distilled | https://alphaflow.s3.amazonaws.com/params/esmflow_pdb_distilled_202402.pt |
| ESMFlow-MD | base | https://alphaflow.s3.amazonaws.com/params/esmflow_md_base_202402.pt |
| ESMFlow-MD | distilled | https://alphaflow.s3.amazonaws.com/params/esmflow_md_distilled_202402.pt |
| ESMFlow-MD+Templates | base | https://alphaflow.s3.amazonaws.com/params/esmflow_md_templates_base_202402.pt |
| ESMFlow-MD+Templates | distilled | https://alphaflow.s3.amazonaws.com/params/esmflow_md_templates_distilled_202402.pt |
