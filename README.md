# graph-rcnn.pytorch
Pytorch code for our ECCV 2018 paper ["Graph R-CNN for Scene Graph Generation"](https://arxiv.org/pdf/1808.00191.pdf)

<div style="color:#0000FF" align="center">
<img src="figures/teaser_fig.png" width="850"/>
</div>

<!-- :balloon: 2019-06-04: Okaaay, time to reimplement Graph R-CNN on pytorch 1.0 and release a new benchmark for scene graph generation. It will also integrate other models like IMP, MSDN and Neural Motif Network. Stay tuned!

:balloon: 2019-06-16: Plan is a bit delayed by ICCV rebuttal, but still on track. Stay tuned! -->

## Introduction

This project is a set of reimplemented representative scene graph generation models based on Pytorch 1.0, including:
* [Graph R-CNN for Scene Graph Generation](https://arxiv.org/pdf/1808.00191.pdf), our own. ECCV 2018.
* [Scene Graph Generation by Iterative Message Passing](https://arxiv.org/pdf/1701.02426.pdf), Xu et al. CVPR 2017
* [Scene Graph Generation from Objects, Phrases and Region Captions](https://arxiv.org/pdf/1707.09700.pdf), Li et al. ICCV 2017
* [Neural Motifs: Scene Graph Parsing with Global Context](https://arxiv.org/pdf/1711.06640.pdf), Zellers et al. CVPR 2018

Our reimplementations are based on the following repositories:

* [maskrcnn-benchmark](https://github.com/facebookresearch/maskrcnn-benchmark)
* [faster-rcnn](https://github.com/jwyang/faster-rcnn.pytorch)
* [scene-graph-TF-release](https://github.com/danfeiX/scene-graph-TF-release)
* [MSDN](https://github.com/yikang-li/MSDN)
* [neural-motifs](https://github.com/rowanz/neural-motifs)

## Why we need this repository?

The goal of gathering all these representative methods into a single repo is to establish a more fair comparison across different methods under the same settings. **As you may notice in recent literatures, the reported numbers for IMP, MSDN, Graph R-CNN and Neural Motifs are usually confusing, especially due to the big gap between IMP style methods (first three) and Neural Motifs-style methods (neural motifs paper and other variants built on it)**. We hope this repo can establish a good benchmark for various scene graph generation methods, and contribute to the research community!

## Checklist

- [x] Faster R-CNN Baseline (:balloon: 2019-07-04)
- [x] Scene Graph Generation Baseline (:balloon: 2019-07-06)
- [x] Iterative Message Passing (IMP) (:balloon: 2019-07-07)
- [ ] Multi-level Scene Description Network (MSDN)
- [x] Neural Motif (Frequency Prior Baseline) (:balloon: 2019-07-08)
- [ ] Neural Motif
- [ ] Graph R-CNN

## Benchmarking

### Object Detection

backbone | model | bs | lr  | lr_decay_step | max_iter | mAP@0.5 | mAP@0.50:0.95
--------|--------|--------|--------|---------|--------|--------|--------
Resnet-101 | faster r-cnn | 6 | 5e-3 | (70k, 90k) | 100k | 24.8 | 12.8

### Scene Graph Generation
backbone | model | bs | lr | lr_decay_step | max_iter | sgdet@20 | sgdet@50 | sgdet@100
--------|--------|--------|---------|--------|--------|--------|---------|---------
Resnet-101 | vanilla | 6 | 5e-3 | (70k, 90k) | 100k | 10.4 | 14.3 | 16.8
Resnet-101 | frequency | 6 | 5e-3 | (70k, 90k) | 100k | 19.4 | 25.0 | 28.5
<!-- Resnet-101 | freq-overlap | 6 | 5e-3 | (70k, 90k) | 100k | - | - | - -->
