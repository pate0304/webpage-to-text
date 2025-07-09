# Installation Guide

## Quick Installation

### Option 1: Install from Source (Recommended for Development)

```bash
# Clone or download the project
cd webpage-to-text

# Install in development mode
pip install -e .

# Or install dependencies manually
pip install -r requirements.txt
```

### Option 2: Install as Package

```bash
# Install the package
pip install .

# Or with development dependencies
pip install -e .[dev]
```

## Verify Installation

```bash
# Check if CLI is available
webpage-to-text --help

# Create a sample config
webpage-to-text --create-config test.yaml

# Test with a simple URL
webpage-to-text --url https://httpbin.org/html --output ./test_output/
```

## Usage Examples

### 1. Using the CLI

```bash
# Extract from single URL
webpage-to-text --url https://example.com --output ./texts/

# Extract from multiple URLs
webpage-to-text --url https://example.com --url https://example.com/about

# Use configuration file
webpage-to-text --config configs/eau_palm_beach.yaml

# Custom rate limiting
webpage-to-text --url https://example.com --rate-limit 2.0
```

### 2. Using Python API

```python
from webpage_to_text import WebPageExtractor

# Basic usage
extractor = WebPageExtractor(output_dir="./my_texts")
result = extractor.extract_url("https://example.com")

# Multiple URLs
urls = ["https://example.com", "https://example.com/about"]
results = extractor.extract_urls(urls)

# With configuration
config = {
    "urls": ["https://example.com"],
    "output_dir": "./texts",
    "rate_limit": 1.0
}
results = extractor.extract_from_config(config)
```

### 3. Configuration Files

Create a YAML configuration file:

```yaml
name: "My Website Extraction"
output_dir: "./extracted_texts"
rate_limit: 1.0
urls:
  - "https://example.com"
  - "https://example.com/about"
filenames:
  - "home.txt"
  - "about.txt"
```

## Testing

Run the test suite:

```bash
# Install test dependencies
pip install -e .[dev]

# Run tests
pytest

# Run with coverage
pytest --cov=webpage_to_text --cov-report=html
```

## Development Setup

```bash
# Install development dependencies
pip install -e .[dev]

# Install pre-commit hooks
pre-commit install

# Format code
black src/
flake8 src/
mypy src/
```

## Troubleshooting

### Common Issues

1. **Import Error**: Make sure you installed the package with `pip install -e .`
2. **Permission Error**: Check that output directory is writable
3. **Rate Limiting**: Some sites may require slower rate limits
4. **SSL Errors**: Some sites may have SSL certificate issues

### Dependencies

Required packages:
- `llama-index>=0.9.0`
- `llama-index-readers-web>=0.1.0`
- `beautifulsoup4>=4.10.0`
- `requests>=2.25.0`
- `PyYAML>=6.0`

## Support

- Check the [README.md](README.md) for detailed documentation
- Review [examples/](examples/) for usage patterns
- Test with provided [configs/](configs/) for common use cases