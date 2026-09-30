# ClassWorkOne — 4-Class Eye Disease Fine-Tuning

Same Kaggle dataset for every notebook:  
[gunavenkatdoddi/eye-diseases-classification](https://www.kaggle.com/datasets/gunavenkatdoddi/eye-diseases-classification)

## Notebooks (all 19 sections)

| Notebook | Model |
|----------|--------|
| `classworkone-eye-disease-classification.ipynb` | EfficientNet-B3 (main research recipe) |
| `finetune-vgg16-eye-disease.ipynb` | VGG16 |
| `finetune-efficientnet-eye-disease.ipynb` | EfficientNet-B0 |
| `finetune-resnet-eye-disease.ipynb` | ResNet50 |
| `finetune-mobilenet-eye-disease.ipynb` | MobileNetV3-Large |
| `finetune-alexnet-eye-disease.ipynb` | AlexNet |

Each of the five finetune notebooks uses the **same 19-section layout** as the main file:

1. Imports  
2. Config + auto-find dataset  
3. Reproducibility + device  
4. Validate + ImageFolder  
5. Class distribution  
6. Stratified 70/15/15 split  
7. Save split assignments  
8. Transforms  
9. Datasets + loaders  
10. Sample training images  
11. Build model  
12. Loss / metrics / train-eval (+ TTA)  
13. Two-phase training (head → full fine-tune)  
14. Training curves  
15. Best checkpoint + test (+ TTA)  
16. Class-wise + overall metrics  
17. Confusion matrices  
18. Save predictions + show errors  
19. Final summary  

## How to run on Kaggle

1. Upload one `.ipynb`  
2. **Add data** → `eye-diseases-classification`  
3. **Accelerator → GPU**  
4. **Run All**

Outputs: `/kaggle/working/<model>_eye_4class_results/`
