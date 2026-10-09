# 03. 核心功能

> 🌐 **语言 / Language：** [English](./README.md) ｜ **简体中文**

本模块演示所有 GitHub Actions workflow 都会用到的基础构件。每个示例 workflow 都位于 `.github/workflows/` 目录下，并遵循 `03-core-features--<name>.yaml` 的命名规则。

## 包含的 Workflow

- [**03-core-features--01-hello-world.yaml**](../.github/workflows/03-core-features--01-hello-world.yaml) —— 最基础的 workflow，通过一个内联 bash 步骤打印一条消息。
- [**03-core-features--02-step-types.yaml**](../.github/workflows/03-core-features--02-step-types.yaml) —— 展示不同的 step 类型，包括 bash、Python，以及一个来自 Marketplace 的 action。
- [**03-core-features--03-workflows-jobs-steps.yaml**](../.github/workflows/03-core-features--03-workflows-jobs-steps.yaml) —— 说明 workflow 如何组织成 job 与 step，以及 job 之间如何并行运行或相互依赖。
- [**03-core-features--04-triggers-and-filters.yaml**](../.github/workflows/03-core-features--04-triggers-and-filters.yaml) —— 探讨触发事件与路径过滤器。该 workflow 会监听 [`03-core-features/filters`](./filters/) 目录内的变更。
- [**03-core-features--05-environment-variables.yaml**](../.github/workflows/03-core-features--05-environment-variables.yaml) —— 讲解 workflow、job、step 三个层级的变量作用域。
- [**03-core-features--06-passing-data.yaml**](../.github/workflows/03-core-features--06-passing-data.yaml) —— 使用 job outputs 与环境变量在 job 之间传递数据。
- [**03-core-features--07-secrets-and-variables.yaml**](../.github/workflows/03-core-features--07-secrets-and-variables.yaml) —— 演示如何从仓库（repository）和 environment 两个层级注入 secret 与 variable。

`filters` 目录中存放着「触发器与过滤器」这个 workflow 所使用的示例文件。
