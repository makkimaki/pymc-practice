# pymc-practice

This repo uses **uv** to manage:
- Python version (**3.12**)
- Virtual Env. (`.venv/`)
- Dependencies (`pyproject.toml` + `uv.lock`)

## Prerequisites
- macOS (apple silicon)
- Homebrew

# Topic
## Table of Contents
- [Command Overview](#commandoverview)
- [Initialize](#initialize)
- [Python Versioning](#python-versioning)
- [Virtual Environment](#virtual-environment)
- [Install dependencies](#install-dependencies)
- [Run your code](#run-your-code)
- [Jupyter / VS Code](#jupyter--vs-code)
- [What to commit / ignore](#what-to-commit--ignore)


# Command　Overview
```
1. uv init              ← プロジェクト定義を作る（最重要）
2. uv python install
3. uv python pin
4. uv venv
5. uv add pymc
6. uv sync
```

## Initialize
```
uv init
```

## Python versioning
### Python install
```
uv python install 3.12

## 使用バージョンの固定 > .python-versionファイルが生成
uv python pin 3.12
```

確認：
```
uv python list
```

## Virtual Environment
```
uv venv .venv
```
- pinされたpython versionで
- `.venv/`を作る

```
project/
├── .python-version
├── .venv/
│   └── bin/python  # ← Python 3.12
```

以降は
```
uv run python
```
- 必ず、.venv + Python 3.12になる。

## Install dependencies
```
uv add pymc
uv sync
```
※ `pyproject.toml`にはpymcしか書かれてないが、直接依存を書く場所でああり、推移依存はなくて問題ない。`uv.lock`に書かれる。

## Run your code
```
uv run python main.py
```

## Jupyter / VS Code

This project uses a local virtual environment under `.venv/`.

### Setup kernel for VS Code
```bash
uv add jupyter ipykernel
uv sync

uv run python -m ipykernel install \
  --user \
  --name pymc-practice \
  --display-name "Python 3.12 (pymc-practice)"
```








## What to commit / ignore
Commit: 
- `pyproject.toml`
- `uv.lock`
- `.python-version`
- `README.md`

Ignore (add to `.gitignore`)
- .venv/
- __pycache__/
- .ipynb_checkpoints/
- .env
- .DS_Store
