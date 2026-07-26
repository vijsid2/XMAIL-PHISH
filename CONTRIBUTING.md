# Contributing to XMAIL-PHISH

Thank you for your interest in contributing to XMAIL-PHISH! This document provides guidelines for contributing.

## Code of Conduct

- Be respectful and inclusive
- Focus on the code, not individuals
- Report security issues privately
- No harassment or discrimination

## How to Contribute

### 1. Report Bugs

- Check if issue already exists
- Provide detailed description
- Include steps to reproduce
- Include error logs/screenshots
- Specify your environment (OS, Python version, etc.)

### 2. Suggest Features

- Describe the problem it solves
- Explain your proposed solution
- List any alternative approaches
- Provide use cases

### 3. Submit Code Changes

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make changes following code style guidelines
4. Write/update tests
5. Commit with clear messages: `git commit -m "Add feature: description"`
6. Push to your fork
7. Create a Pull Request

## Code Style

### Python
- Follow PEP 8
- Use type hints
- Max line length: 100 characters
- Use docstrings for all functions

### JavaScript
- Use ES6+ syntax
- Use meaningful variable names
- Add comments for complex logic
- Format with Prettier

### SQL
- Use uppercase for keywords
- Use meaningful table/column names
- Add comments for complex queries

## Testing

- Write unit tests for new features
- Maintain >80% code coverage
- Run tests before submitting PR
- Test on multiple Python versions if applicable

## Security

- Never commit secrets or API keys
- Run security scans before submitting
- Report vulnerabilities privately
- Follow OWASP guidelines

## Documentation

- Update README if functionality changes
- Add docstrings to all functions
- Include examples for new features
- Update CHANGELOG.md

## Commit Messages

Use clear, descriptive commit messages:

```
Type: Brief description (50 chars max)

Detailed explanation if needed. Wrap at 72 characters.
Explain what problem this solves and why this is the solution.

Fixes #123
```

Types: feature, bugfix, docs, style, refactor, test, chore

## Pull Request Process

1. Update documentation
2. Add tests for new code
3. Ensure all tests pass
4. Update CHANGELOG.md
5. Request review from maintainers
6. Address review comments
7. Squash commits if requested
8. Await merge

## Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/XMAIL-PHISH.git
cd XMAIL-PHISH

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install development dependencies
pip install -r backend/requirements.txt
pip install pytest pytest-cov black flake8 mypy

# Run tests
pytest backend/tests/

# Format code
black backend/

# Lint code
flake8 backend/

# Type check
mypy backend/
```

## Questions?

Feel free to create an issue or discussion for questions.

Thank you for contributing! 🚀
