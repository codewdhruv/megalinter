---
title: Configure custom commands to run before linters
description: Customize your MegaLinter run by installing linters extensions with npm, pip, or even raw bash before linters are run
---
<!-- markdownlint-disable MD013 -->
<!-- @generated by .automation/build.py, please don't update manually -->
<!-- config-precommands-section-start -->

# Pre-commands

MegaLinter can run custom commands before running linters (for example, installing an plugin required by one of the linters you use)

Example in `.mega-linter.yml` config file

```yaml
PRE_COMMANDS:
  - command: npm install eslint-plugin-whatever
    cwd: "root"        # Will be run at the root of MegaLinter docker image
  - command: echo "pre-test command has been called"
    cwd: "workspace"   # Will be run at the root of the workspace (usually your repository root)
    continue_if_failed: False  # Will stop the process if command is failed (return code > 0)
  - command: pip install flake8-cognitive-complexity
    venv: flake8 # Will be run within flake8 python virtualenv. There is one virtualenv per python-based linter, with the same name
```


<!-- config-precommands-section-end -->
