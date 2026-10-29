# Apache Airflow 软件配方（提取中）

```toml
format = "recipkg/1"

[package]
name = "airflow"
version = "0.1.0"
kind = "software"
description = "Apache Airflow 3.3.2 工作流编排核心的行为重建配方；上游运行与独立重建尚未验收。"
entry = "BUILD_PROMPT.md"

[dependencies.quality]
git = "https://github.com/recipkg/recipkg.git"
rev = "41e5b55c6612a9a5a10e499b5ace6a1a3fed0f2b"
subdir = "recipes/software-quality"

[dependencies.design]
git = "https://github.com/recipkg/design-foundations.git"
rev = "8c5bf1f1e40719789cf51bc0dfd8f5aeecae0538"
```

## 目标与边界

固定上游为 Apache Airflow `3.3.2`，提交 `aa19d2dbb9ed187ec01957a92848d9b005e9ba9d`。目标是重建可自托管的工作流编排核心：以 Python DAG 声明工作流，解析任务和依赖，由调度器按时间或事件创建运行，再通过执行器运行任务，并在 Web UI、CLI 与 REST API 中管理状态。行为覆盖、来源和未验证范围见 `SOURCES.md` 与 `COVERAGE.md`。

配方关注 DAG 与任务建模、任务依赖和触发规则、调度与手动触发、数据区间、运行状态、重试与超时、回填、任务间小型 XCom、连接与变量、执行器边界、日志、配置及核心管理 API。构建时保留 Airflow 3.x 的用户可见接口和核心数据模型；不要把单进程原型冒充成多组件部署行为。

`quality` 提供实现质量和可验证性合同；`design` 为 Web UI 提供交互、响应式和无障碍验收参考。它们都是构建提示词依赖，不是 Airflow 运行时服务。

Airflow 是由多个进程和外部组件组成的平台。Python 运行环境、元数据库、日志存储、时区数据库、密钥管理，以及 Celery、Kubernetes 等可选远程执行环境，均属于明确的外部运行前提。DAG 所依赖的 Python 包和外部系统也由部署方提供。配方不包含 Airflow 源码、provider 插件、数据库、凭据、日志或安装钩子。

## 不包含的内容

- 不承诺复刻全部 provider、云服务集成、社区插件、商业扩展或托管服务。
- 不把每种执行器、元数据库、密钥后端和日志后端都视为首版必需项；首版先定义稳定的接口，并以单机 LocalExecutor 验收核心工作流。
- 不把 XCom 当成大文件传输或任务间持久状态服务。
- 不要求像素级复制品牌界面；保留关键页面、交互、状态和权限语义，并按 `design` 合同验收。

缺失信息应继续标成未知，直到固定版本源码观察或实际运行能够裁决。验收条件列在 `ACCEPTANCE.md`；当前没有固定版本运行或独立重建结果。
