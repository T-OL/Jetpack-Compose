## Jetpack Compose



### 1、Compose是什么



#### 	JetPack Compose 是用于构建原生Android界面的新工具包。它可简化并加快Android上的界面开发，帮助您使用更少的代码、强大的工具和直观的Kotlin API，快速打造生动而精彩的应用。



### 2、Compose的优势



#### 	更少的代码：

##### 			使用更少的代码实现更多的功能，并且可以避免各种Bug，从而使代码简洁且易于维护

#### 	直观：

##### 			您只需描述界面，Compose会负责处理剩余的共做。应用状态变化时，界面会自动更新。

#### 	加快应用开发：

##### 			兼容现有的所有代码，方便您随时随地地采用。借助实时预览和全面的Android Studio支持，实现快速迭代。

#### 	功能强大：

##### 			凭借对Android平台API的直接访问和对于Metrial Design、深色主题、动画等的内置支持，创建精美的应用。



### 3、可组合函数



#### 		JetPack Compose是围绕可组合函数构建的。这些函数可以让您以程序化方式定义应用的界面，只需描述应用界面的外观并提供数据依赖项，而不必关注界面的构建过程（初始化元素，将其附加到父项等）。如需创建可组合函数，只需将@Composable注解添加到函数名称中即可



### 4、Compose所解决的问题

##### 在编写可维护的软件时，我们的目标是最大程度地减少耦合并增加内聚

##### 尽可能的将相关的代码组织在一起，以便我们可以轻松地维护它们，并方便我们随着应用规模的增长而扩展我们的代码，这个称之为关注点分离



### 5、挂起函数suspend

##### 挂起函数必须在另一个挂起函数中调用，或者在协中调用
