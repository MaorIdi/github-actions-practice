# GitHub Actions Practice

A FastAPI application demonstrating CI/CD best practices with multi-stage Docker builds and automated deployment.

## 📚 Documentation

Visit the full documentation at: **https://maoridi.github.io/github-actions-practice/**

## Features

- ✅ Automated testing with pytest
- 🐳 Multi-stage Docker builds
- 🚀 CI/CD pipeline with GitHub Actions
- 📦 Container images in GitHub Container Registry
- 📖 Jekyll documentation site

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py

# Access the API
curl http://localhost:8000
```

## Running Tests

```bash
pytest test_main.py -v
```

## Docker

```bash
# Build and run
docker build --target production -t app .
docker run -p 8000:8000 app
```

## CI/CD Pipeline

The pipeline automatically:
1. Runs tests on every push to main
2. Builds production Docker image if tests pass
3. Pushes to GitHub Container Registry
4. Deploys documentation to GitHub Pages

## API Endpoints

- `GET /` - Welcome message
- `GET /items/{item_id}` - Get item by ID
- `POST /items/` - Create new item

## License

MIT
