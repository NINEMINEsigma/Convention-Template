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
- `PlatformInfomation` 平台相关的发布信息

## 多个静态类 <Type>Indicator

包含对应类型常用的工具函数

## 静态类 DescriptiveIndicator

包含一个`描述`字符串, 可选一个`值`对象

## 其他基础内容

用于对齐不同语言间基本实现的颗粒度, 如以下内容

- 程序标记语言
    - 函数形参
        - `In` 预状态必须有效
        - `Out` 后状态必须有效
        - `InOpt` 若不为空则预状态必须有效
        - `OutOpt` 若不为空则后状态必须有效
        - `Read(s)` 以其为首能够读取s指定的元素数量
        - `ReadByte(s)` 以其为首能够读取s指定的字节数量
        - `Write(s)` 以其为首能够写入s指定的元素数量
        - `WriteByte(s)` 以其为首能够写入s指定的字节数量
        - `FormatString` 作为格式字符串
    - 函数返回值
        - `Success(exp)` 表达式为真时函数成功
        - `CheckReturn` 调用方应检查返回值
    - 函数
        - `AcquiresLock(exp)` 会将exp命名的锁对象加锁
        - `ReleaseLock(exp)` 会将exp命名的锁对象解锁
        - `Param(n)` 获取由n指定的顺序已命名形参的名称
    - 结构字段
        - `FieldSize(s)` 具有由s指定的可写大小数量元素
        - `FieldSizeByte(s)` 具有由s指定的可写大小数量字节
    - 结构
        - `StructSizeByte(s)` 该结构的有效对象具有s指定的字节数量
    - 通用
        - `When系列` 检定并控制标记是否生效或函数是否成功
        - `Range系列` 指定数量级或输入区间
        - `Current` 当前标记中的对象的同义词

- 类型转换
- 字符串操作
- Construct/Destruct 重构造/析构
- 命令行解析
- 简单的反射内容
- 元类型
- ...
