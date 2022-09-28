### Compose 布局



#### 	1、Compose中布局的目标

​		1、实现高性能

​		2、让开发者能够轻松编写自定义布局

​		3、在Compose中，通过避免多次测量布局子级可实现高性能。如果需要进行多次测量，Compose具有一个特殊系统，即固有特性测量



#### 	2、标准布局组件

​		1、使用Column可将多个项垂直地放置在屏幕上

​		2、使用Row可将多个项水平地放置在屏幕上

​		3、使用Box可将一个元素放在另一个元素上



#### 	3、修饰符

​	修饰符的作用类似于基于试图的布局中的布局参数，借助修饰符，可以修饰或扩充可组合项。我们可以使用修饰符来执行以下操作

​		1、更改可组合项的大小、布局、行为和外观

​		2、添加信息，如无障碍标签

​		3、处理用户输入

​		4、添加高级互动，如使元素可点击、可滚动、可拖动或可缩放



#### 	4、Slots API

​	Material 组件大量使用槽位API，这是Compose引入的一种模式，它在可组合项之上带来一层自定义设置。这种方法使组件变得更加灵活，因为它们接受可以自行配置的子元素，而不必公开子元素的每个配置参数。槽位会在界面中留出空白区域，让开发者按照自己的意愿来填充



#### 	5、Scaffold 脚手架

​	Scaffold可让我们实现具有基本Material Design布局结构的界面。Scaffold可以为最常见的顶级Material组件（如TopAppBar、BottomAppBar、FloatingActionButton和Drawer）提供槽位。通过使用Scaffold，可轻松确保这些组件得到适当放置且正确地协同工作

![image-20220926203337912](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220926203337912.png)



#### 	6、使用列表

​	如果我们知道用例不需要任何滚动，可以使用简单的Column或Row

​	如果您需要显示大量列表项（或长度未知的列表），可以使用LazyCoolumn或LazyRow

![image_20220927081636](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image_20220927081636.png)

![image-20220927085604817](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927085604817.png)



#### 7、自定义布局

​	在Compose中，界面元素由可组合函数表示，此类函数在被调用后会发出一部分界面，这部分界面随后会被添加到呈现在屏幕上的界面树中。每个界面元素都有一个父元素，还可能有多个子元素。此外，每个元素在其父元素中都有一个位置，指定为（x,y）位置；也都有一个尺寸，指定为width和height

​	

##### 	1、使用布局修饰符

​	可以使用layout修饰符来修改元素的测量和布局方式。Layout使一个lambda；它的参数包括您可以测量的元素（以measurable的形式传递）以及该可组合项的传入约束条件（以constraints的形式传递）



##### 	2、firstBaselineToTop

![image-20220927094324957](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927094324957.png)

![image-20220927094315540](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927094315540.png)



##### 	3、仿Column布局——MyOwnColumn

​	![image-20220927095725383](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927095725383.png)



##### 4、StaggeredGrid瀑布流



##### 5、约束布局

​	在实现对齐要求比较复杂的较大布局时，ConstraintLayout很有用

###### 	1、引用：使用createRefs()或createRefFor()创建的，ConstraintLayout中的每个可组合项都需要有与之关联的引用

###### 	2、约束条件：是使用constrainAs()修饰符提供的，该修饰符将引用作为参数，可以让您在主体lambda中指定其约束条件

###### 	3、约束条件是使用linkTo()或其他有用的方法指定的

###### 	4、parent是一个现有的引用，可用于指定对ConstraintLayout可组合项本身的约束条件

![image-20220927150538919](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927150538919.png)



##### 8、解耦API

​	说白：就是将配置部分单独出来 以参数的形式传递进去修改

![image-20220927151828100](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927151828100.png)



##### 9、Intrinsics

###### 	1、Compose只测量子元素一次，测量两次会发生运行时异常。但是，有时在测量子元素之前，我们需要一些有关子元素的信息

###### 	2、Intrinsics允许您在实际测量之前查询子项

​		(min|max)IntrinsicWidth：鉴于此高度，您可以正确绘制内容的最小/最大宽度是多少

​		(min|max)IntrinsicHeight：鉴于此宽度，您可以正确绘制内容的最小/最大高度是多少

![image-20220927153621046](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220927153621046.png)