# 业务平台安卓应用更新

本仓库公开发布 APK、安装版本清单和经过签名的网页功能包。应用源码与诊断日志保存在私有仓库。

从 1.6.0 起，App 启动或点击“同步功能”会读取 `features.json`，验证内置公钥对应的 RSA 签名后加载网页增强脚本和浮窗快捷功能。修改铃铛识别、网页表单辅助等功能时，可以发布新版功能包，手机无须重新安装 App。功能包的私钥只保存在开发机器上，不能上传到本仓库。原生 Android 代码或权限的变更仍需发布新版 APK。

1.7.0 新增原生消息首页。后台网页维持 OA 登录并尝试读取 `getPopList` 消息；详细业务流程仍可切换到网页。消息响应格式尚需在真实账号上验证，提取规则可由签名功能包更新。

1.8.0 增加通用原生页面渲染器。签名功能包中的 `nativeUi.screens` 可定义原生标签页、消息列表、提醒列表、文字和预设按钮，后续同类页面调整无需重新安装 APK。新增渲染器以外的系统能力仍需 APK 更新。

1.9.0 修复网页预填字段导致自动登录跳过的问题，并让原生提醒记录可点击打开同站流程链接；缺少链接时可以进入 OA 铃铛处理。

手机端通过 GitHub API 读取 `app-update.json`，下载 Release 中的 APK，校验 SHA-256 后交给 Android 系统安装。

发布新的 Android 版本时，先用原签名密钥构建 APK 并创建新的 GitHub Release，取得 APK 资源 ID。随后增加 `app-update.json` 的 `versionCode`，填写版本名、`https://api.github.com/repos/MsMoucao/business-portal-android-updates/releases/assets/资源ID` 和 APK 的 SHA-256，最后推送到 `main`。应用启动时会检查更新，也可手动点击“检查应用版本”。
