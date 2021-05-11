# Configure your Editor / IDE

Basically you will need to configure your editor which will apply flake8, black & isort ***AUTOMATICALLY EVERY TIME YOU SAVE YOUR FILE***

Install & configure these plugins/tools in your IDE/Editor:

1. [Black](https://black.readthedocs.io/en/stable/editor_integration.html)
2. [EditorConfig](https://editorconfig.org/#pre-installed)

Here are the configuration files:

### Additional pyproject.toml config

```
[tool.black]
line-length = 88
include = '\.pyi?$'
exclude = '''
/(
    \.git
  | \.hg
  | \.mypy_cache
  | \.tox
  | \.venv
  | _build
  | buck-out
  | build
  | dist
  | migrations
)/
'''

[tool.isort]
# Make sure this matches `*.py` in .editorconfig
ensure_newline_before_comments = true
force_grid_wrap = 0
include_trailing_comma = true
line_length = 88
multi_line_output = 3
use_parentheses = true
```

### .flake8
```
[flake8]
max-line-length = 88
```

### .editorconfig
```
root = true

[*]
end_of_line = lf
insert_final_newline = false

[Makefile]
indent_style = tab

[*.yml]
indent_size = 2
indent_style = space

[*.py]
# Make sure this matches `tool.isort` in pyproject.toml
charset = utf-8
ensure_newline_before_comments = true
force_grid_wrap = 0
include_trailing_comma = true
indent_size = 4
indent_style = space
line_length = 88
multi_line_output = 3
use_parentheses = true
```

### .pre-commit-config.yaml

```
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v3.2.0
    hooks:
    -   id: trailing-whitespace
    -   id: end-of-file-fixer
    -   id: check-added-large-files

-   repo: https://github.com/psf/black
    rev: 21.5b0
    hooks:
      - id: black
        language_version: python3
        exclude: ^.*\b(migrations)\b.*$
```


# Vim / NeoVim

Please refer [@dhilipsiva](https://github.com/dhilipsiva)'s [init.vim in .files repository](https://github.com/dhilipsiva/.files/blob/master/.config/nvim/init.vim)
