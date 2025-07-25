[返回](./Runtime-README.md)

# /Convention/Runtime/Asynchrony

异步表达式系统，允许对象字段进行延迟初始化和访问，实现将有序调用转换为无序调用的方法

---


## 核心组件

### Asynchronous 基类
异步对象的基类，提供字段级别的异步访问能力。

### AsynchronyExpression 异步表达式
封装单个字段的异步访问逻辑。

**参数：**
- `field`: 字段信息
- `value`: 初始值（默认为未初始化状态）
- `time_wait`: 等待间隔（默认0.1秒）
- `timeout`: 超时时间（默认0秒，表示无超时）
- `callback`: 初始化回调函数

**方法：**
- `get_value()`: 异步获取字段值
- `set_value()`: 设置字段值
- `set_uninitialized()`: 重置为未初始化状态

### AsyncContextDetector 上下文检测器
检测当前运行环境是否为异步上下文。

**静态方法：**
- `is_in_async_context()`: 检查是否在异步上下文中
- `get_current_loop()`: 获取当前事件循环
- `ensure_async_context_safe()`: 确保操作在异步上下文中安全
