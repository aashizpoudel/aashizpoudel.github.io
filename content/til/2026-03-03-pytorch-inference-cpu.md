---
title: "PyTorch Inference on CPU with torch.no_grad()"
date: "2026-03-03"
tags: ["python", "pytorch", "deep-learning"]
---

Always wrap inference code in `torch.no_grad()` context manager. It disables gradient computation and reduces memory consumption, which is important when deploying models on edge devices like Raspberry Pi.

```python
with torch.no_grad():
    output = model(input_tensor)
```
