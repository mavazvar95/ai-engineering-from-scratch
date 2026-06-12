
# Lesson 01 — Dev Environment

**Phase:** 00 — Setup & Tooling  
**Type:** Build | **Lang:** Python, Node, Rust  
**Estimated time:** ~75 min  
**Status:** ✅ Reviewed

---

## What this lesson covers

Setting up a reproducible development environment for AI engineering work:
- Python environment isolation (venv / conda)
- Directory structure conventions for ML projects
- Essential tools: `nvtop`, `htop`, CUDA drivers
- Node.js and Rust toolchains for later phases
- Running the course's `verify.py` script to confirm everything works

---

## My setup

Already familiar with Python environments and project structure from prior ML work. Key things I noted or refreshed:

- **AI-specific folder conventions** — separating `data/`, `notebooks/`, `models/`, `outputs/` from the start avoids messy repos later
- **nvtop** — GPU monitoring tool I wasn't using before, useful for checking GPU utilization in real time
- **verify.py** — the course provides a script to confirm the environment is correctly set up; good practice to always have a verification step in ML projects

---

## Environment used

Google Colab — no local installation needed for Phases 0–2. Will evaluate GPU cloud (RunPod / Lambda Labs) from Phase 4 onwards when local GPU memory becomes a bottleneck.

---

## Reference

- [Original lesson](https://github.com/rohitg00/ai-engineering-from-scratch/tree/main/phases/00-setup-and-tooling/01-dev-environment)
- Course verify script: `python phases/00-setup-and-tooling/01-dev-environment/code/verify.py`
