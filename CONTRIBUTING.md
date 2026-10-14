# Contributing to Wildfire Detection System

Thank you for your interest in contributing to this project, built by **Touseef Ur Rehman**. Contributions of all kinds are welcome — bug reports, new features, documentation improvements, or UI enhancements.

---

## How to Contribute

### Reporting Bugs

1. Search the [Issues](.github/ISSUE_TEMPLATE/bug_report.md) page to make sure the bug hasn't already been reported.
2. If not, open a new issue using the [Bug Report Template](.github/ISSUE_TEMPLATE/bug_report.md).
3. Include a clear description, steps to reproduce, and expected vs. actual behavior.

### Proposing New Features

1. Check existing issues to avoid duplicates.
2. Open a new issue using the [Feature Request Template](.github/ISSUE_TEMPLATE/feature_request.md).
3. Explain the feature, its purpose, and how it fits the project.

### Submitting Pull Requests

1. Fork the repository and create a branch from `main`.
2. Follow the coding guidelines below.
3. Test your changes thoroughly before submitting.
4. Open a Pull Request using the [PR Template](.github/PULL_REQUEST_TEMPLATE.md).
5. Describe your changes clearly and wait for review.

---

## Coding Guidelines

- Follow **PEP 8** for all Python code.
- Use descriptive variable and function names.
- Keep functions small and focused on a single responsibility.
- Add comments where logic is non-obvious.
- Write clear, concise commit messages in imperative form (e.g. `Add satellite model path fix`).

---

## Project Structure

Before contributing, familiarise yourself with the layout:

```
analysis/
├── data/        — Training datasets
├── models/      — Trained .keras model files and scalers
└── notebooks/   — Jupyter notebooks for model training (run on Kaggle)

src/
├── app.py                     — Flask entry point
├── camera_functions.py        — Camera CNN inference
├── satellite_functions.py     — Satellite CNN inference
├── meteorological_functions.py — Weather risk prediction
├── email_alert.py             — Scheduled email alerts
├── static/                    — JS and image assets
└── templates/                 — Jinja2 HTML templates
```

---

## Need Help?

Open an issue and describe your question. All feedback is welcome.
