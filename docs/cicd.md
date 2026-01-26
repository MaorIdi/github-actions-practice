---
layout: default
title: CI/CD Pipeline
---

# CI/CD Pipeline

## Overview

This project uses GitHub Actions for continuous integration and deployment.

## Workflow Trigger

The pipeline runs on every push to the `main` branch.

## Pipeline Steps

### 1. Test Stage
- Checks out the code
- Builds Docker image up to test stage
- Runs pytest automatically during build
- Fails the pipeline if any test fails

### 2. Deploy Stage
- Only runs if tests pass
- Logs into GitHub Container Registry
- Builds production Docker image
- Pushes image with `latest` tag

## Multi-Stage Dockerfile

### Test Stage
```dockerfile
FROM python:3.11-slim AS test
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY main.py test_main.py .
RUN pytest test_main.py -v
```

### Production Stage
```dockerfile
FROM python:3.11-slim AS production
WORKDIR /app
RUN pip install --no-cache-dir fastapi uvicorn[standard] pydantic
COPY main.py .
CMD ["python", "main.py"]
```

## Security

- Uses GitHub Container Registry (GHCR)
- Authentication via GitHub token
- Only production dependencies in final image
- No test code in production build

## Usage

Push to main branch and the pipeline automatically:
1. ✅ Runs all tests
2. 🚀 Deploys if tests pass
3. ❌ Fails deployment if tests fail

[Back to Home](index.md)
