# 👁️ Florence-2: Architecture & Robustness Analysis

📖 **[View the Florence-2 Evaluation Notebook Here](./Florence2_Robustness_Analysis.ipynb)**

## 🎯 Project Overview

This project evaluates the zero-shot object detection performance and robustness of Microsoft's Florence-2-base vision-language model.

The analysis focuses on:
- Quantitative object detection performance on the COCO validation dataset
- Recall@0.5 and Mean IoU evaluation
- Robustness under progressive image brightness degradation
- Qualitative analysis of difficult and dense-scene failure cases

## 🤖 Model

- **Model:** Microsoft Florence-2-base
- **Task:** Zero-Shot Object Detection
- **Prompt:** `<OD>`
- **Dataset:** COCO validation split
- **Baseline evaluation:** 1,000 images
- **Robustness stress test:** 100 images

## 🔬 Experimental Setup

### 1. Quantitative Baseline
The model is evaluated on 1,000 images from the COCO validation split.

The evaluation measures:
- **Recall@0.5**
- **Mean IoU**
- Image-level detection statistics

A prediction is considered a successful detection when:
1. The predicted class matches the ground-truth class.
2. The predicted bounding box has IoU ≥ 0.5 with the ground-truth box.

### 2. Brightness Robustness Stress Test
To evaluate robustness under distribution shift, the input images are progressively darkened using the following brightness levels:
- 100% (original image)
- 80%
- 60%
- 40%
- 20%
- 10%

Detection Recall@0.5 is measured at each brightness level.

### 3. Qualitative Failure Analysis
Difficult examples are extracted from scenes containing at least four ground-truth objects where Florence-2 achieves zero Recall@0.5.

The selected images are visualized together with:
- Ground-truth bounding boxes
- Florence-2 predicted bounding boxes

## 📊 Results

During execution, the experiments generate the following quantitative result files:
- `florence2_coco_quantitative_baseline.csv`
- `florence2_stress_test_results.csv`

The notebook also generates visualization plots for:
- Recall@0.5 distribution
- Detection performance by scene density
- Recall degradation under reduced brightness
- Dense-scene failure cases

## 🛠️ Environment

The project was developed and tested using:
- Python 3.12
- CUDA-enabled GPU
- PyTorch
- Transformers 4.41.2
- Tokenizers 0.19.1

All required Python packages are listed in `requirements.txt`.

## 🚀 Installation & Setup

Clone the repository:
```bash
git clone [https://github.com/YarinGaida/Florence-2-Robustness-Analysis.git](https://github.com/YarinGaida/Florence-2-Robustness-Analysis.git)
cd Florence-2-Robustness-Analysis
```

Create and activate a virtual environment:
```bash
# Linux / macOS
python -m venv .venv
source .venv/bin/activate

# Windows
.venv\Scripts\activate
```

Install the required packages:
```bash
pip install -r requirements.txt
```

## ▶️ Running the Experiments

The complete implementation is contained in: [`Florence2_Robustness_Analysis.ipynb`](./Florence2_Robustness_Analysis.ipynb)

The notebook is organized into the following sequential stages:
1. Environment setup and model loading
2. Evaluation metric implementation
3. COCO quantitative baseline
4. Baseline result visualization
5. Brightness robustness stress test
6. Robustness visualization
7. Qualitative failure-case analysis

## Google Colab
1. Open Florence2_Robustness_Analysis.ipynb in Google Colab.
2. Select a GPU runtime.
3. Run the notebook cells sequentially from top to bottom.
4. The required Python dependencies are installed in the first code cell.
5. The notebook downloads the Florence-2 model and COCO validation data automatically.

## Local Environment
The notebook is intended to be executed using Jupyter Notebook or VS Code with a CUDA-enabled GPU and the dependencies strictly matched to those listed in requirements.txt.

## 📁 Project Structure

```text
Florence-2-Robustness-Analysis/
│
├── Florence2_Robustness_Analysis.ipynb
├── README.md
├── requirements.txt
├── .gitignore
│
└── results/
    └── figures/
        ├── baseline_recall_distribution_and_scene_density_recall.png
        ├── brightness_stress_test.png
        └── dense_scene_failure_cases.png
```

## 📚 References

* **Florence-2 Paper:** [Florence-2: Advancing a Unified Representation for a Variety of Vision Tasks (2023)](https://arxiv.org/abs/2311.06242)
* **Florence-2 Model Weights:** [microsoft/Florence-2-base (Hugging Face)](https://huggingface.co/microsoft/Florence-2-base)
* **COCO Dataset:** [detection-datasets/coco (Hugging Face)](https://huggingface.co/datasets/detection-datasets/coco)
