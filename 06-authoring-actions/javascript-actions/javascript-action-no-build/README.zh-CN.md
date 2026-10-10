# JavaScript Action（无需构建）

> 🌐 **语言 / Language：** [English](./README.md) ｜ **简体中文**

官方文档建议把 `node_modules` 一并提交进仓库：https://docs.github.com/en/actions/sharing-automations/creating-actions/creating-a-javascript-action#commit-tag-and-push-your-action

另一种做法是使用：

- NCC https://github.com/vercel/ncc

或者

- Rollup https://github.com/actions/hello-world-javascript-action/blob/main/rollup.config.js

但这样会多出一个构建步骤。

这里有一个用 rollup 实现的模板仓库：https://github.com/actions/hello-world-javascript-action

说实话，你本来就该用 TypeScript…… 那就需要构建步骤（同时也省去了把 `node_modules` 提交进仓库的麻烦）。
