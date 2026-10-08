# Run on Kaggle via GitHub + resume

Repo: https://github.com/mdimamhosen/MAVIS-EyeDisease  
Notebook: `ClassWorkOne/compare-all-pretrained-eye-disease.ipynb`  
Dataset: https://www.kaggle.com/datasets/gunavenkatdoddi/eye-diseases-classification

## First run

1. New Kaggle notebook → **File → Import notebook** from this GitHub path, **or** clone:

```python
!git clone https://github.com/mdimamhosen/MAVIS-EyeDisease.git
%cd MAVIS-EyeDisease/ClassWorkOne
```

2. Settings → **Internet ON**, **GPU ON**
3. Optional: Add data → `eye-diseases-classification` (else auto-download via kagglehub)
4. Optional but recommended: **Add-ons → Secrets** → `GITHUB_TOKEN` (classic PAT with `repo` scope)
5. Open `compare-all-pretrained-eye-disease.ipynb` → **Run All**

## What gets checkpointed

On epoch end, timeout (~11.5h session / 30h cumulative), error, CUDA OOM, quota/limit, or interrupt:

- Local: `/kaggle/working/eye_multi_pretrained_v2/` (`last.pth`, `best.pth`, `run_state.json`, …)
- `PAUSE.txt` / `ERROR.txt` / `CHECKPOINT_MANIFEST.*`
- If `GITHUB_TOKEN` set:
  - light files → branch `kaggle-checkpoints`
  - weights zip → Release tag `eye-checkpoint-latest`

## Resume on another Kaggle account

1. Same notebook from GitHub
2. Same secret `GITHUB_TOKEN` (so it can pull the checkpoint branch + release)
3. Internet + GPU → **Run All**
4. Notebook auto-pulls GitHub checkpoints, skips finished models, resumes `last.pth`

Fallback without token: download the Kaggle **Output** folder from the old run → **Add data** on the new account → Run All.