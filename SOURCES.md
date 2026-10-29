# 来源、许可与采样边界

## 固定来源

- 项目：Apache Airflow，`https://github.com/apache/airflow`
- 版本：`3.3.2`，发布页：<https://github.com/apache/airflow/releases/tag/3.3.2>
- 版本化标签解析出的源码提交：`aa19d2dbb9ed187ec01957a92848d9b005e9ba9d`
- 标签对象：`c6debda5cb5e34ad4ba67fe64ccd188a60020108`，指向上述提交；标签说明含发布签名材料，本轮未独立验证签名。
- 主仓库许可：Apache License 2.0，固定标签下的许可文件：<https://github.com/apache/airflow/blob/3.3.2/LICENSE>。Provider、插件和第三方依赖可能另有许可，不随本配方转授。
- GitHub 元数据快照（2026-10-29）：47,308 stars；仓库 `size` 字段为 790,962 KB。星数用于候选发现，不代表软件质量或配方覆盖程度。

## 选择理由

标准库已有多媒体、数据库、消息、家居、Agent、协作与 AI 工具，但缺少面向批处理数据管道的通用工作流调度器。Airflow 是 Apache-2.0、活跃且高星的代表项目，3.3.2 文档明确描述 DAG、任务、调度和执行器边界。高星的 n8n 使用 Sustainable Use License / fair-code，项目自己的许可说明也明确指出该许可不是 OSI 开源许可，因此不纳入本次“开源项目”候选。

## 查阅材料

- [Airflow 3.3.2 文档首页](https://airflow.apache.org/docs/apache-airflow/3.3.2/)
- [DAG 定义、发现、依赖和计划](https://airflow.apache.org/docs/apache-airflow/3.3.2/core-concepts/dags.html)
- [任务、状态、超时和重试](https://airflow.apache.org/docs/apache-airflow/3.3.2/core-concepts/tasks.html)
- [执行器模型](https://airflow.apache.org/docs/apache-airflow/3.3.2/core-concepts/executor/index.html)
- [XCom 任务间传值](https://airflow.apache.org/docs/apache-airflow/3.3.2/core-concepts/xcoms.html)
- [CLI 与环境变量参考](https://airflow.apache.org/docs/apache-airflow/3.3.2/cli-and-env-variables-ref.html)
- [公开 REST API 参考](https://airflow.apache.org/docs/apache-airflow/3.3.2/stable-rest-api-ref.html)
- [固定标签的 LICENSE](https://github.com/apache/airflow/blob/3.3.2/LICENSE)

## 采样范围与未核实项

本轮通过 GitHub API 核对仓库星数、仓库规模、发布标签、标签提交和许可标识；查阅固定版本的官方 DAG、任务、执行器、XCom、CLI 与 REST API 文档。没有克隆约 790 MB 的上游仓库，没有运行 Airflow 3.3.2，也没有检查所有源码、provider、测试、迁移、API 操作或部署矩阵。文档描述可作为固定版本的书面行为证据，不能替代源码全量审阅和运行验收。

尚未确认：实际 Python 版本矩阵与不同平台兼容性、所有 API 授权细节、数据库迁移与故障恢复边界、每个 Executor/provider 的具体行为、DAG bundle 的边界条件、UI 的完整操作和无障碍表现，以及所有 provider 与第三方组件的许可清单。重建时应以固定版本正式文档和可运行验收逐项补齐，不要从核心文档推断未覆盖的扩展行为。
