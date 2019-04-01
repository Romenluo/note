
### vue简单介绍和MVVM模式

-----

1. vue简单小巧的核心，渐进式技术栈，足以应付任何规模的应用。渐进式就是可以一步一步，有阶段性的来使用vue.js不必一开始就使用所有的东西。
2. mvvm模式（Model-View-ViewModel）,由mvc衍生而来。有三层，分别是View，Model，ViewModel。其中View层代表的是视图、模版，
负责将数据模型转化为UI展现出来。Model层代表的是模型、数据，可以在Model层中定义数据修改和操作的业务逻辑。ViewModel层连接Model和View。
View和Model并没有直接的联系，通过ViewModel进行交互。ViewModel层通过双向数据绑定将View层和Model层连接了起来，使得View层和Model层的同步工作完全是自动的。
如图所示
![mvvm构架图](../images/vue/mvvm.png)
