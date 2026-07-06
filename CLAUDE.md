# CLAUDE.md

本文件为 Claude Code 在此仓库工作时提供指导。

## 沟通语言

所有对话与代码注释均使用**简体中文**。

## 项目概览

`starter` 是一个 Python 项目模板，要求 Python >= 3.13，使用 **uv** 管理依赖与虚拟环境，使用 **poe（poethepoet）** 作为任务运行器。

> 注意：本项目为 Python 项目，不使用 pnpm / fnm。

## 常用命令

依赖与环境：

```bash
uv sync              # 安装依赖并创建 .venv
uv run poe setup     # 安装 pre-commit 钩子（含 commit-msg）
source .venv/bin/activate
```

开发与任务（通过 poe）：

```bash
poe dev      # 运行主程序（python -m starter.main）
poe format   # ruff format src
poe lint     # ruff check src --fix
poe type     # ty check
poe check    # 依次执行 format、lint、type
poe build    # uv build
poe tag      # cz bump，生成新版本标签
```

安装后也可直接使用 `starter` 命令运行主程序。

## 代码规范

- 行宽 99 字符，使用 ruff format 格式化。
- Lint 规则见 `pyproject.toml` 的 `[tool.ruff.lint]`，包含 pyflakes、pycodestyle、isort、pep8-naming、pyupgrade、flake8-bugbear 等。
- **禁止相对导入**（`ban-relative-imports = "all"`），一律使用绝对导入。
- `F401`（未使用的导入）不自动修复，需手动处理。
- 类型检查使用 **ty**，检查范围为 `src`。

## 提交规范

使用 Conventional Commits，由 commitizen 管理：

- 格式：`type(scope): message`，例如 `feat(core): add new feature`、`fix(api): resolve issue`。
- 提交时 pre-commit 会运行 `poe check`，commit-msg 阶段会校验提交信息格式。
- 版本标签格式为 `v$version`，通过 `poe tag`（`cz bump`）生成。

## 项目结构

```
starter-python/
├── src/
│   └── starter/
│       ├── __init__.py
│       └── main.py
├── pyproject.toml
├── README.md
└── uv.lock
```
