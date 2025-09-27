[返回](./Runtime-README.md)

# /Convention/Runtime/Architecture

---

核心架构模块，提供依赖注入、事件系统和时间线管理功能

## 接口定义

系统定义了以下核心接口来规范架构设计：

### ISignal
信号接口，用于事件系统的消息传递

### IModel
模型类接口, 仅作为接口倒置

### IConvertable<T>
转换接口，提供类型转换能力：
- `T ConvertTo()` 转换为目标类型

### IConvertModel<T>
组合接口，同时继承 `IModel` 和 `IConvertable<T>`

## 核心类型

### SingletonModel<T>
泛型单例模型，提供类型安全的单例管理：
- 支持依赖注入和实例替换
- 提供隐式转换操作符
- 集成模型序列化功能

### DependenceModel
依赖模型，管理多个条件的组合验证：
- 支持多个 `IConvertModel<bool>` 的依赖关系
- 提供枚举接口遍历所有依赖
- 所有依赖条件均满足时返回true

## 注册系统

### 对象注册相关

向slot槽注册实例target, 并设置依赖dependences, 当槽的所有依赖的槽都注册完成后触发completer
- `void Register(Type slot, object target, Action completer, Type[] dependences) throw(InvalidOperation)`

解除slot槽中的注册
- `bool Unregister(Type slot) noexcpect`

### 注册查询
- `bool Contains(Type slot)`
- `bool Get(Type slot)`

## 事件系统

### 消息监听

Listening类, 拥有停止监听的函数`StopListening()`
- `class Listening`

向指定的槽slot中添加监听信号Signal的监听器listener
- `Listening AddListener<Signal>(Type slot, Action<Signal> listener) where Signal : ISignal`

向指定的槽slot发送信号signal
- `void SendMessage(Type slot, ISignal signal)`

向所有槽广播信号signal
- `void SendMessage<Signal>(Signal signal)`

## 时间线系统

### 时间线管理
- `CreateTimeline()` 创建新的时间线
- `AddStep(int timelineId, Func<bool> predicate, params Action[] actions)` 添加步骤
- `UpdateTimeline()` 更新所有时间线
- `ResetTimelineContext(int timelineId)` 重置时间线上下文

提供基于条件的任务调度：
- 支持多条时间线并行执行
- 基于谓词的条件触发
- 支持动态添加执行步骤

## 类型格式化

### 类型序列化
- `FormatType(Type type)` 格式化类型为字符串
- `LoadFromFormat(string data)` 从字符串加载类型
- `LoadFromFormat(string data, out Exception exception)` 安全加载类型

使用格式：`Assembly::FullTypeName`

## 内部管理

### 系统重置
- `InternalReset()` 重置所有内部状态

清理以下组件：
- 注册历史
- 未完成的目标
- 完成器回调
- 依赖关系
- 子对象容器
- 事件监听器
- 时间线队列
