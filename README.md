# Overfitting in adversarially robust deep learning

This repository contains the code and training logs for the paper ["Overfitting in adversarially robust deep learning"][arxiv]. 

The experiments for CIFAR10, CIFAR100, and SVHN are in `train_cifar.py`, `train_cifar100.py`, `train_svhn.py` respectively. 
+ CIFAR10 training with semisupervised data is done in `train_cifar_semisupervised_half.py`, and uses the 500K pseudo-labeled TinyImages data from <https://github.com/yaircarmon/semisup-adv>
+ TRADES training is done with the repository located at <https://github.com/yaodongyu/TRADES>, with the only modification being the changes to the learning rate schedule to train to convergence (to decay at epochs 100 and 150 out of 200 total epochs). 

For ImageNet training, we used the repository located at <https://github.com/MadryLab/robustness> with no modifications. The resulting logged data is stored in `.pth` files which can be loaded with `torch.load()` and are simply dictionaries of logged data. The scripts containing the parameters for resuming the ImageNet experiments can be found in `imagenet_scripts/`. 

Logs are all located in the `experiments` folder, and each subfolder corresponds to a set of experiments carried in the paper. 

Model weights for the following models can be found in this [drive folder][model weights]:
+ The best checkpoints for CIFAR10 WideResNets defined in `wideresnet.py` (in for width factor 10 and 20 (from the double descent curve trained against L-infinity)
+ The best checkpoints for SVHN / CIFAR10 (L2) / CIFAR100 / ImageNet models reported in Table 1 (the ImageNet checkpoints are in the format directly used by <https://github.com/MadryLab/robustness>). The remaining models are for the Preactivation ResNet18 defined in `preactresnet.py`. 

[arxiv]: https://arxiv.org/abs/2002.11569
[model weights]: https://drive.google.com/drive/folders/1FtplsMWGBYicAOmWDGSDP83CLwkLLxo9?usp=sharing