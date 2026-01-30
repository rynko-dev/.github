# Contributing to Rynko

Thank you for your interest in contributing to Rynko! This document provides guidelines and information for contributors.

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment. We expect all contributors to:

- Be respectful and considerate in all interactions
- Welcome newcomers and help them get started
- Focus on constructive feedback
- Accept responsibility for mistakes and learn from them

## How to Contribute

### Reporting Bugs

If you find a bug, please open an issue with:

1. **Clear title** describing the problem
2. **Steps to reproduce** the issue
3. **Expected behavior** vs **actual behavior**
4. **Environment details** (SDK version, Node/Python version, OS)
5. **Code samples** if applicable (remove sensitive data)

### Suggesting Features

We welcome feature suggestions! Please open an issue with:

1. **Clear description** of the feature
2. **Use case** explaining why it's needed
3. **Proposed solution** (if you have one)
4. **Alternatives considered**

### Pull Requests

1. **Fork** the repository
2. **Create a branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following our coding standards
4. **Write/update tests** for your changes
5. **Run tests** to ensure everything passes
6. **Commit** with clear, descriptive messages
7. **Push** to your fork and open a PR

#### PR Guidelines

- Keep PRs focused on a single change
- Include tests for new functionality
- Update documentation if needed
- Link related issues using `Fixes #123` or `Closes #123`

## Development Setup

### SDKs

Each SDK has its own setup instructions in its README:

- [Node.js SDK](https://github.com/rynko-dev/sdk-node)
- [Python SDK](https://github.com/rynko-dev/sdk-python)
- [Java SDK](https://github.com/rynko-dev/sdk-java)

### General Requirements

- Follow existing code style and patterns
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed

## Commit Message Format

We use conventional commits:

```
type(scope): description

[optional body]

[optional footer]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(sdk): add batch document generation support
fix(auth): handle token refresh edge case
docs(readme): update installation instructions
```

## Testing

- Write unit tests for new functionality
- Ensure all existing tests pass before submitting PR
- Aim for meaningful test coverage, not just high numbers

## Documentation

- Update README if adding new features
- Add JSDoc/docstrings for public APIs
- Include code examples where helpful

## Questions?

- Check existing [issues](https://github.com/rynko) first
- Open a new issue for questions
- Email us at support@rynko.dev

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see LICENSE file in each repository).

---

Thank you for contributing to Rynko!
