# 析构过程

析构器会在类的实例销毁之前被立即调用，使用 `deinit` 关键字来标示析构器。仅适用于`class`类型.

## 析构器是如何工作的

当不再需要某一个实例时，Swift 会自动销毁该实例，以释放资源。
Swift 通过 自动引用计数（ ARC ）来管理实例内存。
通常在实例释放时，你无需行手执动清理。
但是，当你在使用自己的资源时，可能需要自己执行一些额外的清理。例如，如果你创建了一个自定义类以打开文件并向其写入一些数据，则可能需要在销毁类实例之前关闭该文件。
在类中， 只能有一个析构器。

```
deinit {
    //执行析构器
}
```

在实例销毁之前，会自动调用析构器。你不能自己调用析构器。父类的析构器由其子类继承，父类析构器会在子类析构器实现的末尾自动调用。即使子类不提供自己的析构器，父类析构器也会被调用。

因为实例在调用析构器之后才会被释放，所以析构器可以访问调用它的实例的所有属性，并可以根据这些属性修改其行为（例如查找需要关闭的文件的名称） ）。
