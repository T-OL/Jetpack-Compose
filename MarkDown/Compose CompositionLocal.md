### Compose CompositionLocal



#### 1、显式传参与隐式传参	![image-20220929105214827](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929105214827.png)

##### 	比较：

![image-20220929105940687](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929105940687.png)

#### CompositionLocal

##### 	1、通常情况下，在Compose中，数据以参数形式向下流经整个界面树传递给每个可组合函数。但是，对于广泛使用的常用数据（如颜色或类型样式），这可能会很麻烦。

##### 	2、为了支持无需将颜色作为显示参数依赖项传递给大多数可组合项，Compose提供了CompositionLocal，可让您创建以树为作用域的具名对象，这可以用作让数据流经过界面树的一种隐式方式

##### 	3、我们可以通过MaterialTheme的colors、shapes和typography属性访问的LocalColors、LocalShapes和LocalTypography属性

![image-20220929110859779](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929110859779.png)

##### 	4、如需为CompositionLocal提供新值，请使用CompositionLocalProvider及其provides infix函数

##### 	5、CompositionLocal的current值对应于该组合部分中的某个祖先提供的最接近的值



#### 创建CompositionLocal

​	效果图和结构树

![image-20220929150944641](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929150944641.png)

![image-20220929152640218](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929152640218.png)

![image-20220929152815905](C:\Users\Ywhuii\AppData\Roaming\Typora\typora-user-images\image-20220929152815905.png)



##### 	1、通过compositionLocalOf创建来获取CompositionLocal对象

###### 		1、如果更改提供的值，会使读取其current值的组件发生重组

##### 	2、通过staticCompositionLocalOf创建来获取CompositionLocal对象

###### 		1、与compositionLocalOf不同，更改值会导致提供CompositionLocal的整个content lambda被重组，而不仅仅是在组合中读取current值的组件（所有用到的组件都会重组）

###### 		2、如果为CompositionLocal提供的值发生更改的可能性微乎其微或永远不会改变，使用staticCompositionLocalOf可提高性能