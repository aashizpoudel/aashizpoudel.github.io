---
title: "Using bore tunnel to port forward jupyter notebook"
date: "2026-02-28"
tags: ["ssh", "jupyter", "linux"]
---

When working on a remote server, you can forward a Jupyter notebook port to your local machine:

```bash
bore local 8888 --to bore.pub --remote-port 8992
```

Then open `bore.pub:8992` in your browser.
