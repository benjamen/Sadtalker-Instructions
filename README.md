# Sadtalker-Instructions (windows 20/06/2025)

Perfect — your system is running **CUDA 12.9**, which is **too new for most current prebuilt PyTorch and xFormers wheels**.

⚠️ **Important context**: As of mid-2025, PyTorch **does not yet provide official wheels for CUDA 12.9**, and most libraries like `xformers` and `diffusers` expect **CUDA 11.8 or 12.1**.

---

## ✅ Your Best Path: Use CUDA 12.1-Compatible PyTorch

You’ll need to install PyTorch and `xformers` for **CUDA 12.1**, which is the newest *officially supported* runtime as of now.

---

### 🧼 Step 1: Clean Broken Torch Packages

```bash
pip uninstall torch torchvision torchaudio -y
```

---

### 🚀 Step 2: Install PyTorch for CUDA 12.1

```bash
pip install torch==2.2.2+cu121 torchvision==0.17.2+cu121 torchaudio==2.2.2 --index-url https://download.pytorch.org/whl/cu121
```

> ✅ This combo supports your **RTX 4070**, works with **Python 3.10**, and uses **CUDA 12.1** which is compatible with your driver.

---

### 🔧 Step 3: Install xformers Compatible with Torch 2.2.2

Use this wheel for Windows + Python 3.10:

```bash
pip install https://github.com/facebookresearch/xformers/releases/download/0.0.26.post1/xformers-0.0.26.post1-cp310-cp310-win_amd64.whl
```

---

### 🔍 Step 4: Verify GPU Works

```bash
python -c "import torch; print(torch.cuda.is_available())"
```

Expected output:

```
True
```

---

### 🧪 Step 5: Run Your App

```bash
python app_en.py
```

---

Let me know if you want to generate a working `requirements.txt` file once this is stable, or if any step throws an error.

