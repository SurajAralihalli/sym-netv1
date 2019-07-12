# SYMNet
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/2e9024b5c2ff44279f49ea5382244d09)](https://app.codacy.com/app/yrahul3910/symnet?utm_source=github.com&utm_medium=referral&utm_content=yrahul3910/symnet&utm_campaign=Badge_Grade_Dashboard)

SYMNet (Saha-Yedida-Mathur-Nagaraj Net) is a deep learning pipeline with a focus on simplicity and fast training of Deep Neural Nets. Functionality is available through command-line options or as an API. The focus is
on simplicity and getting quick results. For theoretical understanding of the pipeline, please refer to the following papers:
LipschitzLR learning rate policy: arXiv:1902.07399
SBAF and A-ReLU activation functions: arXiv:1906.01975

## API Usage
### Numeric data
The `symnet.py` file shows how to use the API for multi-class classification
on a tabular (CSV) dataset. Start by creating a model:  

    model = NumericModel(csv_path, n_classes=3, label_column='target', task='classification')

Then, you can call `fit` and `predict` on the model, or find the loss and accuracy using
the `score` method. Currently, only classification is supported, but more features will
be added soon.

## CLI Usage
You can use the `symnet.py` file to run classification on a tabular dataset. The available options are:
*  `--task`: As of now, only `'classification'` and `'regression'` are supported.
*  `--dataset`: The CSV dataset.
*  `--data-type`: As of now, only `'numeric'` is supported.
*  `--labels`: The CSV column with labels
*  `--num-classes`: Number of classes (for classification)
*  `--activation`: The activation to use. Any of `('relu', 'elu', 'selu', 'sigmoid', 'softmax', 'linear', 'sbaf', 'arelu', 'softplus)`
*  `--no-header`: Indicates that the CSV does not have a header row
*  `--batch-size`: The batch size to use
*  `--train-split`: The training data subset split size
*  `--epochs`: The number of epochs
*  `--no-balance`: Do not rebalance classes in classification problems

## Docker
The Dockerfile in `symnet-docker` sets up a minimal Debian Stretch system with Python 3.7 and
required packages installed. Run it with  

    docker run -it -v [host-src:]/symnet symnet /bin/bash

This starts up an interactive terminal, mounts a volume at `/symnet` in the container,
and runs a Bash shell. You can change the command run in the
last argument.
   
## Todo
-  [ ]  Add regression support
-  [ ]  Add support for image datasets
-  [ ]  Add support for text datasets
-  [ ]  Add support for image segmentation tasks

## Cite our work
SymNet uses the LipschitzLR learning rate policy: [arXiv:1902.07399](https://arxiv.org/abs/1902.07399)

BibTeX entry:  

    @article{yedida2019novel,
      title={A novel adaptive learning rate scheduler for deep neural networks},
      author={Yedida, Rahul and Saha, Snehanshu},
      journal={arXiv preprint arXiv:1902.07399},
      year={2019}
    }

SymNet also implements the SBAF and A-ReLU activation functions: [arXiv:1906.01975](https://arxiv.org/abs/1906.01975). 
If you use these, please cite:  

    @article{saha2019evolution,
      title={Evolution of Novel Activation Functions in Neural Network Training with Applications to Classification of Exoplanets},
      author={Saha, Snehanshu and Nagaraj, Nithin and Mathur, Archana and Yedida, Rahul},
      journal={arXiv preprint arXiv:1906.01975},
      year={2019}
    }
