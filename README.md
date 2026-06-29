# Deep Learning with MindSpore and PyTorch — A Comparative Study

A hands-on deep learning portfolio that reimplements a set of labs in both **MindSpore**
and **PyTorch**, with the goal of mastering both frameworks and understanding the
underlying theory independently of the tool.

The project starts from an intensive MindSpore-based AI course (Huawei) and rebuilds each
lab in PyTorch, accompanied by comparative notes between the two frameworks.

## Goals

- Rebuild the MindSpore course labs in PyTorch.
- Develop practical fluency in both frameworks.
- Strengthen the theoretical foundations of deep learning (from MNIST to Vision Transformers).
- Document the implementation differences between MindSpore and PyTorch.

## Repository structure

```
.
├── notebooks/
│   ├── 00_fundamentals/   # NumPy, tensors, core concepts
│   ├── 01_frameworks/     # Each framework's introduction and API
│   ├── 02_mnist/          # First complete model (dense + CNN)
│   ├── 03_cnn_images/     # Convolutions and image classification
│   ├── 04_nlp/            # Natural language processing
│   ├── 05_transformer/    # Transformer architecture and attention
│   └── 06_vit/            # Vision Transformer
├── notes/                 # Comparative notes: MindSpore vs PyTorch
├── utils/                 # Reusable helper functions
├── data/                  # Datasets (not versioned; downloaded via code)
├── environment.yml        # Reproducible conda environment
└── requirements.txt       # pip dependencies
```

## Runtime environment (CPU / GPU)

This project reimplements the same labs in MindSpore and PyTorch for comparison. For that
reason, the comparative work runs with **both frameworks on CPU**, ensuring the
comparisons are equivalent and not biased by hardware acceleration.

This decision reflects a real constraint: on Windows, MindSpore only supports CPU (GPU
support is available only on Linux). Keeping PyTorch on CPU as well ensures both
implementations run under the same conditions.

For the most demanding models (Transformer and Vision Transformer), a PyTorch version
running on **GPU (NVIDIA RTX 5060, CUDA)** may also be included, in a separate environment,
to demonstrate hardware acceleration. Those cases are clearly identified in the
corresponding notebooks.

| Environment  | Framework(s)         | Device      | Use                        |
|--------------|----------------------|-------------|----------------------------|
| `huawei2024` | MindSpore + PyTorch  | CPU         | Comparative labs           |
| `torch-gpu`  | PyTorch              | GPU (CUDA)  | Heavy models (optional)    |

## Compatibility note (Windows)

When using both frameworks in the same environment on Windows, importing MindSpore before
PyTorch can cause a DLL loading error (`c10.dll`, WinError 1114). To avoid it:

- Each framework's labs are kept in separate notebooks.
- If both are needed in the same script, import `torch` **before** `mindspore`.

Additionally, PyTorch on Windows requires the **Microsoft Visual C++ Redistributable (x64)**
installed on the system.

## Environment setup

Using conda (recommended):

```bash
conda create -n huawei2024 python=3.10
conda activate huawei2024
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Verification:

```python
import torch          # import torch first (see compatibility note)
import mindspore
print("PyTorch:", torch.__version__)
print("MindSpore:", mindspore.__version__)
print("CUDA available:", torch.cuda.is_available())
```

## Progress

The commit history follows the study plan: **each commit corresponds to one completed
task**, so the project's progress can be followed chronologically.

| Block | Topic                       | Status |
|-------|-----------------------------|--------|
| 00    | Fundamentals                | 🔄     |
| 01    | Framework introduction      | ⬜     |
| 02    | MNIST                       | ⬜     |
| 03    | CNN / Images                | ⬜     |
| 04    | NLP                         | ⬜     |
| 05    | Transformer                 | ⬜     |
| 06    | Vision Transformer          | ⬜     |

## Stack

Python 3.10 · MindSpore 2.9 · PyTorch 2.12 (CPU) · NumPy · pandas · scikit-learn · Matplotlib

## License

MIT
