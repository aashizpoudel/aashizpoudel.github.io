---
title: "Docker Multi-Stage Builds for Python"
date: "2026-03-05"
tags: ["docker", "python", "devops"]
---

You can significantly reduce Docker image size for Python apps by using multi-stage builds. Build your dependencies in a builder stage with all build tools, then copy just the installed packages to a slim runtime image.

```dockerfile
# Builder stage
FROM python:3.11 AS builder
COPY requirements.txt .
RUN pip install --user -r requirements.txt

# Runtime stage
FROM python:3.11-slim
COPY --from=builder /root/.local /root/.local
COPY . /app
```
