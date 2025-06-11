[返回](./Runtime-READNE.md)

# /Convention/Runtime/Config

---

包含了关于静态的配置信息等内容, 并且引入全体标准库内容

## Import All

检查并尝试引入所有依赖库

## 静态配置

若不存在相应配置, 则需要定义

- `CURRENT_COM_NAME`    公司/组织名称
- `CURRENT_APP_NAME`    应用名称
- `__PLATFORM_NAME`     平台名称
- `__PLATFORM_VERSION`  平台版本
- `PLATFORM_EXTENSION`  扩展说明的内容

## PlatformIndicator包含的内容

- `IsRelease` Debug/Release状态
- 平台判断
    - `IsPlatformWindows`
    - `IsPlatformLinux`
    - `IsPlatformUnix`
    - `IsPlatformApple`
    - `IsPlatformAndroid`
    - `IsPlatformPosix`
- 平台架构判断
    - `IsPlatformx64`
- 编译器/解释器判断 如`IsMSVC`等
- `KeyboardInput` 获取非阻塞输入
- `ApplicationPath` 获取当前应用程序目录
- `StreamingAssetsPath` 获取StreamingAssets目录
- `PersistentPath` 获取持久化目录

## 静态类 <Type>Indicator

包含对应类型常用的工具函数

## 静态类 DescriptiveIndicator

包含一个`描述`字符串, 可选一个`值`对象

## 其他基础内容

用于对齐不同语言间基本实现的颗粒度, 如以下内容

- 程序标记语言
- 类型转换
- 字符串操作
- Construct/Destruct 重构造/析构
- 命令行解析
- 简单的反射内容
- 元类型
