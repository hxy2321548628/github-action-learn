# 06. 编写 Action

> 🌐 **语言 / Language：** [English](./README.md) ｜ **简体中文**

本模块演示如何构建自定义 GitHub Action 以及可复用工作流。下面每个示例都有一个对应的 workflow 位于 `.github/workflows/` 中，遵循 `06-authoring-actions--<name>.yaml` 的命名规则。

## 复合 Action（Composite Action）
- **目录：** `composite-action`
- **Workflow：** [`.github/workflows/06-authoring-actions--01-composite-action.yaml`](../.github/workflows/06-authoring-actions--01-composite-action.yaml)
- **作用：** 定义一个简单的 action，打印一句问候语并输出一个
  随机数。对应的 workflow 演示了在两个彼此独立的 job 中分别调用该 action。

## 可复用工作流（Reusable Workflows）
- **目录：** `reuseable-workflow`
- **Workflow：**
 - [`.github/workflows/06-authoring-actions--02-reuseable-workflows-source.yaml`](../.github/workflows/06-authoring-actions--02-reuseable-workflows-source.yaml) – 定义可复用工作流
 - [`.github/workflows/06-authoring-actions--03-reuseable-workflows-caller.yaml`](../.github/workflows/06-authoring-actions--03-reuseable-workflows-caller.yaml) – 调用该可复用工作流
  - **作用：** 源工作流对外暴露 inputs 与 secrets，并在一个 job 中把它们打印出来。
    调用方工作流由手动触发，并分别以相对路径和具体 commit 引用的方式调用源工作流。

## JavaScript 与 TypeScript Action
- **目录：** `javascript-actions`
- **Workflow：** [`.github/workflows/06-authoring-actions--04-javascript-actions.yaml`](../.github/workflows/06-authoring-actions--04-javascript-actions.yaml)
- **作用：** 运行三个 job，分别展示 JavaScript/TypeScript action 的不同做法：
  - `javascript-action-no-build` 使用原生 Node，依赖直接提交进仓库。
  - `javascript-action-with-build` 演示一个通常需要构建步骤的 Node action（以子模块方式引入）。
  - `typescript-action-with-build` 展示一个在执行前先编译的 TypeScript action。

## 容器 Action（Container Actions）
- **目录：** `container-actions`
- **Workflow：** [`.github/workflows/06-authoring-actions--05-container-actions.yaml`](../.github/workflows/06-authoring-actions--05-container-actions.yaml)
- **作用：** 运行三个 job，分别执行基于容器的 action：
  - `shell-dockerfile` 每次运行都根据本地 Dockerfile 构建一个基于 shell 的容器 action。
  - `shell-public-container-image` 复用一个预构建好的容器镜像，从而跳过构建步骤。
  - `python-dockerfile` 构建并运行一个由 Dockerfile 定义的 Python action，并打印问候语。
