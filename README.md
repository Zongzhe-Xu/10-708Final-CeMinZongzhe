## Environment

We run our experiments with Python 3.8, PyTorch 1.12.0 with CUDA 11.6. Please install corresponding PyTorch and CUDA versions according to your computational resources. Then install the rest of required packages by running `pip install -r requirements.txt`. 

We also need ``apex``, which enables mixed precision to speed up training. Please follow https://github.com/NVIDIA/apex to install.

## Dataset

We use the [Visual Genome](https://homes.cs.washington.edu/~ranjay/visualgenome/index.html) dataset in this work, which consists of 108,077 images, each annotated with objects and relations. Following [previous work](https://arxiv.org/pdf/1701.02426.pdf), we filter the dataset to use the most frequent 150 object classes and 50 predicate classes for experiments.

You can download the images here, then extract the two zip files and put all the images in a single folder:

Part I: https://cs.stanford.edu/people/rak248/VG_100K_2/images.zip

Part II: https://cs.stanford.edu/people/rak248/VG_100K_2/images2.zip

Then download VG metadata preprocessed by [IMP](https://arxiv.org/abs/1701.02426): [annotations](http://svl.stanford.edu/projects/scene-graph/dataset/VG-SGG.h5), [class info](http://svl.stanford.edu/projects/scene-graph/dataset/VG-SGG-dicts.json),and [image metadata](http://svl.stanford.edu/projects/scene-graph/VG/image_data.json) and copy those three files in a single folder.

Finally, update `config.py` to with a path to the aforementioned data, as well as the absolute path to this directory.

To reproduce the results, please also download the pre-trained GB-Net checkpoint ``vgrel-11`` from https://github.com/alirezazareian/gbnet and place in `checkpoints/vgdet/vgrel-11`.

## Usage

You can simply run the codes in ``ipynb/`` to conduct the experiments. For PredCls, we train from the GB-Net checkpoint, and for SGCls task, we start from the best PredCls checkpoint.

## Acknowledgements

Our codebase is adapted from [GB-Net](https://github.com/alirezazareian/gbnet) and [EB-Net](https://github.com/zhanwenchen/eoa). We thank the authors for releasing their code!