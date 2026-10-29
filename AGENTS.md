# Airflow 配方维护说明

- 阅读 `RECIPE.md`、`BUILD_PROMPT.md`、`ACCEPTANCE.md`、`SOURCES.md`、`COVERAGE.md` 和完整递归依赖后再修改。
- 本配方固定 Apache Airflow 3.3.2 提交。升级来源时先复查发布、完整提交、许可、接口变化和验收；不得把分支 HEAD 当固定版本。
- 只提交 UTF-8 Markdown 配方材料。不要把 Airflow 源码、可执行文件、provider 包、脚本、数据库、密钥、日志、构建产物或安装钩子放进归档。
- 维护 `SOURCES.md` 的采样范围和许可，维护 `COVERAGE.md` 的证据分层。文档阅读、归档检查、上游运行与独立重建是不同证据。
- 修改依赖时固定完整 Git 提交；逐项检查别名、依赖用途、递归材料和 `LOCK.md` 中生成的摘要。只在对应内容发生变化时更新包版本。
- 将 UI 行为与 `design` 依赖对应，将代码质量合同与 `quality` 对应；不要把这些配方依赖描述成 Airflow 的运行时服务。
- 不降低既有验收范围来把未通过项目标记为完成。记录失败、未执行和未知项。
