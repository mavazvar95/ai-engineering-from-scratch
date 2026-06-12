# Lesson 02 — Git & Collaboration

**Phase:** 00 — Setup & Tooling  
**Type:** Learn | **Lang:** --  
**Estimated time:** ~45 min  
**Status:** ✅ Reviewed

---

## What this lesson covers

Git workflows and collaboration practices adapted for AI/ML projects:
- Branch strategies for ML experiments
- What to commit and what to `.gitignore` (models, datasets, API keys)
- Tagging model versions
- Using GitHub for experiment tracking alongside code

---

## My notes

Already comfortable with Git for software projects. Key differences when applying it to ML/AI work:

- **Never commit model weights or datasets** — use `.gitignore` aggressively; large files go to cloud storage (S3, GDrive) or registries (HuggingFace Hub)
- **Experiment branches** — treat each training run or hyperparameter sweep as a branch; makes it easy to compare and roll back
- **Commit the config, not the output** — commit `config.yaml` with hyperparameters, not the resulting `.pkl` or `.pt` file
- **Tag releases** — `v1.0-baseline`, `v1.1-with-augmentation`; makes reproducibility much easier

---

## Reference

- [Original lesson](https://github.com/rohitg00/ai-engineering-from-scratch/tree/main/phases/00-setup-and-tooling/02-git-and-collaboration)
