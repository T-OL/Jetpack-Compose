### Compose 主题



#### 	1、Material Design

##### 		Material Design是一个用于创建数字界面的综合设计体系，Material Design组件（按钮、卡片、开关等）建立在Material Theming之上，Material theme包括颜色、排版和形状属性



#### 	2、定义主题

##### 		1、创建主题

##### 		2、颜色

##### 		3、排版

##### 		4、形状

##### 		5、深色主题



#### 	3、使用颜色

##### 			1、我们已经掌握了如何创建自己的主题，来为我们的应用设置颜色、字体样式和形状，所有Material组件开箱即可使用这些自定义功能。例如，FloatingActionButton可组合项中，默认使用主题中的secondary颜色，但是，有时候我们并不想使用默认设置

![image-20220929192223303](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929192223303.png)

##### 	2、原色：Compose提供了一个Color类，在静态声明颜色定义时，请务必小心，因为这些定义会导致更难或者无法支持不同的主题（例如，浅色/深色主题）

![image-20220929193004254](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929193004254.png)

##### 	3、主题颜色：

###### 		1、一种更灵活的方法是从主题中检索颜色：

![image-20220929193142758](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929193142758.png)

###### 		2、由于主题中的每种颜色都是Color实例，因此我们还可以使用copy方法轻松地“派生”颜色：

![image-20220929193154335](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929193154335.png)

##### 	4、Surface颜色和内容颜色

###### 		许多组件都接受一对颜色，分别是“颜色”和“内容颜色”：这样一来，我们不仅可以设置可组合项的颜色，而且还能为“内容”（即包含在其中的可组合项）提供默认颜色。默认情况下，许多可组合项都使用这种内容颜色，例如Text颜色或Icon色调。contentColorFor方法可以为任何主题颜色检索适当的"on"颜色。例如：如果我们设置primary背景，它就会返回onPrimary作为内容颜色。如果我们设置非主题背景颜色，则应自行提供合理的内容颜色

![image-20220929193708322](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929193708322.png)



##### 	5、Header组件：

###### 		目前：我们的Header组件始终具有Color.LightGray背景。这在浅色主题中看起来没有问题，但在深色主题中，就会与背景形成高度对比。它们并不指定特定的文本颜色，因此会继承不能与背景形成对比的当前内容颜色：

![image-20220929201300524](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929201300524.png)



###### 		在Home.kt的Header可组合项中，移除用于指定硬编码颜色的background修饰符。改为将Text封装在包含主题派生颜色的Surface中，并指定相应内容应采用primary颜色：

![image-20220929201559506](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929201559506.png)

##### 	6、内容Alpha值

###### 		1、通常情况下，我们希望通过强调或弱化内容来突出重点并体现出视觉上的层次感。Material Design建议采用不同的不透明度来传达这些不同的重要程度

###### 		2、Jetpack Compose通过LocalContentAlpha实现此功能，我们可以通过为此CompositionLocal提供一个值来为层次结构指定内容Alpha值，以便子可组合项可以使用此值，例如Text和Icon

###### 		3、Material 指定了一些标准Alpha值（high、medium、disabled），MaterialTheme默认将LocalContentAlpha设为ContentAlpha.high



##### 	7、primarySurface

###### 		Material Design 建议避免在深色主题中使用大面积明亮的颜色。一种常见模式是在浅色主题中将容器设为primary颜色，并在深色主题中将其设为surface颜色；许多组件都默认使用此策略，例如应用栏和底部导航栏。为了便于实现，Colors提供了primarySurface颜色，以准确提供上述行为

![image-20220929203301416](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929203301416.png)



##### 		8、处理文本

###### 			1、我们使用Text可组合项来显示文本，使用TextField和OutlinedTextField进行文本输入，并使用TextStyle对文本应用单一样式。

###### 			2、正如我们在设置颜色时所看到的那样，用于显示文本的Material组件将获取我们的主题排版自定义设置

###### 			3、组件本身往往不会显示文本，而是提供"槽位API"，让我们能够传入Text可组合项。那么，组件是如何设置主题排榜样式的呢？		它们使用ProvideTextStyle可组合项（本身就使用CompositionLocal）来设置"当前"TextStyle。如果未提供具体的textStyle参数，Text可组合项会默认查询"当前"样式

![image-20220929203841308](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929203841308.png)

###### 			4、主题文本样式：就像处理颜色时一样，最好从当前主题中检索TextStyle，从而鼓励我们使用一组数量少且一致的样式，并使其更易于维护。MaterialTheme.typography会检索在MaterialTheme可组合项中设置Typography实例，让我们能够使用自己定义的样式

![image-20220929204102940](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929204102940.png)

###### 			5、多种样式：如果我们需要对某些文本应用多种样式，可以使用AnnotatedString类来应用标记，从而为一系列文本添加SpanStyle

![image-20220929204438805](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929204438805.png)

###### 			6、处理形状：

###### 					与颜色和排版一样，如果设置形状主题，相应设置会反映在Material组件中。例如，Button会获取为小组件设置的形状：

![image-20220929204726664](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929204726664.png)

###### 					有些组件会使用经过修改的主题形状以适应其上下文的要求。例如，默认情况下TextField使用小型形状主题，但它会对底角应用零边角大小：

![image-20220929204911324](C:\Users\Ywhuii\Documents\Jetpack Compose\代码图片示例\image-20220929204911324.png)