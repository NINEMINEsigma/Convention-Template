[返回](./Runtime-READNE.md)

# /Convention/Runtime/Internal

---

包含了关于本框架下内置的接口

## Import Config

导入[Config](Config.md)

## TypeClass元类型

完全公开的对外接口

- 成员函数

    - ToString 转字符串类型

    ```cpp
    string ToString() const
    ```

    - SymbolName 获取类型符号

    ```cpp
    string SymbolName() const noexcept
    ```

    - GetType() 获取类型

    ```cpp
    Type GetType() const noexcept
    ```

    - As() 安全的类型转换

    ```cpp
    template<typename Ty>
    [[ReturnMaynull]]
    conditional_t<is_reference_v<Ty>,Ty,Ty*> As()
    [[ReturnMaynull]] TypeClass* As(const type_info&)
    ```

