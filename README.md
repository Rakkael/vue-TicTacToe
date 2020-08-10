纯前端 井字棋实现
----------------


大致思路：
-------

父组件直接用App.vue

创建子组件Box.vue，在子组件中设计井字棋的一个方格。在父组件中调用9次子组件，用flex排列成'井'字型。

利用$emit向父组件中传递数据，数据包括 被点击的是第几个Box、Box中的内容是X还是O

在父组件中记录点击次数，每触发一次自定义事件，count++，并利用props把当前的count值传递给子组件，用于判断子组件中显示 X 还是 O

判定规则：count 和 2 取余，如果结果等于 0 则为 X； 结果不为 0 则为 O

这样基本上就实现了一个井字棋了


胜负判定方法的实现：
 --------

在父组件中定义了一个3x3矩阵，把接受到的数据 （被点击的是第几个Box、Box中的内容是X还是O）赋给矩阵相对应的位置。

例如，第0个Box被点击，内容被传入 矩阵的[0,0] 位。
        第1个Box被点击，内容被传入 矩阵的[0,1] 位。
        ···
        第8个Box被点击，内容被传入 矩阵的[2,2] 位。

然后利用for循环，对矩阵进行同一行或者同一列的值进行遍历，如果某一行中内容全部相同，则判断有人胜出。（注意：排除掉矩阵的初始值 null）

在利用if判断两条对角线上的内容是否相同，三者都相同且不为null，则判定有人胜出。

------
大概就是这些了。一开始觉得还很简单，信心满满。结果做的时候头皮发麻。尤其是判胜规则，重写了好几次，深感自己是个制杖，太菜了。