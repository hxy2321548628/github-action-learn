# 中英术语对照表 & 阅读指南

> 🌐 **语言 / Language：** [English](./README.md) ｜ **简体中文**

本课程原文是英文，而 GitHub Actions 的许多术语在中文社区存在多种译法。为了避免歧义，本中文版统一采用下表的译法。

## 📐 翻译约定

阅读本中文版时，请记住下面 4 条规则：

1. **技术术语首次出现时写作「中文（English）」**，之后直接用中文，例如「可复用工作流」。
2. **YAML 的键名（key）一律不翻译**，例如 `on:`、`runs-on:`、`needs:`、`strategy:`、`permissions:`。
3. **命令、action 名称、镜像名、URL、代码标识符一律保留英文原文**，例如 `actions/checkout`、`ubuntu-24.04`、`GITHUB_TOKEN`、`workflow_dispatch`。
4. **一部分术语刻意不翻译**，因为直译反而会造成误解，详见「刻意保留英文的术语」一节。

---

## 1. 核心概念

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| Workflow | 工作流 | `.github/workflows/` 下的一个 YAML 文件，是最外层的自动化单元 |
| Job | 作业（job） | 一个 workflow 由一个或多个 job 组成；默认并行运行 |
| Step | 步骤（step） | job 内的最小执行单元，按顺序执行 |
| Action | action（不译） | 可复用的自动化单元，是 step 的一种类型（`uses:`） |
| Runner | 运行器 | 真正执行 job 的机器／容器 |
| Event | 事件 | 触发 workflow 的外部动作，例如 push、pull_request |
| Trigger | 触发器 | 决定 workflow 何时运行的配置（`on:`） |
| Expression | 表达式 | `${{ }}` 包裹的求值语法 |
| Context | 上下文 | 表达式中可访问的对象，如 `github`、`env`、`needs`、`matrix` |
| Step / Job output | 步骤输出／作业输出 | 用 `GITHUB_OUTPUT` 与 `outputs:` 向后续步骤／作业传值 |

## 2. 触发与执行控制

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| `workflow_dispatch` | 手动触发 | 在 Actions 页面手动运行 |
| `workflow_call` | 被调用触发 | 让该 workflow 成为可复用工作流 |
| `schedule` / cron | 定时触发 | 用 cron 表达式按计划运行 |
| Path filter | 路径过滤器 | 只在指定路径的文件变更时触发 |
| Branch filter | 分支过滤器 | 只在指定分支上触发 |
| Concurrency | 并发控制 | `concurrency:`，限制同一组 workflow 同时运行 |
| `cancel-in-progress` | 取消进行中的运行 | 有新运行时取消旧的运行 |
| Conditional / `if:` | 条件判断 | 决定 job 或 step 是否执行 |
| Matrix | 矩阵 | `strategy.matrix`，用参数组合批量生成 job |
| `fail-fast` | 快速失败 | 矩阵中任一 job 失败时是否取消其余 job |
| Dynamic matrix | 动态矩阵 | 运行时用 `fromJSON()` 动态生成矩阵 |
| DAG | 有向无环图 | job 之间通过 `needs:` 形成的依赖关系图 |

## 3. 数据、配置与上下文

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| Environment variable | 环境变量 | `env:`，分 workflow / job / step 三个作用域 |
| Scope | 作用域 | 变量或权限的生效范围 |
| Secret | 密钥（secret） | 加密存储的敏感值，日志中会被自动打码 |
| Variable | 变量（variable） | 非敏感的配置值，通过 `vars.` 访问 |
| Repository-level | 仓库级 | 在整个仓库范围内生效 |
| Environment-level | 环境级 | 只在指定 GitHub Environment 中生效 |
| Environment | 环境（environment） | 带保护规则（审批、等待、分支限制）的部署目标 |
| Input | 输入参数 | 可复用工作流或手动触发接受的外部参数 |
| `GITHUB_ENV` | 环境文件 | 写入后成为后续步骤可见的环境变量 |
| `GITHUB_OUTPUT` | 输出文件 | 写入后成为该步骤的 output |
| `GITHUB_PATH` | 路径文件 | 写入后追加到后续步骤的 `PATH` |
| `GITHUB_STEP_SUMMARY` | 步骤摘要 | 写入后显示在 run 摘要页面（支持 Markdown） |
| Checkout | 检出代码 | 用 `actions/checkout` 把仓库拉到运行器上 |

