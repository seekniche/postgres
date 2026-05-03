# PostgreSQL Agent 说明书

本仓库是用于学习 PostgreSQL 18.3 的本地源码目录。Codex、OpenCode 等 AI
coding agent 在协助阅读、修改、编译和测试代码时，应遵循本文档中的本地项目约定。

## 构建与安装目录

- 构建目录固定使用仓库根目录下的 `tmp_build`。
- 安装目录固定使用仓库根目录下的 `output`。
- 不要把构建产物或安装产物写入源码目录中的其他位置。
- 每次执行编译命令时，都要统计并记录耗时，优先使用 `time`。
- 编译时优先使用并行构建，例如 `make -j$(sysctl -n hw.ncpu)`。
- 本地默认不启用 ICU，配置时使用 `--without-icu`。

构建示例：

```sh
cd /Users/garfieldbc/proj/postgres
mkdir -p tmp_build
cd tmp_build
../configure --prefix="/Users/garfieldbc/proj/postgres/output" --without-icu
time make -j$(sysctl -n hw.ncpu)
make install
```
