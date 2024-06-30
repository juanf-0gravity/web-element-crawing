# Contributing to TRANCE Web Crawler

Thank you for your interest in contributing to TRANCE Web Crawler! This document provides guidelines and information for contributors.

## Code of Conduct

By participating in this project, you are expected to uphold our Code of Conduct:
- Be respectful and inclusive
- Focus on what is best for the community
- Show empathy towards other community members

## How to Contribute

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates. When creating a bug report, include:

- **Use a clear and descriptive title**
- **Describe the exact steps to reproduce the problem**
- **Provide specific examples and code snippets**
- **Describe the behavior you observed and what you expected**
- **Include system information** (OS, Python version, browser version)

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear and descriptive title**
- **Provide a detailed description of the suggested enhancement**
- **Explain why this enhancement would be useful**
- **Include mockups or examples if applicable**

### Pull Requests

1. **Fork the repository** and create your branch from `main`
2. **Make your changes** following the coding standards below
3. **Add tests** for any new functionality
4. **Update documentation** as needed
5. **Ensure all tests pass**
6. **Create a pull request** with a clear title and description

## Development Setup

1. Fork and clone the repository
2. Set up your development environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   python -m playwright install chrome
   ```
3. Create a branch for your feature:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Coding Standards

### Python Code Style

- Follow [PEP 8](https://pep8.org/) style guide
- Use meaningful variable and function names
- Write docstrings for all public functions and classes
- Keep functions focused and small
- Use type hints where appropriate

### Code Organization

- Place new utilities in appropriate modules under `src/utils/`
- Keep crawler logic in `src/crawler/`
- Configuration should go in `src/config/`
- Follow existing package structure

### Example Code Style

```python
def process_interactive_element(element: dict, context: str) -> dict:
    """
    Process an interactive element and extract relevant information.
    
    Args:
        element: Dictionary containing element information
        context: The context in which the element appears
        
    Returns:
        Dictionary with processed element data
    """
    if not element or not isinstance(element, dict):
        raise ValueError("Element must be a non-empty dictionary")
    
    processed_data = {
        'type': element.get('type', 'unknown'),
        'context': context,
        'timestamp': time.time()
    }
    
    return processed_data
```

### JavaScript/Extension Code

- Use ES6+ features where appropriate
- Follow consistent indentation (2 spaces)
- Add comments for complex logic
- Use meaningful variable names

### Testing

- Write unit tests for new functionality
- Ensure all existing tests pass
- Test edge cases and error conditions
- Use meaningful test names that describe what is being tested

### Documentation

- Update README.md if adding new features
- Add docstrings to all public functions
- Update configuration documentation for new settings
- Include examples in docstrings where helpful

## Project Structure Guidelines

When adding new features:

- **Crawler logic** goes in `src/crawler/`
- **Utilities** go in `src/utils/`
- **Storage/database** logic goes in `src/storage/`
- **Configuration** goes in `src/config/`
- **Tools/scripts** go in `src/tools/`

## Commit Message Guidelines

Use clear and meaningful commit messages:

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- Reference issues and pull requests liberally after the first line

Examples:
```
Add support for custom form field detection

- Implement new detection algorithm for dynamic forms
- Add configuration options for detection sensitivity
- Update tests to cover new functionality

Fixes #123
```

## Release Process

Maintainers handle releases. Contributors should:
- Ensure their changes don't break existing functionality
- Update version numbers if instructed
- Help with testing release candidates

## Getting Help

If you need help or have questions:

1. Check existing documentation in `docs/`
2. Search existing issues on GitHub
3. Create a new issue with the "question" label
4. Join discussions in existing issues

## Recognition

Contributors will be acknowledged in the project. Significant contributors may be invited to become maintainers.

Thank you for contributing to TRANCE Web Crawler!