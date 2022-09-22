# Volumetric memory network for interactive medical image segmentation

We propose a novel memory-augmented network named VMN for interactive segmentation of volumetric medical data.

## Paper

This repository provides the official PyTorch implementation of VMN in the following papers:

**Volumetric memory network for interactive medical image segmentation** <br/>
[Tianfei Zhou](https://www.zongweiz.com), Liulei Li, Gustav Bredell, Jianwu Li, and [Ender Konukoglu](https://people.ee.ethz.ch/~kender/) <br/>
Biomedical Image Computing, CVL, ETH Zurich | Beijing Institute of Technology <br/>
Medical Image Analysis (MedIA) [[Paper](https://www.sciencedirect.com/science/article/pii/S1361841522002316)] <br/>
**_[Elsevier-MedIA Best Paper Award](http://www.miccai.org/about-miccai/awards/medical-image-analysis-best-paper-award/)_** 


**Quality-Aware Memory Network for Interactive Volumetric Image Segmentation** <br/>
[Tianfei Zhou](https://www.zongweiz.com), Liulei Li, Gustav Bredell, Jianwu Li, and [Ender Konukoglu](https://people.ee.ethz.ch/~kender/) <br/>
Biomedical Image Computing, CVL, ETH Zurich | Beijing Institute of Technology <br/>
International Conference on Medical Image Computing and Computer Assisted Intervention (MICCAI) [[Paper](https://link.springer.com/chapter/10.1007/978-3-030-87196-3_52)]

## Preparation

### Dataset Download
Download [MSD](http://medicaldecathlon.com/) and [KiTS](https://kits19.grand-challenge.org/data/). This repo provides dataloaders for MSD, you can some modification to adapt them to other datasets.

### Dataset Organization
To run the training and testing code, we require the following data organization format

    ${ROOT}--
            |--KiTS
            |--MSD
            │   ├── ImageSets06
            │   │   └── train.txt
            │   │   └── test.txt
            │   ├── ImageSest10
            │   ├── Task06_mask
            │   │   ├── lung_001
            │   │   │   ├── 0.png 
            │   │   │   ├── ...
            │   │   │   └── 199.png
            │   │   ├── lung_002
            │   │   ├── ...
            │   │   └── lung_060
            │   ├── Task06_origin
            │   │   ├── lung_001
            │   │   │   ├── 0.png 
            │   │   │   ├── ...
            │   │   │   └── 199.png
            │   │   ├── ...
            │   │   └── lung_060
            │   ├── ImageSets10
            │   ├── Task10_mask
            │   └── Task10_origin
            └──${DATASET3}

### Download Pretrained Weights

- Download the [weight](https://drive.google.com/file/d/1nzhFYOJx3rzvnO8o6g-D1MMA6iQ4VYpw/) pretrained on YouTube-VOS for VMN
- Update the `initial` attribution in `option.py`

## Training and Testing

* 2D Interactive Network

```
    Mem3D/
    └── (train/test)_(dextr/hybrid/inter/scribble/two_point).py
```
    
* Volumetric Memory Network

```
    Mem3D/
    ├── (train/test)_STM.py.  # without Quality Assessment
    └── train_SAQ.py          # with Quality Assessment
```

* Round Based 3D Interactive Segmentation

```
    Mem3D/
    ├── eval_SAQ.py               # w QA
    └── eval_IOG_refine_dextr.py  # w/o QA
```

* Volume-wise Dice Evaluation

```
    Mem3D/
    └── eval.py
```


## Acknowledgements
- This code is based on [DEXTR](https://github.com/scaelles/DEXTR-PyTorch) and [STM](https://github.com/lyxok1/STM-Training).

## Citation
If you use VMN for your research, please cite our papers:

```
@article{zhou2022volumetric,
  title={Volumetric memory network for interactive medical image segmentation},
  author={Zhou, Tianfei and Li, Liulei and Bredell, Gustav and Li, Jianwu and Konukoglu, Ender},
  journal={Medical Image Analysis},
  year={2022},
  publisher={Elsevier}
}

@inproceedings{zhou2021quality,
  title={Quality-aware memory network for interactive volumetric image segmentation},
  author={Zhou, Tianfei and Li, Liulei and Bredell, Gustav and Li, Jianwu and Konukoglu, Ender},
  booktitle={International Conference on Medical Image Computing and Computer-Assisted Intervention},
  pages={560--570},
  year={2021},
  organization={Springer}
}
```
