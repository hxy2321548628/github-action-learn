# 04. 高级功能

> 🌐 **语言 / Language：** [English](./README.md) ｜ **简体中文**

本模块涵盖 GitHub Actions 的多项高级能力。每个主题都由 [`.github/workflows`](../.github/workflows) 中的一个 workflow 来演示，其文件名以 `04-advanced-features--` 开头。

## 主题与对应 Workflow

- **运行器类型（Runner Types）** – [`04-advanced-features--01-runner-types.yaml`](../.github/workflows/04-advanced-features--01-runner-types.yaml)
  - 展示 GitHub 托管的 Linux/Windows/macOS 运行器、容器 job，以及第三方运行器
- **制品（Artifacts）** – [`04-advanced-features--02-artifacts.yaml`](../.github/workflows/04-advanced-features--02-artifacts.yaml)
  - 一个 job 上传一个文本文件，第二个 job 下载并显示它
- **缓存（Caching）** – [`04-advanced-features--03-caching.yaml`](../.github/workflows/04-advanced-features--03-caching.yaml)
  - 演示 `actions/cache` action 以及 `setup-node` 内置的缓存能力
- **GitHub 权限（GitHub Permissions）** – [`04-advanced-features--04-github-permissions.yaml`](../.github/workflows/04-advanced-features--04-github-permissions.yaml)
  - 在 pull request 场景下对比只读与读写的 `GITHUB_TOKEN` 权限
- **第三方认证（Third-Party Authentication）** – [`04-advanced-features--05-third-party-auth.yaml`](../.github/workflows/04-advanced-features--05-third-party-auth.yaml)
  - 对比静态 AWS 凭据与基于 OIDC 的认证方式
- **矩阵与条件（Matrix & Conditionals）** – [`04-advanced-features--06-matrix-and-conditionals.yaml`](../.github/workflows/04-advanced-features--06-matrix-and-conditionals.yaml)
  - 在二维矩阵上运行 job，并依据条件跳过某些 step
- **动态矩阵（Dynamic Matrix）** – [`04-advanced-features--07-dynamic-matrix.yaml`](../.github/workflows/04-advanced-features--07-dynamic-matrix.yaml)
  - 动态生成一组需要运行的 job，交给 matrix 策略执行
- **工作流命令（Workflow Commands）**
[`04-advanced-features--08-workflow-commands.yaml`](../.github/workflows/04-advanced-features--08-workflow-commands.yaml)
  - 演示一些特殊格式的指令，用于与 GitHub Action 运行器通信，从而控制 workflow 的行为

缓存示例还包含一个极简的 Node 项目：[`caching/minimal-node-project`](./caching/minimal-node-project)。
