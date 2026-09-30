# Eye Disease Classification — AI Track Log
# Path: MAVIS/EyeDiseaseClassification/AITrackImamHosen.md
# Rule: append every instruction / decision / change here.

---
## 2026-09-30 — Multi-pretrained compare + 30h resume

### User request
- Use dataset API: https://www.kaggle.com/datasets/gunavenkatdoddi/eye-diseases-classification
- Proper checkpoint if 30h ends — save everything for another Kaggle account
- Handle all issues (download, OOM, leakage, resume)

### What was done
- Added `ClassWorkOne/compare-all-pretrained-eye-disease.ipynb`
- Dataset slug: `gunavenkatdoddi/eye-diseases-classification`
  - kagglehub.dataset_download first
  - Kaggle CLI fallback
  - Or Add data under `/kaggle/input/eye-diseases-classification[/dataset]`
- Classes: cataract / diabetic_retinopathy / glaucoma / normal
- Protocol: MD5 dedupe + stratified 70/15/15, DEFAULT ImageNet, **no freeze**
- Models: alexnet, mobilenet_v3_large, efficientnet_b0, resnet50, vgg16, swin_t
- Output: `/kaggle/working/eye_multi_pretrained_v2/`
- Resume: copies prior `run_state.json` tree from `/kaggle/input`
- Stops ~11.5h/session; cumulative **30h** hard stop
- On pause/finish: `PAUSE.txt`, `RESUME_INSTRUCTIONS.txt`, `CHECKPOINT_MANIFEST.json/txt`,
  per-model `best.pth`/`last.pth`/`results.txt`, `FINAL_RESULTS.txt/json`, `top2/`
- Acc ≥ 0.999 flagged SUSPICIOUS
- Updated ClassWorkOne/README.md
