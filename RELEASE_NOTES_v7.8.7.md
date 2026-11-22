## **v7.8.7 更新日志**

> **提示：** 本次更新无破坏性变更，可直接覆盖安装。

#### 修复：Zero Trust 访问策略 Geo 规则崩溃

- 修复访问策略 / 访问组编辑弹窗中展示 Geo（国家/地区）规则时应用崩溃的问题（ClassCastException: String cannot be cast to List）
- Geo 规则的 country_code 同时兼容单个国家代码字符串与字符串数组两种返回格式，统一规整为列表后再展示与回写，避免因接口数据格式不一致导致异常

#### 优化：网络安全配置适配 Android 17

- 调整网络安全配置，关闭 Android 17（targetSdk 37）默认启用的证书透明度（CT）校验并信任系统 CA，解决抓包工具本地签发的 MITM 证书缺少 SCT 记录而无法被信任的问题
- debug 构建额外信任用户 CA，release 构建仍仅信任系统 CA，安全策略仅在调试环境放开
- 同步整理 AndroidManifest 与网络安全配置文件的属性排版，行为保持不变

本次更新修复了 Zero Trust Geo 规则导致的崩溃，并调整网络安全配置以适配 Android 17 的证书校验机制
