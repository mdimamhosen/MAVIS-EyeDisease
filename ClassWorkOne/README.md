# ClassWorkOne — 4-Class Eye Disease Fine-Tuning

Same Kaggle dataset for every notebook:  
[gunavenkatdoddi/eye-diseases-classification](https://www.kaggle.com/datasets/gunavenkatdoddi/eye-diseases-classification)

**Classes:** cataract / diabetic_retinopathy / glaucoma / normal

## Single-model notebooks

| Notebook | Model |
|----------|--------|
| `classworkone-eye-disease-classification.ipynb` | EfficientNet-B3 (main research recipe) |
| `finetune-vgg16-eye-disease.ipynb` | VGG16 |
| `finetune-efficientnet-eye-disease.ipynb` | EfficientNet-B0 |
| `finetune-resnet-eye-disease.ipynb` | ResNet50 |
| `finetune-mobilenet-eye-disease.ipynb` | MobileNetV3-Large |
| `finetune-alexnet-eye-disease.ipynb` | AlexNet |

## Multi-model compare (recommended for baseline ranking)

| Notebook | Model |
|----------|--------|
| `compare-all-pretrained-eye-disease.ipynb` | All 6 (DEFAULT, no freeze, clean split, 30h resume) |

Dataset API: `gunavenkatdoddi/eye-diseases-classification` via **kagglehub** (+ CLI fallback), or Add data.

1. Upload notebook → **Internet ON** → GPU → Run All  
2. Hash-dedupe → stratified 70/15/15  
3. Trains: AlexNet, MobileNetV3-Large, EfficientNet-B0, ResNet50, VGG16, Swin-T  
4. Output: `/kaggle/working/eye_multi_pretrained_v2/`  
5. Top-2 → `…/top2/` + `FINAL_RESULTS.txt/json`

### 30h / new-account resume

- Per-epoch `last.pth` + `best.pth` + `run_state.json`  
- Session stop ~11.5h; cumulative hard stop **30h** with full flush  
- `PAUSE.txt`, `RESUME_INSTRUCTIONS.txt`, `CHECKPOINT_MANIFEST.txt/json`  
- New account: download output folder → **Add data** → Run All  

## How to run single-model notebooks on Kaggle

1. Upload one `.ipynb`  
2. **Add data** → `eye-diseases-classification` (or Internet ON for API download)  
3. **Accelerator → GPU**  
4. **Run All**

Outputs: `/kaggle/working/<model>_eye_4class_results/`