## 4. 制品与缓存

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| Artifact | 制品 | job 之间传递文件，或用 `actions/upload-artifact` 长期保存 |
| Cache | 缓存 | 复用依赖、编译产物，加速后续运行 |
| Cache key | 缓存键 | 决定缓存是否命中的标识，通常包含 lock 文件哈希 |
| Cache hit / miss | 缓存命中／未命中 | `cache-hit` 输出为 `'true'` 表示命中 |
| `cache-dependency-path` | 缓存依赖路径 | 指定用于计算缓存键的 lock 文件路径 |
| Restore / Save | 恢复／保存 | `actions/cache` 的两个阶段 |
| Lock file | 锁定文件 | 如 `package-lock.json`，用于精确还原依赖版本 |

## 5. 权限与安全

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| Permissions | 权限 | `permissions:`，控制 `GITHUB_TOKEN` 的能力 |
| `GITHUB_TOKEN` | （保留英文） | GitHub 自动注入的临时令牌 |
| Least privilege | 最小权限原则 | 只授予完成任务所必需的权限 |
| Read-only / read-write | 只读／读写 | 权限的两个基本级别 |
| Pin (to a commit SHA) | 固定（到 commit SHA） | 用完整哈希引用 action，防止版本被替换 |
| Supply chain attack | 供应链攻击 | 通过被篡改的第三方依赖／action 入侵 |
| Self-hosted runner | 自托管运行器 | 跑在自己基础设施上的运行器 |
| Fork PR | 来自 fork 的 PR | 外部贡献者的 pull request，需特别防范 |
| Protected environment | 受保护环境 | 需要人工审批才能部署的环境 |
| `required_reviewers` | 必需审批人 | 环境保护规则之一 |
| Mask / Masking | 打码 | 日志中把敏感值显示为 `***` |

## 6. 认证

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| OIDC (OpenID Connect) | OIDC（保留英文） | 运行时换取短期云凭据的标准协议 |
| Short-lived credentials | 短期凭据 | 由 OIDC 换取的临时凭据，无需长期存储 |
| Static credentials | 静态凭据 | 长期不变的 Access Key / Secret，应避免使用 |
| Assume role | 扮演角色 | `role-to-assume`，OIDC 认证到 AWS 的关键配置 |
| `id-token: write` | （保留英文） | 申请 OIDC JWT 所必需的权限 |
| Third-party authentication | 第三方认证 | 认证到 AWS、Azure、GCP 等外部平台 |

## 7. 运行器类型

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| GitHub-hosted runner | GitHub 托管运行器 | 由 GitHub 提供，跑在 Azure 上，按分钟计费 |
| Third-party hosted runner | 第三方托管运行器 | 如 namespace.so，通常更快更便宜 |
| Self-hosted runner | 自托管运行器 | 成本低但运维开销大 |
| Container job | 容器作业 | 用 `container:` 在指定镜像中执行 job |
| Prebuilt image | 预构建镜像 | 直接复用镜像，跳过构建步骤 |

## 8. 编写 Action

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| Composite action | 复合 Action | 用 `using: composite` 把多个 step 打包成一个 action |
| Reusable workflow | 可复用工作流 | 用 `workflow_call` 让其他 workflow 调用 |
| JavaScript action | JavaScript Action | `using: node20`，用 JS/TS 编写 |
| Container action | 容器 Action | `using: docker`，在容器中运行 |
| `secrets: inherit` | 继承密钥 | 把所有调用方密钥传递给被调工作流 |
| Relative path reference | 相对路径引用 | 如 `./.github/workflows/x.yaml` |
| Commit reference | commit 引用 | 如 `owner/repo/.github/workflows/x.yaml@<sha>` |

