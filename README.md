# Learning to Orient Surfaces by Self-supervised Spherical CNNs
Repository containing the code of "Learning to Orient Surfaces by Self-supervised Spherical CNNs", accepted to [NeurIPS 2020](https://neurips.cc/). WIP.

[[Paper]]() - [[Video]]() - [[Poster]]()

### Authors
Riccardo Spezialetti - Federico Stella - Marlon Marcon - Luciano Silva - [Samuele Salti](https://vision.deis.unibo.it/ssalti/) - [Luigi Di Stefano](https://www.unibo.it/sitoweb/luigi.distefano/)

<p align="center">
  <img width="600" height="400" src="assets/teaser.png">
</p>

## Installation
Before start, make sure that all dependencies are installed. The simplest way to do so, is to use [anaconda](https://www.anaconda.com/).
You can create an anaconda environment called `compass` using
```
conda env create -f requirements.yml
conda activate compass
```

### Instal external dependencies
Install lie-learn:
```bash
git clone https://github.com/AMLab-Amsterdam/lie_learn
cd lie_learn
python setup.py install
```
Install spherical-cnns:
```bash
git clone https://github.com/jonas-koehler/s2cnn.git
cd s2cnn
python setup.py install
```

### Instal and Test Spherical Voxelization
```bash
# Install pybind
sudo apt-get install python-pybind11
```

```bash
cd  utils/spherical_voxel/
python3 setup.py develop
# The test will fail
python3 -m unittest utils/test_geometry.py 
```

## How To

### Training
To train a new network from scratch on 3DMatch, run:
```
python apps/train_compass.py --config_file configs/train_3dm.yaml --name_train <name> --path_log <path to log dir> --path_ds <path to dataset> --name_file_folder_train <CSV file with training split> --name_file_folder_validation <CSV file with val split>
```
In `configs` there are also pre-configured settings for StanfordViews and ETH.
To produce the test-time adaptation you need to load a base model (e.g. trained with 3DMatch) and train it with the config file corresponding to the dataset you want to adapt to, specifying the additional command line arguments to load the base model:
```
--path_ckp_ts <path to ts file of base model> --path_ckp_s2_layer <path to s2 layer> --path_ckp_lrf_layer <path to lrf layer>
```

## Test
To test the network, 
```
python 
```

## Pretrained Models
Pretrained models are available for download:
| Training |  zip |
|:-:|:--:|
| 3DMatch | [weights](https://github.com/CVLAB-Unibo/compass/tree/master/pretrained_models/basemodel) |
| 3DMatch, adapted with ETH | [weights](https://github.com/CVLAB-Unibo/compass/tree/master/pretrained_models/adaptation_eth) |
| 3DMatch, adapted with StanfordViews | [weights](https://github.com/CVLAB-Unibo/compass/tree/master/pretrained_models/adaptation_stanfordviews) |
| ModelNet40 | [weights]() |

## Citation
If you find this code useful in your research, please cite:
```
@inproceedings{xxxx,
  title={yyyyyyy},
  author={zzzz},
  booktitle={zzzz},
  year={2020}
}
```

## License
Code is licensed under Apache 2.0 License. More information in the `LICENSE` file.

## Acknowledgements
Parts of our code are from other repositories:
