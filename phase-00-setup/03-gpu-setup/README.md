# Lesson 03 — GPU Setup & Cloud

**Phase:** 00 — Setup & Tooling  
**Type:** Build | **Lang:** Python  
**Estimated time:** ~45 min  
**Status:** ✅ Complete

---

## What this lesson covers

- Verifying GPU availability with PyTorch's CUDA API
- Configuring Google Colab with a T4 GPU
- Benchmarking matrix multiplication on CPU vs GPU
- Estimating the largest model that fits in VRAM using the fp16 rule of thumb

---

## My results

Environment: **Google Colab — Tesla T4 GPU**

| | Value |
|---|---|
| CUDA available | True |
| PyTorch version | 2.11.0+cu128 |
| GPU | Tesla T4 |
| VRAM | 15.6 GB |
| Max model size (fp16) | ~8B parameters |

### CPU vs GPU benchmark — matrix multiplication (5000×5000)

| | Time |
|---|---|
| CPU | 2.035s |
| GPU | 0.199s |
| **Speedup** | **10x** |

The GPU is 10x faster on a single matrix multiplication. In real training, with thousands of these operations chained together, the difference is orders of magnitude larger — the reason an 8-hour CPU training run takes 10 minutes on GPU.

---

## Key concepts

**CUDA** — NVIDIA's parallel computing platform that lets PyTorch run operations on the GPU instead of the CPU.

**VRAM** — Memory on the GPU, separate from system RAM. Models live here during training. Limits how large a model you can run.

**fp16 (half precision)** — 16-bit floating point format. Uses half the memory of fp32 with minimal accuracy loss. Rule of thumb: 2 bytes per parameter. With 15.6 GB VRAM → max ~8B parameters.

**`.to("cuda")`** — Moves a tensor from CPU RAM to GPU VRAM. Required before any GPU computation.

**`torch.cuda.synchronize()`** — GPU operations are asynchronous. This forces the code to wait until the GPU finishes before measuring time.

---

## Notebook

[03-gpu-setup.ipynb](./03-gpu-setup.ipynb)

---

## Reference

- [Original lesson](https://github.com/rohitg00/ai-engineering-from-scratch/tree/main/phases/00-setup-and-tooling/03-gpu-setup-and-cloud)