## 9. 开发者体验

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| `act` | （保留英文） | 在本地容器中运行 GHA workflow 的工具 |
| Breakpoint | 断点 | 失败时通过 SSH 连进运行器排查问题 |
| Debug logging | 调试日志 | 用 `ACTIONS_STEP_DEBUG` / `ACTIONS_RUNNER_DEBUG` 开启 |
| Workflow command | 工作流命令 | `::error::`、`::warning::`、`::group::` 等特殊指令 |
| Annotation | 注解 | 显示在 PR 或运行页面上的错误／警告标记 |
| Log group | 日志分组 | `::group::` / `::endgroup::` |
| Dry-run | 干跑 | 不真正执行，只验证流程 |
| Feedback loop | 反馈回路 | 从改动到获得结果的时间 |

## 10. 性能与部署

| 英文 | 本中文版译法 | 说明 |
| --- | --- | --- |
| Baseline | 基线 | 优化前先测量得到的性能参照值 |
| Queue time | 排队时间 | job 等待运行器分配的时间 |
| Cache hit rate | 缓存命中率 | 命中缓存的运行占比 |
| Long-tail job | 长尾作业 | 少数耗时特别长的 job |
| Fail fast | 快速失败 | 尽早拒绝有问题的改动 |
| Parallelize | 并行化 | 拆分矩阵以利用更多 CPU 核心 |
| Emulation | 模拟执行 | 如 QEMU，性能远低于原生架构 |
| Quality gate | 质量门禁 | 不达标就不允许合并／发布的检查 |
| Push based / Pull based (GitOps) | 推送式／拉取式 | 两种部署模型 |
| Stale issues/PRs | 陈旧的 issue/PR | 长期无活动、可自动关闭的条目 |

---

## ⚠️ 刻意保留英文的术语

以下术语如果直译，反而会让人看不懂或产生误解，因此本中文版**保留英文原文**：

| 术语 | 为什么不翻译 |
| --- | --- |
| **action** | 「动作」「操作」都无法体现它在 GHA 中是一个可复用软件包的含义；社区普遍直接说 action |
| **workflow / job / step** | 首次出现时会标注中文，但在 YAML 语境中直接保留英文更贴近实际操作 |
| **runner** | 直译「跑步者」毫无意义；本中文版用「运行器」，也会直接写 runner |
| **OIDC** | 协议名称，保留原文 |
| **GitHub 专有名词** | `GITHUB_TOKEN`、`workflow_dispatch`、`pull_request` 等属于配置标识符，改写会导致无法复制粘贴 |
| **Marketplace / orb** | 产品／生态专有名称 |

---

## 🧭 建议的学习路径

1. **[01 历史与动机](./01-history-and-motivation/README.zh-CN.md)** —— 先建立「为什么需要 CI」的直觉。
2. **[02 为什么选择 GitHub Actions](./02-why-github-actions/README.zh-CN.md)** —— 了解它在 CI 工具生态中的位置。
3. **[03 核心功能](./03-core-features/README.zh-CN.md)** —— **重点**。把 7 个 workflow 逐个在本地跑一遍（用 `act`）。
4. **[04 高级功能](./04-advanced-features/README.zh-CN.md)** —— **重点**。权限、缓存、矩阵、OIDC 是实际工作中最常用的部分。
5. **[05 Marketplace Actions](./05-marketplace-actions/README.zh-CN.md)** —— 学会安全地挑选第三方 action。
6. **[06 编写 Action](./06-authoring-actions/README.zh-CN.md)** —— 从「用 action」进阶到「写 action」。
7. **[07 常见工作流](./07-common-workflows/README.zh-CN.md)** —— 把前面所学串成一条完整的 CI/CD 流水线。
8. **[08 开发者体验](./08-developer-experience/README.zh-CN.md)** —— 学会在本地高效迭代，而不是反复 push 试错。
9. **[09 最佳实践](./09-best-practices/README.zh-CN.md)** —— 收尾时对照检查自己的流水线。
10. **Capstone 结课项目** —— 见课程大纲；本仓库中 `capstone/` 是一个空的 git 子模块占位目录。

> 💡 **学习建议：** 每个模块目录下的 `README.zh-CN.md` 会列出对应的 workflow 文件。建议**中英对照**阅读 —— 中文版帮你快速理解意图，英文原版帮你熟悉将来在工作和官方文档中必然会遇到的真实术语。
