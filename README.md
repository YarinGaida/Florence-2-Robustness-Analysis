# Florence-2 Architecture & Robustness Analysis

## Overview

This project evaluates the zero-shot object detection performance and robustness of Microsoft's Florence-2 vision-language model.

The analysis focuses on:

- Quantitative object detection performance on the COCO validation dataset
- Recall@0.5 and Mean IoU evaluation
- Robustness under progressive image brightness degradation
- Qualitative analysis of difficult and dense-scene failure cases

## Model

- Model: Microsoft Florence-2-base
- Task: Zero-shot Object Detection
- Prompt: `<OD>`
- Dataset: COCO validation split
- Evaluation subset: 1,000 images
- Robustness stress test: 100 images

## Experiments

### 1. Quantitative Baseline

The model is evaluated on 1,000 COCO validation images.

Metrics:

- Recall@0.5
- Mean IoU
- Image-level detection statistics

### 2. Brightness Robustness Stress Test

The input images are progressively darkened using the following brightness levels:

- 100%
- 80%
- 60%
- 40%
- 20%
- 10%

The effect of brightness degradation on object detection recall is measured.

### 3. Qualitative Failure Analysis

Difficult cases are extracted from scenes containing multiple objects where Florence-2 achieves zero recall.

## Environment

Recommended:

- Python 3.12
- CUDA-enabled GPU
- PyTorch
- Transformers 4.41.2
- Tokenizers 0.19.1

Install dependencies:

```bash
pip install -r requirements.txt