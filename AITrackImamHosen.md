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

---
## 2026-10-08 — GitHub-direct run + error/timeout/quota checkpoints

### User request
- Handle the pipeline through GitHub directly
- Checkpoint on error / timeout / quota / etc. for another account

### What was done
- Synced repo to `https://github.com/mdimamhosen/MAVIS-EyeDisease`
- Notebook now:
  - Pulls prior state from GitHub branch `kaggle-checkpoints` + Release `eye-checkpoint-latest`
  - Pushes light artifacts to that branch; weights zip to Release (needs Kaggle Secret `GITHUB_TOKEN`)
  - `safe_train_model`: catches KeyboardInterrupt, CUDA OOM, timeout, quota/limit, generic errors
  - Always `flush_checkpoint_bundle` + optional GitHub push
  - Writes `ERROR.txt` / `PAUSE.txt` / `CHECKPOINT_MANIFEST.*`
- Added `ClassWorkOne/KAGGLE_GITHUB.md` runbook
