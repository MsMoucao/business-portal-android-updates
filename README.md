# 业务平台安卓应用更新

本仓库只公开发布 APK 和版本清单。应用源码保存在私有仓库。

手机端通过 GitHub API 读取 `app-update.json`，下载 Release 中的 APK，校验 SHA-256 后交给 Android 系统安装。

发布新版本时，先用原签名密钥构建 APK 并创建新的 GitHub Release，取得 APK 资源 ID。随后增加 `app-update.json` 的 `versionCode`，填写版本名、`https://api.github.com/repos/MsMoucao/business-portal-android-updates/releases/assets/资源ID` 和 APK 的 SHA-256，最后推送到 `main`。应用启动时会检查更新，也可手动点击“检查更新”。
