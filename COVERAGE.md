# 覆盖状态

当前阶段：**提取中**。本仓库保存 Apache Airflow 3.3.2 核心行为的重建合同；未运行上游、未重建软件，不能据此声称 Airflow 已复刻或可替代。

## 配方当前描述

| 能力 | 当前材料 | 证据状态 |
| --- | --- | --- |
| DAG、任务、任务依赖与文件发现 | `RECIPE.md`、`BUILD_PROMPT.md` | 固定版本官方文档观察；源码细节未核查 |
| 计划触发、手动运行、logical date/data interval | `BUILD_PROMPT.md`、`ACCEPTANCE.md` | 部分文档观察；运行语义待验收 |
| Task Instance 状态、跳过、失败传播、重试、超时 | `BUILD_PROMPT.md`、`ACCEPTANCE.md` | 官方任务文档观察；真实运行未验证 |
| XCom 与小型任务结果 | `BUILD_PROMPT.md`、`ACCEPTANCE.md` | 官方 XCom 文档观察；后端和重试行为未运行验证 |
| CLI、REST API、UI、Connections、Variables | `BUILD_PROMPT.md`、`ACCEPTANCE.md` | 文档范围抽样；权限和字段行为未验证 |
| Scheduler、元数据库、Executor、日志与持久化 | `RECIPE.md`、`BUILD_PROMPT.md` | 架构合同；固定版本实测未做 |
| Celery、Kubernetes、Edge 及社区 provider | `RECIPE.md`、`ACCEPTANCE.md` | 明确列为扩展边界，未提取完整行为 |

## 证据分层

- 固定版本身份：上游 `3.3.2`，提交 `aa19d2dbb9ed187ec01957a92848d9b005e9ba9d`；详见 `SOURCES.md`。
- 文档观察：DAG、task 状态、执行器、XCom 和 CLI 文档。
- 上游二进制或源码实测：无。
- 依本配方独立重建：无。
- `ACCEPTANCE.md` 中的运行时验收：待执行。
- 递归依赖提示词结构和包归档检查：待执行。

提取只覆盖明确列出的核心工作流，不代表 3.3.2 的完整功能规格。遇到未观察行为时先记为未知，再固定条件运行或查阅对应源码与正式文档。
