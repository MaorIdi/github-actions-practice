---
layout: default
title: Home
---

# GitHub Actions Practice

A FastAPI application demonstrating CI/CD best practices with multi-stage Docker builds.

## Features

- **FastAPI Application**: REST API with multiple endpoints
- **Automated Testing**: Pytest tests run automatically
- **Multi-Stage Docker Build**: Separate test and production stages
- **GitHub Actions CI/CD**: Automated testing and deployment
- **Container Registry**: Images pushed to GitHub Container Registry

## API Endpoints

### GET /
Returns a welcome message.

### GET /items/{item_id}
Retrieve an item by ID with optional query parameter.

### POST /items/
Create a new item with name, price, description, and optional tax.

## Running Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py

# Run tests
pytest test_main.py -v
```

## Docker

```bash
# Build and run with Docker
docker build --target production -t app .
docker run -p 8000:8000 app
```

## CI/CD Pipeline

The GitHub Actions workflow automatically:
1. Runs all tests when code is pushed
2. Builds production Docker image
3. Pushes to GitHub Container Registry
4. Only deploys on successful tests

See [CI/CD Workflow](cicd.md) for details.
