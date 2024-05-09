# Biology project: AlphaFLOW

Project for the Course "Physical Methods of Biology"

## Installation

- Create a virtual environment: `conda create -n [name] python=3.9`
- Activate it: `conda activate [name]`
- Install CUDA: `conda install nvidia/label/cuda-11.6.2::cuda`
- Since you are using a conda environment, you might need to have these env variables set, so that it correctly points to the environment's CUDA directories:  
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

## Usage

Follow [_Running inference_ instructions](https://github.com/bjing2016/alphaflow?tab=readme-ov-file#running-inference) on AlphaFLOW repository.
