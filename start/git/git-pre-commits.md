---
description: >-
  Набір допоміжних практик, покликаний підвищити якість розробки та уніфікувати
  підходи до форматування коду різних розробників відповідно до прийнятих
  стандартів
---

# Git pre-commits

### **Налаштування "pre-commits"**

Для підвищення якості розробки та коду можу бути реалізовано використання спеціальної бібліотеки: pre-commits. Вона дозволяє встановлювати певні тригери, так звані pre-commit hooks (якорі), які будуть виконуватися під час запуску певних команд при роботі із репозиторіями, наприклад commit, push etc.

> **Важливо!!!**: Документація по роботі із pre-commits: https://pre-commit.com/

Загальний алгоритм може бути таким у нашому форматі:

1. Встановлюємо бібліотеку: `pip install pre-commit`
2. Створюємо `.pre-commit-config.yaml` файл у нашому репозиторії та налаштовуємо hooks:

```python
minimum_pre_commit_version: 2.13.0
default_stages: [commit, push]
exclude: '^$'
default_language_version:
  python: python3.8
repos:
  - repo: local
    hooks:
    - id: autoflake
      name: Remove unused variables and imports
      entry: bash -c 'autoflake "$@"; git add -u' -- # This runs autoflake and stages the reformatted python files before running autoflake again, which should then "pass"
      language: python
      args: ["--in-place", "--remove-all-unused-imports", "--remove-unused-variables", "--expand-star-imports", "--ignore-init-module-imports"]
      files: \.py$
    - id: isort
      name: Sorting import statements
      entry: bash -c 'isort "$@"; git add -u' --
      language: python
      args: ["--filter-files"]
      files: \.py$
    - id: black
      name: Black Python code formatting
      entry: bash -c 'black "$@"; git add -u' --
      language: python
      types: [python]
      language_version: python3.8
      args: ["--line-length=120"]
    - id: flake8
      name: Flake8 linting pep8, pyflakes and circular complexity
      entry: flake8
      language: system
      types: [python]
      args: ["--max-line-length=120", "--ignore=D100,D104,E203,E402,E501,W503", "--docstring-convention=google"]
    - id: tests
      name: run tests
      entry: pytest tests -v
      language: python
      always_run: true
      pass_filenames: false
      stages: [push]  # Makes sure that tests are only run when pushing the code
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.0.1
    hooks:
    - id: trailing-whitespace
    - id: end-of-file-fixer
    - id: double-quote-string-fixer
    - id: check-docstring-first
    - id: check-yaml
    - id: debug-statements
    - id: name-tests-test
    - id: requirements-txt-fixer
  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v0.812
    hooks:
    - id: mypy
```

1. Виконуємо команду pre-commit install - встановлюємо hooks у цьому репозиторії
2. Тоді алгоритм роботи звичайний:

<pre class="language-bash"><code class="lang-bash"><strong>pre-commit install 
</strong>git add .pre-commit-config.yaml
<strong>git add .
</strong>git commit -m "message"

# Якщо потрібно закомітити без перевірки, тоді:
git commit --no-verify -m "message"
</code></pre>
