# 业务平台安卓应用更新

本仓库只公开发布 APK 和版本清单。应用源码保存在私有仓库。

手机端通过 GitHub API 读取 `app-update.json`，下载 Release 中的 APK，校验 SHA-256 后交给 Android 系统安装。
