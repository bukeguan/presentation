#   CSS属性

## 三大特性

### 1、层叠性

如果发生了样式冲突，那就会根据一定的规则（选择器优先级）进行样式的层叠（覆盖）

注：样式冲突：指元素的同一个样式名被设置了不同的值，这就是冲突。

### 2、继承性

元素会自动拥有其父元素或其祖先元素上所设置的某些样式，==优先继承离得近的==

常见的可继承属性：

text-,  font-,   line-,    color......

### 3、优先级

!important>行内样式>ID选择器>类选择器>元素选择器>*>继承的样式

注：计算权重时需注意：**并集选择器的每一个部分是分开算的**

## 颜色

### rgb与rgba

使用红、绿、蓝三种光的三原色进行组合

+ r表示红色
+ g表示绿色
+ b表示蓝色
+ a表示透明度

规律：若三种颜色值相同，呈现的是灰色，值越大，灰色越浅

### HEX与HEXA

HEX原理同rgb一样，依然是通过：红、绿、蓝进行组合，只不过要用6个数字，分成3组来表达

格式为：#rrggbb

注：IE浏览器不支持HEXA，但支持HEX

### HSL和HSLA

HSL是通过：色相、饱和度、亮度，来表示一个颜色的，格式为：hsl（色相、饱和度、亮度）

+ 色相：取值范围是0~360度，具体度数对应的颜色如下图：

  <img src="Image/HSL.jpeg" style="zoom:50%">
  
+ 饱和度：取值范围是0%~100%（向色相中对应颜色中添加灰色，0%全灰，100%没有灰）

+ 亮度： 取值范围是0%~100%（0%亮度没了为黑色，100%亮度太强为白色）

HSLA其实就是在HSL的基础上添加了透明度

## 渐变

### 1、线性渐变

+ 多个颜色之间的渐变，默认从上到下渐变：background-image：linear-gradient（red, yellow, green)
+ 使用关键词设置线性渐变的方向：background-image：linear-gradient（to top，red，yellow，green）
+ 使用角度设置线性渐变的方向：background-imag：linear-gradient（30deg，red，yellow，green）
+ 调整开始渐变的位置：background-image：linear-gradient（red 50px， yellow 100px，grenn 150px）

### 2、径向渐变

+ 多个颜色之间的渐变，默认从圆心四散（不一定为正圆，要看容器的本身宽高比）：background-image：radial-radient（red，ellow，green）

+ 使用关键词调整渐变圆的圆心位置：background-image：radial-gradient（at rigth top， red，yellow，green）

+ 使用像素值调整渐变圆的圆心位置：background-image：radial-gradient（at 100px 100px， red，yellow，green）

+ 调整形状为正圆：background-image：radial-gradient（circle， red，yellow，green）或

  background-image：radial-gradient（100px 100px， red，yellow，green）

### 3、重复渐变

+ 需要在上面两个渐变基础上添加repeating。

## 字体属性

### 1、字体大小

+ 属性名：font-size

+ 语法：

  ~~~css
  div {
  	font-size:40px;
  }
  ~~~

+ 注意点：

  + 不同浏览器默认的字体大小可能不一致，所以最好给一个明确的值，不要用默认的大小
  + 通常以给body设置font-size属性，这样body中的其他元素就都可以继承了

### 2、字体族

+ 属性名：font-family

+ 语法： 

  ~~~css
  div {
      font-family: "STICaiyun", "Microsoft YaHei", sans-serify;
  }
  ~~~

+ 注意：

  + 使用字体的英文名兼容性会更好
  + 如果字体名包含空格，必须用引号包裹起来
  + 可以设置多个字体按照从左到右的顺序逐个查找，找到就用，没有就使用后面的，sans-serify表示非衬线字体，若是前面没有找到字体便会找非衬线字体，serify衬线字体同样

### 3、字体风格

+ 属性名：font-style
+ 常用值：
  1. normal：正常
  2. italic：斜体（使用字体自带的斜体效果）
  3. oblique：斜体（强制倾斜产生的斜体效果）

### 4、字体粗细

+ 属性名：font-weight

+ 常用值：

  关键词：

  1. lighter：细
  2. normal：正常
  3. bold：粗
  4. bolder：很粗（多数字体不支持）

  数值：

  1. 100~1000且无单位，数值越大，字体越粗
  2. 100\~300等同于lighter，400~500等同于normal，600及以上等同于bold

### 5、字体复合写法

+ 属性名：font，可以把上述字体样式合并成一个属性
+ 编写规则：
  1. **字体大小、字体族必须都写上**
  2. **字体族必须是最后一位、字体大小必须是倒数第二位**
  3. 各个属性间用空格隔开

### 6、行高

+ 属性名：line-height

+ 可选值：

  1. normal：由浏览器根据文字大小决定一个默认值
  2. 像素（px）
  3. 数字：参考自身font-size的倍数（很常用）
  4. 百分比：参考自身font-size的百分比

+ 备注：由于字体设计原因，文字在一行中，并不是绝对垂直居中，若一行中都是文字，不会太影响观感

  行高注意事项：

  1. line-height过小文字会产生重叠，且最小值是0，不能为负数
  2. **line-height是可以继承的，且为了能更好的呈现文字，最好写数值**
  3. line-height和height是什么关系？
     + 设置了height，那么高度就是height的值
     + 不设置height，会根据line-height计算高度

  应用场景：

  1. 对于多行文字：控制行与行之间的间距
  2. 对于单行文字：让height等于line-height，可以实现文字垂直居中

### 7、Web字体

+ 可以通过**@font-face**指定字体的具体位置，浏览器会自动下载该字体，这样就不会依赖用户电脑上的字体了

+ 语法：

  ~~~css
  @font-face {   //简写方式，会使得网页加载过多资源，
      font-family:"情书字体"；
      src = url('./jjjj');
  }
  ~~~

+ 定制字体，中文的字体文件很大，使用完整的字体文件不现实，通常针对某几个字进行单独定制

+ 可使用阿里web字体定制工具：https://www.iconfont.cn/webfont

### 8、 字体图标

+ 相比图片更加清晰
+ 灵活性高，更方便改变大小、颜色、风格等
+ 兼容性好，IE也能支持
+ 注：字体图标的具体使用方式，每个平台不尽相同，最好参考平台使用指南

## 文本属性

### 1、文本颜色

+ 属性名：color
+ 可选值：
  1. 颜色名
  2. rgb或rgba
  3. HEX或HEXA
  4. HSL或HSLA

### 2、文本间距

+ 字母间距：letter-spacing
+ 单词间距：word-spacing（通过空格识别词）
+ 属性值为像素（px）正值让间距增大，负值让间距缩小

### 3、文本修饰

+ 属性名：text-decoration

+ 可选值：

  1. none：无装饰线（常用）
  2. underline：下划线（常用）
  3. overline：上划线
  4. line-through：删除线

  可搭配如下值使用：

  1. dotted：虚线
  2. wavy：波浪线
  3. 也可以指定颜色

### 4、文本缩进

+ 属性名：text-indent
+ 属性值：css中的长度单位，例如：px

### 5、文本对齐_水平_

+ 属性名：text-align
+ 常用值：
  1. left：左对齐
  2. right：右对齐
  3. center：居中对齐

### 6、文本对齐_垂直_

+ 顶部：无需任何属性，在垂直方向上，默认就是顶部对齐

+ 居中：对于单行文字，让height=line-height即可

+ 底部：对于单行文字，临时的方式：
  让line-height= （height*2）- font-size - x

  注：x是根据字体族，动态决定的一个值 

### 7、vertical-align

+ 属性名：vertical-align

+ 作用：用于指定==同一行元素之间==，或表格单元格内文字的垂直对齐方式

+ 常用值：

  1. baseline：使元素的基线与父元素的基线对齐
  2. top：使元素的==顶部==与其==所在行的顶部==对齐
  3. middle：使元素的==中部==与==父元素的基线==加上父元素字母x的一半对齐
  4. bottom：使元素的==底部==与其==所在行的底部==对齐

  注：**vertical-align**不能控制块元素

### 8、文本阴影

+ 语法：text-shadow：h-shadow v-shadow blur color；
+ h-shadow：必须写，水平阴影位置，允许负值
+ v-shadow ：必须写，垂直阴影位置，允许负值
+ blur：可选，模糊距离
+ color：可选，阴影的颜色 

### 9、文本换行

+ normal：文本超出边界自动换行，文本中的换行被浏览器识别为一个空格
+ pre：原样输出，与pre标签效果相同
+ pre-wrap：在pre效果的基础上，超出元素边界自动换行
+ pre-line：在pre效果的基础上，超出边界自动换行，且只识别文本中的换行，空格会忽略
+ nowrap：强制不换行

### 10、文本溢出

+ clip：当内联内容溢出时，将溢出部分裁剪掉
+ ellipsis：当内联内容溢出块容器时，将溢出部分替换为“..."
+ 注：要使text-overflow属性生效，快容器必须显示定义overflow为非visible值，white-space为nowrap值

### 11、文本描边

+ 注：该功能仅webkit内核浏览器支持
+ -webkit-text-stroke-width：设置文字描边的宽度，写长度值
+ -webkit-text-stroke-color：设置文字描边的颜色，写颜色值
+ -webkit-text-stroke：复合属性，设置文字描边宽度和颜色

## 列表属性

+ 列表相关属性，可以用在ul、ol、li元素上

+ list-style-type：设置列表符号

  属性值：

  + none：不显示前面的标识
  + square：实心方块
  + disc：圆形
  + decimal：数字
  + lower-roman：小写罗马字
  + upper-roman：大写罗马字
  + lower-alpha：小写字母
  + upper-alpha：大写字母

+ list-style-position：设置列表符号的位置

  属性值：

  + inside：在li的里面
  + outside：在li的外面

+ list-style-image:自定义列表符号

  属性值：

  + url：图片地址

+ list-style：复合属性（==没有数量、顺序的要求==）

## 表格属性

### 1.  边框相关属性（其他元素也能用）

+ border-width ：边框宽度

+ border-color：边框颜色

+ border-style：边框风格

  属性值：

  + none
  + solid：实线
  + dashded：虚线
  + dotted：点线
  + double：双实线

+ border：边框复合属性，==没有数量顺序的要求==

### 2. 表格独有的属性（只有table标签才能使用）

+ table-layout：设置列宽度，属性值为：
  + auto：自动
  + fixed：固定列宽

+ border-spacing：单元格间距：css中可用的长度值，生效的前提：单元格边框不能合并；
+ border-collapse：合并单元格边框；属性值：
  + collpase：合并
  + separate：不合并

+ empty-cells：隐藏没有内容的单元格；属性值：
  + show：显示
  + hide：隐藏
  + **生效的前提：单元格边框不能合并；**

+ caption-side：设置表格标题位置；属性值：
  + top：上面
  + bottom：在表格下面


## 背景属性

+ background-color：设置背景颜色

  默认背景颜色是transparent

+ background-image：设置背景图片

  url（图片地址）

+ background-repeat：设置背景重复方式

  repeat：重复，铺满整个元素，默认值

  repeat-x：只在水平方向重复

  repeat-y：只在垂直方向重复

  no-reapeat：不重复

+ background-position：设置背景图位置

  水平：left、center、right

  垂直：top、center、bottom

  若只写一个值，另一个方向上取center

  通过长度指定坐标位置：以元素左上角为坐标原点，设置图片左上角的位置，两个值分别是x坐标和y坐标

+ background：复合属性，没有数量和顺序要求

## 鼠标属性

+ cursor：设置鼠标光标的样式

  属性值；

  + pointer：小手
  + move：移动图标
  + text：文字选择器
  + crosshair：十字架
  + wait：等待
  + help：帮助

## 盒子模型

### 1. 长度单位

1. px ：像素
2. em：相对元素font-size的倍数
3. rem：相对根字体大小，html标签就是根
4. %：相对父元素计算

### 2. 元素的显示模式

+ 块级元素（block）
  1. 在页面中==独占一行==，不会与任何元素共用一行，是从上到下排列的
  2. 默认宽度：撑满==父元素==
  3. 默认高度：由==内容==撑开
  4. 可以通过css设置宽高
+ 行内元素（inline）
  1. 在页面中==不独占一行==，一行中不能容纳下的行内元素，会在下一行继续从左到右排列
  2. 默认宽度：由==内容==撑开
  3. 默认高度：由==内容==撑开
  4. ==无法==通过css设置宽高
+ 行内块元素（inline-block）
  1. 在页面中==不独占一行==，一行中不能容纳下的行内元素，会在下一行继续从左到右排列
  2. 默认宽度：由==内容==撑开
  3. 默认高度：由==内容==撑开
  4. ==可以==通过css设置宽高

### 3. 总结各元素的显示模式

<img src="Image/元素的显示模式.png" style="zoom:80%">

### 4. 修改元素显示模式

+ 通过css中的display属性可以修改元素的默认显示模式，常用值：

  none：元素会被==隐藏==

  block：元素将作为块级元素显示

  inline：元素作为内联元素显示

  inline-block：元素作为行内块元素显示

### 5.盒子模型的组成

+ css会把所有的HTML元素都看成一个盒子，所有的样式也都是基于这个盒子

  1. margin（外边距）：盒子与外界的距离
  2. border（边框）：盒子的边框
  3. padding（内边距）：紧贴内容的补白区域
  4. cotent（内容）：元素中的文本或后代元素都是它的内容

  图示如下：

  <img src="Image/盒子模型.png" style="zoom:50%">

  盒子的大小=content+左右padding+左右border

  注：外边距margin不会影响盒子的大小，但会影响盒子的位置

### 6. 盒子内容区（content）

  + width、max-width、min-width：设置内容区宽度、最大宽度、最小宽度

  + height、max-height、min-height：设置内容区域的高度、最大高度、最小高度

    注：最大/最小宽度一般不与width一起使用

    最大/最小高度一般不与height一起使用

### 7. 默认宽度

  + 默认宽度，就是==不设置width==属性时，元素所呈现出来的宽度

    总宽度=父的content-自身的左右margin

    内容区的宽度=父的content-自身左右margin-自身左右border-自身左右padding

### 8.盒子内边距

  + padding-top：上内边距

  + padding-right：右内边距

  + padding-bottom：下内边距

  + padding-left：左内边距

  + padding：复合属性：按照上下左右顺时针排列

    例如：padding:10px 30px 20px; //上边距为10，下边距为20，左右边距为30

  注：

  1. padding值不能为负数
  2. 行内元素的左右内边距没问题，上下内边距不能完美设置

### 9. 盒子边框

  + border-style：边框线风格
  + border-width：边框线宽度（==默认3px==)
  + border-color：边框线颜色(==默认黑色==)
  + border：复合属性，没有顺序和数量要求

### 10. 盒子外边距

  + margin-left、margin-right、margin-top、margin-bottom、margin
  
    注意事项：
  
    1. 子元素的marigin，是参考父元素的content计算的
    2. 上margin、左margin：影响自身的位置；下margin、右margin：影响后面兄弟元素的位置
    3. 块级元素、行内元素，均可以完美的设置四个方向的margin；但行内元素，左右margin可以完美设置，上下margin无效
    4. margin的值也可以是auto，如果给一个块级元素设置左右margin都为auto，该块级元素会在父元素中水平居中
    5. margin的值可以是负值

### 11.resize-调整盒子大小

+ none：不允许用户调整元素大小
+ both：用户可以调节元素的宽高
+ horizontal：用户可以调节元素的宽度
+ vertical：用户可以调节元素的高度

### 12.box-shadow-盒子阴影

+ h-shadow:水平阴影位置，可以为负值，必须填写
+ v-shadow：垂直阴影位置，可以为负值，必须填写
+ blur：可选，模糊距离
+ spread：可选，阴影的外延值
+ color：可选，阴影的颜色
+ inset：可选，将外部阴影改为内部阴影

### 13.opacity-不透明度

+ opacity属性能为整个元素添加透明效果，值是0到1之间的小数，0是完全透明，1表示完全不透明

  注：opacity于rgba的区别

  opacity是一个属性，设置的是整个元素（包括元素里的内容）的不透明度

  rgba是颜色的设置方式，用于设置颜色，它的透明度，仅仅是调整颜色的透明度

### 14.背景属性

1. background-origin
   + 设置背景图的原点
   + padding-box：从padding区域开始显示背景图像
   + border-box：从border区域开始显示背景图像
   + content-box：从content区域开始显示背景图像
2. background-clip
   + border-box：从border区域开始向外裁剪背景
   + padding-box：从padding区域开始向外裁剪背景
   + content-box：从content区域开始向外裁剪背景
   + text：背景图只呈现在文字上，需要在background-clip前加上-webkit-前缀
3. background-size:
   + 设置背景图的尺寸
   + 用长度值指定背景图片大小，不允许负值：background-size: 300px, 200px;
   + 用百分比指定背景图的大小，不允许负值：background-size: 100%, 100%;
   + auto:背景图的真实大小--默认值
   + contain：将背景图等比缩放，使背景图的宽或高，与容器的宽或高相等
   + cover：将背景图等比缩放，直到完全覆盖容器，图片会尽可能完全的显示在元素上。---相对较好的选择
4. 复合属性
   + background:color url repeat psition / size origin clip
   + 注：
     + origin和clip的值如果一样，如果只写一个值，则origin和clip都设置，如果设置了两个值，前面的是origin，后面的为clip
     + **size的值必须写在position值的后面，并且用“/"分开**

### 15.边框属性

1. 边框圆角
   + border-radius：将盒子变为圆角
     + border-top-left-radius:左上角圆角半径，一个值为正圆半径，**两个值分别是椭圆的x半径、y半径**，其他类似
2. 边框外轮廓（了解）
   + outline-width：外轮廓的宽度
   + outline-color：外轮廓的颜色
   + outline-style：外轮廓的样式
   + outline-offset：设置外轮廓与边框的距离，正负值都可以设置

#### margin塌陷问题

什么是margin塌陷：第一个子元素的==上margin==会作用在父元素上，最后一个子元素的==下margin==会作用在父元素上

如何解决margin塌陷问题？

+ 给父元素设置不为0的padding
+ 给父元素设置宽度不为0的border
+ 给父元素设置css样式**overflow：hidden**

####  margin合并问题

什么是margin合并：上面元素的==下外边距==和下面兄弟元素的==上外边距==会合并，取一个最大的值，而不是相加

#### 处理内容溢出

+ overflow：溢出内容的处理方式

  属性值：

  + visible：显示，默认值
  + hidden：隐藏
  + scroll：显示滚动条，不论内容是否溢出
  + auto：自动显示滚动条，内容不溢出不显示

+ overflow-x：水平方向溢出内容的处理方式

+ overflow-y：垂直方向溢出内容的处理方式

注：

1. overflow-x、overflow-y不能一个是hidden，一个是visible，是实验性属性，不建议使用
2. overflow常用的值是hidden和auto，除了能处理溢出的显示方式，还可以解决很多疑难杂症

#### 隐藏元素的方式

1. visibility属性：

   其默认值是show，如果设置为hidden，元素会隐藏

   元素看不见了，还占有原来的位置（元素的大小依然保持）

2. display属性：

   设置display：none，就可以让元素隐藏

   彻底的隐藏，不占用任何位置

#### 样式的继承

**会继承的css属性**：

字体属性、文本属性（除了vertical-align）、文本颜色等

**不会继承的css属性**：

边框、背景、内边距、外边距、宽高等

规律：能继承的属性都是不影响布局的，简单说：都是和盒子模型无关的

### 布局小技巧

1. 行内元素、行内块元素，可以被父元素当文本处理

   即：可以像处理文本对齐一样，去处理：行内、行内块在父元素中的对齐

   例如：text-align、line-height、text-indent

2. 如何让子元素，在父元素中==水平居中==：

   + 若子元素为块元素，给元素加上：**margin：0 auto**；
   + 若子元素为行内元素、行内块元素，给父元素加上：text-align：center；

3. 如何让子元素，在父亲中==垂直居中==：

   + 若子元素为块元素，给子元素加上：margin-top，值为：（父元素content-子元素盒子总高）/2
   
   + 若子元素为行内元素、行内块元素：
   
     让父元素的height = line-height，每个子元素都加上：vertical-align：middle；
   
     补充：若想绝对垂直居中，父元素font-size设置为0

#### 元素之间的空白问题

+ 产生的原因：

  行内元素、行内块元素，彼此之间的换行会被浏览器解析为一个空白字符

+ 解决方案：

  1. 去掉换行和空格
  2. 给父元素设置font-size：0，再给需要显示文字的元素，单独设置字体大小

行内块的幽灵空白问题

+ 产生原因：

  行内块元素与文本的基线对齐，而文本的基线与文本最低端之间是有一定距离的

+ 解决方案：

  1. 给行内块设置vertical，值不为baseline即可
  2. 若父元素中只有一张图片，设置图片为display：block
  3. 给父元素设置font-size：0，如果该行内块内部还有文本，则需单独设置font-size

## 浮动

### 简介

 最初，浮动是用来实现文字环绕图片效果的，现在浮动是主流的页面布局方式之一

### 浮动后的特点

1. 脱离文档流
2. 不管浮动前是什么元素，浮动后：默认宽与高都是被内容撑开，而且可以设置宽高
3. 不会独占一行，可以与其他元素共用一行
4. 不会margin合并，也不会margin塌陷，能完美的设置四个方向的margin和padding
5. 不会像行内块一样被当作文本处理（没有行内块的空白问题）

### 浮动后会有哪些影响：

对兄弟元素的影响：后面的兄弟元素，会占据浮动元素之前的位置，在浮动元素的下面；对前面的兄弟无影响

对父元素的影响：不能撑起父元素的高度，导致父元素高度塌陷，但父元素的宽度依然束缚浮动的元素

### 解决浮动产生的影响：

1. 给父元素设置高度
2. 给父元素也设置浮动，带来其他影响
3. 给父元素设置overflow：hidden
4. 在所有浮动元素的最后面，添加一个块级元素，并给该块级元素设置clear：both
5. 给浮动元素的父元素，设置伪元素，通过伪元素清除浮动

注：布局中的一个原则：设置浮动的时候，兄弟元素要么全都浮动，要么全都不浮动

## 相对定位

1. 如何设置相对定位？

   + 给元素设置position：relative，即可实现相对定位
   + 可以使用left、right、top、bottom四个属性调整位置

2. 相对定位的参考点在哪里？

   + 相对自己原来的位置

3. 相对定位的特点：

   + 不会脱离文档流，元素位置的变化只是视觉效果上的变化，不会对其他元素产生任何影响

   + 定位元素的显示层级比普通元素高，无论什么定位，显示层级都是一样的

     默认规则是：

     + 定位的元素会盖在普通元素之上
     + 都发生定位的两个元素，后写的元素会盖在先写的元素之上

   + left不能和right一起设置，top和bottom也是一样

   + 相对定位的元素，也能继续浮动，但不推荐这样做

   + 相对定位的元素，也能通过margin调整位置，但不推荐这样做

   **注**：绝大多数情况下，相对定位，会与绝对定位配合使用

## 绝对定位

1. 如何设置绝对定位

   + 给元素设置position：absolute即可实现绝对定位
   + 可以使用left、right、top、bottom四个属性调整位置

2. 绝对定位的参考点在哪里

   + 参考它的包含块

     包含块：

     1. 对于没有脱离文档流的元素：包含块就是父元素
     2. 对于脱离文档流的元素：包含块就是第一个拥有定位属性的祖先元素

3. 绝对定位元素的特点：

   + 脱离文档流，会对后面的兄弟元素、父元素有影响

   + left不能和right一起设置，top和bottom不能一起设置

   + 绝对定位、浮动不能同时设置，如果同时设置，浮动失效，以定位为主

   + 绝对定位的元素，也能通过margin调整位置，但不推荐这样做

   + 无论是什么元素设置为绝对定位之后，都变成了定位元素

     定位元素：默认宽、高都被内容所撑开，且能自由设置宽高

## 固定定位

1. 如何设置固定定位

   + 给元素设置position：fixed，即可实现固定定位
   + 可以使用left、right、top、bottom四个属性调整位置

2. 固定定位的参考点在哪里

   + 参考它的视口

     视口：对于PC浏览器来说，视口就是我们看网页的那扇"窗户"

3. 固定定位元素的特点

   + 脱离文档流，会对后面的兄弟元素、父元素有影响
   + left不能和right一起设置，top和bottom不能一起设置
   + 固定定位、浮动不能同时设置，如果同时设置，浮动失效，以固定定位为主
   + 固定定位的元素，也能通过margin调整位置，但不推荐这样做
   + 无论是什么元素设置为固定定位之后，都变成了定位元素

## 粘性定位

1. 如何设置粘性定位
   + 给元素设置position：sticky，即可实现粘性定位
   + 可以使用left、right、top、bottom四个属性调整位置，不过最常用的是top值
2. 粘性定位的参考点在哪里
   + 离他最近的一个拥有”滚动机制“的祖先元素，即便这个祖先不是最近的真是可滚动祖先
3. 粘性定位元素的特点
   + 不会脱离文档流，他是一种专门用于窗口滚动时的新的定位方式
   + 最常用的值是top值
   + 粘性定位和浮动可以同时设置，但不推荐这样做
   + 粘性定位的元素，也能通过margin调整位置，但不推荐

## 定位层级

1. 定位元素的显示层级比普通元素高，无论什么定位，显示层级都是一样的
2. 如果位置发生重叠，默认情况是：后面的元素，会显示在前面元素之上
3. 可以通过css属性z-index调整元素的显示层级
4. z-index的属性值是数字，没有单位，值越大显示层级越高
5. 只有定位的元素设置z-index才有效
6. 如果z-index值大的元素，依然没有覆盖掉z-index值小的元素，那么请检查其包含块的层级

## 定位的特殊应用

注意：

+ 发生固定定位、绝对1定位后，元素都变成了定位元素，默认宽高被内容撑开，且依然可以设置宽高
+ 发生相对定位后，元素依然是之前的显示模式
+ 所说的特殊应用，只针对**绝对定位**和**固定定位**的元素，不包括相对定位的元素

##### 让定位元素的宽充满包含块

1. 块宽想与包含块一致，可以给定位元素同时设置left和right为0
2. 高度想与包含块一致，top和bottom设置为0

##### 让定位元素在包含块中居中

+ 方案一

  ~~~css
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  ~~~

+ 方案二

  ~~~css
  left: 50%;
  top: 50%;
  margin-left: 父元素的宽度一半；
  margin-top：父元素的高度一半；
  //注：该定位元素必须设置宽高
  ~~~

## 布局

### 版心

+ 在PC端网页中，一般都会有一个固定宽度且水平居中的盒子，来显示网页的主要内容，这是网页的版心
+ 版心的宽度一般是960~1200像素之间
+ 版心可以是一个，也可以是多个

### 常用布局名词

+ 顶部导航条：topbar
+ 页头：header、page-header
+ 导航：nav、navigator、navbar
+ 搜索栏：search、search-box
+ 横幅、广告、宣传图：banner
+ 主要内容：content、main
+ 侧边栏：aside、sidebar
+ 页脚：footer、page-footer

## 状态标签

### meter

+ 语义：定义已知范围内的标量测量，也被称之为gauge（尺度），双标签，例如：电量、磁盘用量等
+ 常用属性：
  + high：规定高值（数值）
  + low：规定低值（数值）
  + min：规定最小值（数值）
  + max：规定最大值（数值）
  + optimum：规定最优值（数值）
  + value：规定当前值（数值）

### progress

+ 语义：显示某个任务完成的进度的指示器，一般用于表示进度条，双标签，例如：工作完成进度

+ 常用属性：

  max：规定目标值（数值）

  value：规定当前值（数值）

## 列表标签

+ **datalist**：用于搜索框的关键字提示（双标签）
+ **details**：用于展示问题和答案，或对专有名词进行解释（双标签）
+ **summary**：卸载deatiils里面，用于指定问题或转悠名词（双标签）

## 新增文本标签

### 文本注音

+ **ruby**：包裹需要注音的文字（双标签）

+ **rt**：写注音，rt标签写在ruby的里面（双标签）

+ 列：

  ~~~css
  <ruby>
  	<span>小学生</span>
  	<rt>xiaoxuesheng</rt>//注音需要写在下方
  </ruby>
  ~~~

### 文本标记

+ **mark**：标记（双标签）

## 新增表单功能

### 表单控件新增属性

+ **placeholder**：提示文字（注意：不是默认值，value是默认值），适用于文字输入类的表单控件
+ **required**：表示该输入项必填，适用于出按钮外其他表单控件
+ **autofocus**：自动获取焦点，适用于所有表单控件
+ **autocomplete**：自动完成，可以设置为**on或off**，适用于文字输入类的表单控件
+ **pattern**：填写正则表达式，适用于文本输入类表单控件，注：多行输入不可以用，且空的输入框不会验证，往往会与required配合

## 视频标签

+ \<video>标签用来定义视频，它是双标签
+ 属性：
  + src：url地址
  + width：设置视频播放器宽度
  + height：设置视频播放器高度
  + controls：向用户显示视频控件
  + muted：视频静音
  + autoplay：视频自动播放
  + loop：循环播放
  + poster：视频封面
  + preload：none：不预加载视频；metadata：仅预先获取视频的元数据；auto：下载整个视频文件

## 新增全局属性

+ <img src="Image/image-20231017214511731.png" style="zoom:80%">

## HTML5兼容性处理

+ 添加元信息，让浏览器处于最优渲染模式

  ~~~css
  <! --设置IE总是使用最新的文档模式进行渲染-- >
  <meta http-equiv="X-UA-Compatible" content="IE=Edge">
  <! --优先使用 webkit（Chromium）内核渲染，针对360等浏览器 -- >
  <meta name="renderer" content="webkit"
  ~~~

+ 使用html5shiv让低版本浏览器认识H5的语义化标签

  ~~~css
  <! -- [if lt ie 9]>
  <script src=",,/html5shiv.js"></script>
  <![endif]-- >
  ~~~

  

## display-块和内联元素

+ 块级元素(block):块元素是一个元素，占用了全部宽度，在前后都是换行符;总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示。例：\<h1>、\<p>

+ 内联元素(inline):内联元素只需要必要的宽度，不强制换行；和相邻的内联元素在同一行。例：\<span>、\<a>

+ **display: none**，该元素不会显示，且被隐藏的元素不会占用自身固有宽度高度空间

+  **display: block** ，此元素将显示为块级元素，此元素前后会带有换行符，==若不指定宽高，默认会继承父元素的宽度==

+ **display: inline**， 此元素会被显示未内联元素，元素前后没有换行符

+ **display: inline-block**， 行内块元素，被隐藏的元素会变为行内块元素并显示。

  应用：常将所有\<li>元素加上display: inline-block样式，原本垂直的列表就可以水平显示了。

+ **==display: flex==**，弹性布局，子元素的float、clear和vertical-align属性将失效。

## flex容器的属性

  + **flex-direction**:决定主轴的方向（即项目的排列方向）：
    + row(默认值)，主轴为水平方向，起点在左端。
    + row-reverse：主轴为水平方向，起点在右端。
    + column：主轴为垂直方向，起点在上沿。
    + column-reverse：主轴为垂直方向，起点在下沿。
  + **flex-wrap**: 决定了如果一条轴线排不下，如何换行:
    + nowrap（默认）：不换行。
    + wrap：换行，第一行在上方。
    + wrap-reverse：换行，第一行在下方。
  + **==justify-content==**: 定义了项目在主轴上的对齐方式:
    + flex-start（默认值）：左对齐
    + flex-end：右对齐
    + center： 居中
    + space-between：两端对齐，项目之间的间隔都相等。
    + space-around：每个项目两侧的间隔相等。
  + **align-items**：定义项目在交叉轴上如何对齐：
    + flex-start：交叉轴的起点对齐，一行根据上边对齐。
    + flex-end：交叉轴的终点对齐，一行根据下边对齐。
    + center：交叉轴的中点对齐。
    + baseline: 项目的第一行文字的基线对齐。
    + stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
  + **align-content**：定义了多根轴线的对齐方式：
    + flex-start：与交叉轴的起点对齐，跟作文一样，一行一行紧挨着。
    + flex-end：与交叉轴的终点对齐，跟 flex-start类型，不过时从底部开始数。
    + center：与交叉轴的中点对齐，从中间向下向上扩散。
    + space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
    + space-around：每根轴线两侧的间隔都相等。
    + stretch（默认值）：轴线占满整个交叉轴。

+ **display: inherit**， 继承父元素display属性的值

## border-边框

+ **border-width**， 为元素指定边框的宽度
+ **border-style**， 为元素指定边框样式：
  1. **none**， 不设置
  2. **hidden**，隐藏
  3. **dotted**， 显示一系列的点
  4. **dashed**， 显示一系列小线段
  5. **solid**， 显示一条单一的实心直线
  6. **double**， 显示两条实心的直线
+ **border-color**， 为元素指定边框颜色
+ **border-radius**， 为元素指定边框圆角的半径
+ **border-img**， 为元素设置边框背景

## z-index

该属性是用来设置元素的堆叠顺序或者叫做元素层级，z-index的值越大，元素的层级越高。当元素发生重叠时，层级高的元素会覆盖在层级低的元素的上面，使层级低的重叠部分被遮盖住。

该属性只能在设置了==position:relative | absolute | fixed==的元素和父元素设置了==display:flex==属性的子元素中起作用，在其他元素中是不作用的。

## object-fit

用于规定应如何调整\<img> 或\<video>的大小来适应其容器。

比如：“保留长宽比”或者“展开并占用尽可能多的空间”

+ `fill` - 默认值。调整替换后的内容大小，以填充元素的内容框。如有必要，将拉伸或挤压物体以适应该对象。
+ `contain` - 缩放替换后的内容以保持其纵横比，同时将其放入元素的内容框。
+ `cover` - 调整替换内容的大小，以在填充元素的整个内容框时保持其长宽比。该对象将被裁剪以适应。
+ `none` - 不对替换的内容调整大小。
+ `scale-down` - 调整内容大小就像没有指定内容或包含内容一样（将导致较小的具体对象尺寸）

## text-trasform

改变元素中的字母大小写，而不论源文档中文本的大小写，但是没有明确定义如何确定那些字母要大写，这取决于用户代理如何识别出各个“词”。

+ **none**， 默认-定义带有小写字母和大写字母的标准的文本
+ **capitalize**，文本中的每个单词以大写字母开头
+ **uppercase**，定义仅有大写字母
+ **lowercase**，定义无大写字母，仅有小写字母
+ **inherit**，规定应该从父元素继承 text-transform 属性的值。

## 2D变化

### 1、位移

+ 可以改变元素位置，使用方式如下：
  1. 先给元素添加属性transform
  2. 编写transform的具体值：
     + translatX：设置水平方向位移，需指定长度值，若指定的是百分比，是参考自身宽度的百分比
     + translateY：设置垂直方向的位移，需指定长度值，若指定的是百分比，是参考自身高度的百分比
     + translate：一个值代表水平方向，两个值代表水平和垂直方向
  3. 注：
     + **位移与相对定位很相似，都不脱离文档流，不会影响到其他元素**
     + 与相对定位的区别，相对定位的百分比值，参考的是其父元素；**位移的百分比值，参考的是其自身**
     + 浏览器针对位移有优化，与定位相比，浏览器处理位移的效率更高
     + transform可以链式编写，例：transform：translateX（30px） translateY（40px）
     + **位移对行内元素无效**

### 2、 缩放

+ 让元素放大或缩小，具体使用方式如下：
  1. 先给元素添加转换属性 transform
  2. 编写 transform 的具体值，相关值如下：
     + scaleX：设置水平方向的缩放比列，值为一个数字，1表示不缩放，大于1放大，小于1缩小
     + scaleY：设置垂直方向的缩放比例
     + scale：同时设置两个方向的缩放比例，一个值代表同时设置水平和垂直缩放，两个值分别表示：水平缩放、垂直缩放

### 3、旋转

+ 让元素在二维平面内，顺时针旋转或逆时针旋转，具体使用方式如下：
  1. 先给元素添加转换属性 transform
  2. 编写 transform 的具体值，相关可选值如下：
     + rotate：设置旋转角度，需指定一个角度值（deg），正值顺时针，负值逆时针
  3. **注：旋转会导致坐标系也会跟着旋转，在使用transform复合属性时，建议将其放在最后**

### 4、扭曲（了解）

+ 让元素在二位平面内被“拉扯”，实际开发几乎不用
  1. 给元素添加转换属性 transform
  2. 编写transform的具体值：
     + skewX：设置元素在水平方向扭曲，值为角度值，会将元素的左上角、右下角拉扯
     + skewY：设置元素在垂直方向扭曲，值为角度值，会将元素的左上角、右下角拉扯

### 5、变换原点

+ 元素变化时，默认的原点是元素的中心，使用transform-origin 可以设置变化原点
+ 修改变化原点对位移没有影响，对旋转和缩放会产生影响
+ 如果提供两个值，第一个用于横坐标，第二个用于纵坐标
+ 如果只提供一个，若是像素值，表示横坐标，纵坐标取50%；若是关键词，则另一个坐标取50%

## 3D变换

### 1、空间与景深

+ 开启3D空间，元素进行3D变化的首要操作，**父元素**必须开启3D空间；使用transform-style 开启3D空间，可选值如下：
  + flat：让子元素位于此元素的二维平面内--默认值
  + preserve-3d：让子元素位于此元素的三维空间内（3D空间）
+ 设置景深
  + 何为景深？--指定观察者与z=0平面的距离，能让发生3D变化的元素，产生透视的效果，看起来更加立体
  + 使用perspective设置景深：none：不指定透视；长度值：指定观察者距离z=0平面的距离，不允许负值；
  + 注：perspective设置给发生3D变换元素的**父元素**

### 2、 透视点位置

+ 透视点位置，就是观察者位置，默认的透视点在元素的中心
+ 使用perspective-origin 设置观察者位置，例如：
  + perspective-origin：400px 300px；//相对坐标轴往右偏移了400px，往下偏移300px
+ 通常情况，我们不需要调整透视点位置

### 3、位移

+ 在2D位移的基础上，可以让元素沿z轴位移，具体使用方式如下：
+ 先给元素添加转换属性 transform
+ 编写transform的具体值：
  + translateZ：设置z轴位移，需指定长度值，正值向屏幕外，负值向屏幕里，**且不能写百分比**
  + translate3d：第一个参数对应x轴，第2个参数对应y轴，第3个参数对应z轴，且均不能省略

### 4、旋转 

+ 让元素沿x轴和y轴旋转
+ 先给元素添加转换属性 transform
+ rotateX：设置x轴旋转角度，需指定一个角度值（deg），面对x轴正方向，正值顺时针，负值逆时针
+ rotateY：设置y轴旋转角度，需指定一个角度值（deg），面对y轴征方向，正值顺时针，负值逆时针
+ rotate3d：前3个参数分别表示坐标轴：x,y,z第4个参数表示旋转角度，参数不允许忽略

### 5、 缩放

+ 先给元素添加转换属性 transform
+ scaleZ：设置z轴方向的缩放比例，值为一个数字，1表示不缩放，大于1放大，小于1缩小
+ scale3d：第一个参数对应x轴，第2个参数对应y轴，第3个参数对应z轴，参数不允许省略

### 6、背部可见性

+ backface-visibility：设置旋转的背部是否可见

## 过渡

### 1、基本使用

+ 过渡可以在不使用Flas动画，不适用Javascript的情况下，让元素从一种模式平滑过渡到另一种模式
+ transition-property；定义那个属性需要过渡，只有在该属性中定义的属性才会有过渡效果
  + 常用值：none；all：过渡所有属性；具体某个属性：以逗号分隔
+ transition-duration
  + 作用：设置过渡的持续时间，即一个状态过渡到另一个状态需要耗时多久
  + 常用值：0：没有任何过渡时间；s或ms；列表；

### 2、高级使用

+ transition-delay：指定开始过渡的延迟时间，单位：s或ms
+ transition-timing-function：设置过渡的类型
  + ease：平滑过渡
  + linear：线性过渡
  + ease-in：慢-快
  + ease-out：快-慢
  + ease-in-out：慢-快-慢
  + step-start：等同于steps（1，start）
  + step-end：等同于steps（1，end）
  + steps（integer，？）：接受两个参数的步进函数，第一个参数必须为正整数，指定函数的步数。第二个参数取值可以是start或end，指定每一步的值发生变换的时间点；第二个参数默认值为end
  + cubic-bezie（number，number，number，number）：特定的贝塞尔曲线类型

### 3、复合属性

+ 如果设置了一个时间，表示duration；如果设置了两个时间，第一是duration，第二是delay，其他值没有顺序要求

  ~~~css
  transition：1s 1s linear all;
  ~~~

## 动画

  ### 1、基本使用

  + 第一步：定义关键帧（定义动画）

    1. 简单方式定义：

       ~~~css
       @keyframes 动画名 {
           from {
       		/*preperty1:value1*/
           }
           to {
               /*property1:value2*/
           }
       ~~~

    2. 完整方式定义：

       ~~~css
       @keyframs 动画名 {
           0% {
               /*preperty1:value1*/
           }
           20% {
               /*preperty1:value1*/
           }
           ...
           100% {
               /*preperty1:value1*/
           }
       }
       ~~~

  + 第二步：给元素应用动画，用到的属性如下：

    1. animation-name：给元素指定具体的动画
    2. animation-duration：设置动画所需时间
    3. animation-delay：设置动画延迟

### 2、其他属性

+ animation-timing-function,设置动画的类型，常用值如下：
  1. ease：平滑动画
  2. linear：线性过渡
  3. ease-in；慢-快
  4. ease-out：快-慢
  5. ease-in-out：慢-快-慢
  6. step-end：等同于steps（1，end）
  7. step-start：等同于steps（1，start）
  8. steps（integer，？）：接受两个参数的进步函数，第一个参数必须为正整数，指定函数的步数。第二个参数取值可以是start或end，指定每一步的值发生变换的时间点。第二个参数默认值为end
  9. cubic-bezie（number，number, number, number)：特定的贝塞尔曲线类型
+ animation-iteration-count，指定动画的播放次数，常用值如下：
  1. number：动画循环次数
  2. infinite：无限循环
+ animation-direction，指定动画方向，常用值如下：
  1. normal：正常方向
  2. reverse：反方向运行
  3. alternate：动画先正常运行再反方向运行，并持续交替运行
  4. alternate-reverse：动画先反运行再正方向运行，并持续交替运行
+ animation-fill-mode，设置动画之外的状态
  1. forwards：设置对象状态为动画结束时的状态
  2. bacwards：设置对象状态为动画开始时的状态
+ animation-play-state，设置动画的播放状态，常用值如下：
  1. running：运动
  2. paused：暂停

## 多列布局

+ 常用于报纸的布局，或者**多列图片，类似于壁纸网站那种瀑布流格式**
+ 常用属性如下：
  + column-count：指定列数
  + column-width：指定列宽，值是长度
  + columns：同时指定列宽和列数，复合属性；值没有数量和顺序要求
  + column-gap：设置列边距，值是长度
  + column-rule-style：设置列与列之间边框的风格，值与border-style一致
  + column-rule-width：设置列与列之间边框的宽度，值是长度
  + column-rule-color：设置列与列之间边框的颜色
  + colomn-rule：设置列边框，复合属性
  + column-span：指定是否跨列；值是：none、all

## 伸缩盒模型

### 1、伸缩容器、伸缩项目

+ 伸缩容器：开启了flex的元素，就是：伸缩容器
  1. 给元素设置：display：flex或display：inline-flex，该元素就变成了伸缩容器
  2. display：inline-flex很少使用，因为可以给多个伸缩容器的父容器，也设置为伸缩容器
  3. 一个元素可以同时是：伸缩容器、伸缩项目
+ 伸缩项目：伸缩容器所有**子元素**自动成为了：伸缩项目
  1. 仅伸缩容器的**子元素**成为了伸缩项目，孙子元素、重孙子元素等后代，不是伸缩项目
  2. 无论原来是那种元素，一旦成为了伸缩项目，全都会“块状化”

### 2、主轴与侧轴

+ 主轴：伸缩项目沿着主轴排列，主轴默认是水平的，默认方向是：从左到右
+ 侧轴：与主轴垂直的就是侧轴，侧轴默认是垂直的，默认方向是：从上到下

### 3、 主轴方向

+ 属性名： flex-direction
+ 常用值如下：
  1. row：主轴方向水平从左到右
  2. row-reverse：主轴方向水平从右到左
  3. column：主轴方向垂直从上到下
  4. column-reverse：主轴方向垂直从下到上
+ 注：改变了主轴的方向，侧轴方向也随之改变

### 4、主轴换行方式

+ 属性名：flex-wrap
+ 常用值如下：
  1. nowrap：默认值，不换行
  2. wrap：自动换行
  3. wrap-reverse：反向换行

### 5、复合属性

+ flex-flow：是一个复合属性，复合了flex-direction和flex-wrap两个属性，值没有顺序要求

### 6、主轴对齐方式

+ 属性名：justify-content
+ 常用值如下：
  1. flex-start：主轴起点对齐
  2. flex-end：主轴终点对齐
  3. center：居中对齐
  4. space-between：均匀分布，两端对齐
  5. space-around：均匀分布，两端距离是中间距离的一半
  6. space-evenly：均匀分布，两端距离是与中间距离一致

### 7、 侧轴对齐方式

1. 只有**一行**的情况
   + 属性名：align-items
   + 常用值：
     1. flex-start：侧轴的起点对齐
     2. flex-end：侧轴的终点对齐
     3. center：侧轴的中点对齐
     4. baseline：伸缩项目的第一行文字的基线对齐
     5. stretch：如果**伸缩项目未设置高度**，将占满整个容器的高度
2. **多行**的情况
   + 属性名：align-content
   + 常用值：
     1. stretch：占满整个侧轴（前提是伸缩项目未设置高度）
     2. 其余参考主轴对齐方式

### 8、垂直和水平居中方式

1. 父元素开启弹性布局：display：flex；子元素利用margin：auto；

2. 父元素开启弹性布局：display：flex；且利用主轴和侧轴的居中来实现：justify-content：center；align-items：center

3. 利用变换中的移动来实现：

   给父元素加上定位：position：relative；给子元素加上定位：postion：absolute；top: 50%; left : 50%;

   再利用移动：transform: translate(-50%， -50%)；

### 9、基准长度

+ flex-basis：设置的是主轴方向的基准长度，会让宽度或高度失效
+ 作用：浏览器根据这个属性设置的值，计算主轴上是否有多余空间，默认值auto，即：伸缩项目的宽或高

### 10、拉伸

+ flex-grow：定义伸缩项目的放大比例，默认为0
+ 规则：
  1. 若所有伸缩项目的flex-grow值都为1，则：它们将等分剩余空间
  2. 若三个伸缩项目的flex-grow值分别为：1、2、3，则：分别瓜分到：1/6，2/6，3/6的空间

### 11、压缩

+ flex-shrink：定义了项目的压缩比例，默认为1，即：如果空间不足，该项目会缩小

+ 收缩项目的计算较复杂：

  <img src="Image/image-20231107215049961.png">

### 11、flex复合属性

+ flex为复合属性，默认值为：0 1 auto
+ 如果写 flex：1 1 auto，可简写为： flex：auto
+ 如果写 flex：1 1 0，可简写为： 1
+ 如果写 flex：0 0  auto，可简写为： flex：none
+ 如果写 flex：0 1 auto，可简写为： flex：0 auto

### 12、项目排序

+ order 属性定义项目的排列顺序，数值越小，排列越靠前，默认为0

### 13、单独对齐

+ 通过align-self 属性，可以单独调整某个伸缩项目的对齐方式
+ 默认值为 auto，表示继承父元素的align-items属性

## 响应式布局

### 1、媒体类型

+ 用 @media 后面跟媒体类型，表示在什么样的媒体上呈现所对应想要的效果
+ 媒体类型值：
  + all：检测所有设备
  + screen：检测电子屏幕
  + print：检测打印机

### 2、媒体特性

+ <img src = "Image\image-20231107222257515.png">

### 3、媒体查询—运算符

+ and :并且
+ , 或 or：或
+ not： 否定
+ only：肯定

### 4、常用阈值

+ 在实际开发中，会将屏幕划分成几个区间：
  1. 超小屏幕：小于768px
  2. 中等屏幕：小于992px
  3. 大屏幕：小于1200px
  4. 超大屏幕：大于1200px

### 5、结合外部样式的用法

+ <link rel= "stylesheet" media = "具体的媒体查询" href = "mystylesheet.css">

## Grid布局

### 1、概念

+ 采用网格布局的区域，称为"容器"（container）。容器内部采用网格定位的子元素，称为"项目"（item）

  ```vue
  <div>
    <div><p>1</p></div>
    <div><p>2</p></div>
    <div><p>3</p></div>
  </div>
  ```

+ 上面代码中，最外层的`<div>`元素就是容器，内层的三个`<div>`元素就是项目

+ 注意：**项目只能是容器的顶层子元素，不包含项目的子元素**，比如上面代码的`<p>`元素就不是项目。Grid 布局只对项目生效。

### 2、容器属性

+ **display：grid**，指定一个容器采用网格布局。默认情况下，容器元素都是块级元素，但也可以转为行内元素，如：`display：inline-grid`

  **注**：注意，设为网格布局以后，容器子元素（项目）的`float`、`display: inline-block`、`display: table-cell`、`vertical-align`和`column-*`等设置都将失效。

+ **`grid-template-columns`属性**：定义每一列的列宽，如：`grid-template-columns: 33.33% 33.33% 33.33%;`

+ **`grid-template-rows`属性**：定义每一行的行高，如：`grid-template-rows: 100px 100px 100px;`

+ **auto-fill 关键字**：如果希望每一行（或每一列）容纳尽可能多的单元格，这时可以使用`auto-fill`关键字表示自动填充

+ **auto-fit关键字**：会尽量扩大单元格的宽度

+ **fr关键字**：为了方便的表示比例关系，若两列的宽度分别为1fr和2fr，则表示后者为前者的2倍

+ **auto关键字**：表示由浏览器自己决定长度

+ **网格线的名称**：在grid-template-columns和grid-template-rows中，还可以使用方括号指定每一根网格线的名称，如：

  ```vue
  .container {
    display: grid;
    grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];
    grid-template-rows: [r1] 100px [r2] 100px [r3] auto [r4];
  }
  ```

+ **`grid-row-gap`属性**：设置行与行的间隔（行间距），`grid-column-gap`属性设置列与列的间隔（列间距），`grid-gap`是两者的合并简写方式，

  **注**：根据最新标准，上面三个属性名的`grid-`前缀已经删除，`grid-column-gap`和`grid-row-gap`写成`column-gap`和`row-gap`，`grid-gap`写成`gap`

+ **`grid-template-areas`属性**，网格布局允许指定‘区域’，一个区域由多个或一个单元格组成，该属性用于定义区域，如：

  ```css
  .container {
    display: grid;
    grid-template-columns: 100px 100px 100px;
    grid-template-rows: 100px 100px 100px;
    grid-template-areas: 'a b c'
                         'd e f'
                         'g h i';
  }
  ```

  上面代码先划分出9个单元格，然后将其定名为`a`到`i`的九个区域，分别对应这九个单元格。

  多个单元格合并成一个区域的写法如下:

  ```css
  grid-template-areas: 'a a a'
                       'b b b'
                       'c c c';
  ```

  如果某些区域不需要利用，则使用"点"（`.`）表示:

  ```css
  grid-template-areas: 'a . c'
                       'd . f'
                       'g . i';
  ```

  **注**：

  + 上面代码中，中间一列为点，表示没有用到该单元格，或者该单元格不属于任何区域
  + 区域的命名会影响到网格线。每个区域的起始网格线，会自动命名为`区域名-start`，终止网格线自动命名为`区域名-end`

+ `grid-auto-flow`**属性**，划分网格以后，容器的子元素会按照顺序，自动放置在每一个网格。默认的放置顺序是"先行后列"，其默认值为`row`，可以将其改为`column`，`row dense`和`column dense`后面的`dense`表示紧密排列不出现空格

+ **`justify-items` 属性， `align-items` 属性**：

  `justify-items`属性设置单元格内容的水平位置（左中右），`align-items`属性设置单元格内容的垂直位置（上中下）

  + start：对齐单元格的起始边缘。
  + end：对齐单元格的结束边缘。
  + center：单元格内部居中。
  + stretch：拉伸，占满单元格的整个宽度（默认值）

  **注**：`place-items`属性是`align-items`属性和`justify-items`属性的合并简写形式

+ **`justify-content`属性，`align-content`属性**：

  `justify-content`属性是整个内容区域在容器里面的水平位置（左中右），`align-content`属性是整个内容区域的垂直位置（上中下）

  + start - 对齐容器的起始边框
  + end - 对齐容器的结束边框
  + center - 容器内部居中
  + stretch - 项目大小没有指定时，拉伸占据整个网格容器
  + space-around - 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与容器边框的间隔大一倍
  + space-between - 项目与项目的间隔相等，项目与容器边框之间没有间隔
  + space-evenly - 项目与项目的间隔相等，项目与容器边框之间也是同样长度的间隔

  **注：**`place-content`属性是`align-content`属性和`justify-content`属性的合并简写形式

+ **grid-auto-columns 属性， grid-auto-rows 属性**

  用来设置，浏览器自动创建的多余网格的列宽和行高。它们的写法与`grid-template-columns`和`grid-template-rows`完全相同。如果不指定这两个属性，浏览器完全根据单元格内容的大小，决定新增网格的列宽和行高

### 3、项目属性

+ 项目的位置是可以指定的，具体方法就是指定项目的四个边框，分别定位在哪根网格线：

  + `grid-column-start`属性：左边框所在的垂直网格线
  + `grid-column-end`属性：右边框所在的垂直网格线
  + `grid-row-start`属性：上边框所在的水平网格线
  + `grid-row-end`属性：下边框所在的水平网格线

+ **注**：这四个属性的值还可以使用`span`关键字，表示"跨越"，即左右边框（上下边框）之间跨越多少个网格

+ **grid-column、grid-row属性**：

  `grid-column`属性是`grid-column-start`和`grid-column-end`的合并简写形式，`grid-row`属性是`grid-row-start`属性和`grid-row-end`的合并简写形式，

  简写形式为：`grid-column: 1 / 2 //表示第一列的网格线为左边框，第二列的网格线为右边框`

+ **grid-area属性**：

  `grid-area`属性指定项目放在哪一个区域

+ **justify-self 属性， align-self 属性， place-self 属性**：

  `justify-self`属性设置单元格内容的水平位置（左中右），跟`justify-items`属性的用法完全一致，但只作用于单个项目。

  `align-self`属性设置单元格内容的垂直位置（上中下），跟`align-items`属性的用法完全一致，也是只作用于单个项目

  + start：对齐单元格的起始边缘。
  + end：对齐单元格的结束边缘。
  + center：单元格内部居中。
  + stretch：拉伸，占满单元格的整个宽度（默认值）

  `place-self`属性是`align-self`属性和`justify-self`属性的合并简写形式

## BFC

### 1、概念

+ BFC 是 Blcok Formatting Context（块级格式上下文），可以理解成元素的一个“特异功能”
+ 该“特异功能”，在默认情况下处于关闭状态，当元素满足了某些条件后，该“特异功能”被激活
+ 所谓激活“特异功能”，专业点说就是：该元素创建了BFC

### 2、开启BFC能解决什么问题

+ 其子元素不会再产生margin塌陷问题
+ 自己不会被其他浮动元素所覆盖
+ 就算其子元素浮动，元素自身高度也不会塌陷

### 3、如何开启BFC

+ 根元素
+ 浮动元素
+ 绝对定位、固定定位的元素
+ 行内块元素
+ 表格单元格：table、thead、tbody、th、td、tr、caption
+ overflow 的值不为 visible的块元素
+ 伸缩项目
+ 多列容器
+ column-span为 all 的元素
+ display 的值， 设置为 flow-root

# 选择器

------

选择器：选取需要设置样式的元素的模式，可以分为五类：

+ 简单选择器（根据名称、id、类来选取元素）
+ 组合器选择器（根据它们之间的特定关系来选取元素）
+ 伪类选择器（根据特定状态选取元素）
+ 伪元素选择器（选取元素的一部分并设置其样式）
+ 属性选择器（根据属性或属性值来选取元素）

==选择器权重计算方式：==

1、 每个选择器，都可计算出一组权重，格式为（a,b,c）

a:ID选择器的个数

b:类、伪类、属性选择器的个数

c: 元素、伪元素选择器的个数

2、比较规则：按照从左到右，一次比较大小，当前为胜出后，后面的不再对比

例如：（1，0，0）>（0，2，2）

3、特殊规则：

行内样式权重大于所有选择器

!important的权重大于行内样式，大于所有选择器，权重最高

## 简单选择器

#### ID选择器

+ 根据元素的id属性值，来精准的选中某个元素

  **语法**：

  ~~~css
  #id值 {
  	属性名：属性值；
  }
  ~~~

  注：

  + id属性值：尽量由字母、数字、下划线、短杠组成，不要包含空格

  + 一个元素只能拥有一个id属性，多个元素的id属性值不能相同

  + 一个元素可以拥有id和class属性

#### 类选择器

+ 根据元素的class值，来选中某些元素,**使用频率最高**

  **语法**：

  ~~~css  
  .类名{
      属性名：属性值；
  }
  ~~~

  注：

  + 元素的class属性不带**”.“** , 但CSS的类选择器要带**”.“**

  + 一个元素不能写多个class属性，下面为错误示例： 

    ~~~CSS
    <h1 class='speak' class='big'>你好啊</h1>
    ~~~

  + 一个元素的class属性能写多个值，要用空格隔开，例如：

    ~~~css
    <h1 class="speak big">你好啊</h1>
    ~~~

#### 元素选择器

+ 为页面中某种元素设置样式

  **语法：**

  ~~~css
  标签名 {
      属性名： 属性值;
  }
  ~~~

  注：

  + 元素选择器无法实现差异化设置

#### 通配选择器

+ 可以选中所有的HTML元素

  **语法：**

  ~~~css
  * {
      属性名： 属性值；
  }
  ~~~

  注： 

  + 在清除样式时由很大的帮助

## 组合选择器

####  交集选择器

+ 选中同时符合多个条件的元素

  **语法：**

  ~~~css
  选择器1选择器2....{}
  p.beauty{
      color: blue;
  }
  .rich.beauty{
      color: green;
  }
  ~~~

  注：

  + 有标签名，标签名必须写在前面
  
  + 交集选择器中不可能出现两个元素选择器
  
#### 并集选择器

  + 选中多个选择器对应的元素，又称：分组选择器。
  
    **语法：**
  
    ~~~css
    选择器1，选择器2.。。选择器n{
        
    }  //多个选择器通过“,“连接
    //例如：
    #peiqi,
    .rich,
    .beauty{
    	font-size: 40px;
        background-color: skyblu;
        width: 200px;
    }
    ~~~
  
    注：
  
    + 并集选择器我们一般竖着写
    + 任何形式的选择器都可以作为并集选择器的一部分
    + 并集选择器通常用于集体声明，可以缩小样式表体积。

#### 后代选择器

  + 选中指定元素中，符合要求的==后代元素==
  
    语法：选择器1 选择器2 ..... 选择器n {}（先写祖先，再写后代），选择器之间用空格隔开。
  
    ~~~css
    ul li {
        color: red;
    }
    ul li a {
        color: orange;
    }
    .subject li {
    	color: blue;
    }
    .subject li.front-end {
        color: yellow;
    }
    ~~~
  
    注：
  
    + 后代选择器，最终选择的是后代，不选中祖先
    + 儿子、孙子、重孙子都算是后代
    + 结构一定要符合HTML嵌套要求。

#### 子代选择器

  + 选中指定元素中，符合要求的子元素（==儿子元素==）
  
    语法：选择器1>选择器2>.....选择器 n{}
  
    ~~~css 
    div>a {
        color: red;
    }
    .persons>a {
        color: red;
    }
    ~~~

#### 兄弟选择器

  +  相邻兄弟选择器：选中指定元素后，符合条件的相邻兄弟元素。（==所谓相邻就是紧挨着他的下一个，只往下找第一个元素==）
  
    语法：选择器1+选择器2{ }
  
    ~~~css
    div+p{
        color: red;
    }
    ~~~
  
  + 通用兄弟选择器：选中指定元素后，符合条件的所有兄弟元素
  
    语法：选择器1~选择器2 { }
  
    ~~~css
    div~p {
        color： red;
    }
    ~~~
  
    注：两种兄弟选择器选择的是下面的兄弟

  #### 属性选择器

  + 选中属性值符合一定要求的元素
  
    语法：
  
    + [属性名]选中具有某个属性的元素
    + [属性名="值"]选中包含某个属性，且属性值等于指定的元素
    + [属性名^='值']选中包含某个属性，且属性值以指定的值开头的元素
    + [属性名$='值']选中包含某个属性，且属性值以指定的值结尾的元素
    + [属性名*='值']选择包含某个属性，属性值包含指定值的元素
    
    ~~~css
    [title] { color:red;}
    [title="atguigu"]{color:red;}
    [title^="a"]{color:red;}
    [title$="u"]{color: red;}
    [title*="g"]{color:red;}
    ~~~

  ## 伪类选择器

  选中特殊状态的元素

  ### :root 选择器

  该选择器匹配文档根元素，在HTML中，根元素始终是html

  ### :nth-child(n) 

  用于匹配属于其父元素的第N个子元素，不论元素类型。==注：n可以是数字、关键字或公式==

  ```css
  p:nth-child(3n+0) {
      background: #ff0000;
  }
  /*使用公式 (an + b)。描述：表示周期的长度，n 是计数器（从 0 开始），b 是偏移值。在这里，我们指定了下标是 3 的倍数的所有 p 元素的背景色：*/
  ```

#### 动态伪类

  + :link 超链接==未被访问的状态==
  + :visited 超链接==访问过==的状态
  + :hover 鼠标==悬停==在元素上的状态
  + :active 元素==激活==的状态（激活指按下鼠标不松开）
  + :focus 获取焦点的元素 (表单类才能使用:focus伪类)

  注：遵循**LVHA**顺序即：link, visited, hover, active

  #### 结构伪类

  常用的：

  + :first-child 所有兄弟元素中的第一个
  
  + :last-child 所有兄弟元素中的最后一个
  
  + :nth-child(n) 所有兄弟元素中的第n个
  
  + :first-of-type 所有同类型兄弟元素中的第一个
  
  + :last-of-type 所有同类型兄弟元素中的最后一个
  
  + :nth-of-type(n) 所有同类型兄弟元素中的第n个
  
    关于n的值：
  
    + 0或不写：什么都选不中--几乎不用
    + n:选中所有子元素--几乎不用
    + 1~正无穷的整数：选中对应序号的子元素
    + 2n或even：选中序号为偶数的子元素
    + 2n+1或odd：选中序号为奇数的子元素
    + -n+3：选中的是前3个

  了解即可：

  + :nth-last-child(n) 所有兄弟元素中的倒数第n个
  + :nth-last-of-type(n) 所有同类型兴地元素中的倒数第n个
  + :only-child 选择==没有兄弟==的元素
  + :only-of-type 选择==没有同类型兄弟==的元素
  + :root 根元素
  + :empty 内容为空元素（空格也算内容）

  ###### 否定伪类

  + :not(选择器) 排除满足括号中条件的元素

  ##### UI伪类

  + :checked 被选中的复选框或单选按钮
  + :enable 可用的表单元素(没有disabled属性)
  + :disabled 不可用的表单元素（有disabled属性）

  ##### 目标伪类（了解）

  + :target 选中锚点指向的元素

  ##### 语言伪类

  + :lang() 根据指定的语言选择元素（本质是看lang属性的值）

## 伪元素选择器

伪元素：用于设置元素指定部分的样式，例如：可以用于设置元素的首字母、首行的样式或在元素的内容之前或之后插入内容

##### ::before、::after

在指定元素之前或之后插入新内容。例：

```css
h1::before {
    content: url(smiley.gif);
}
/*在每个<h1>元素的内容之前插入一幅图像*/
```

##### ::first-letter：选中元素中的一个文字

##### ::first-line：选中元素中的第一行文字

##### ::selection：选中被鼠标选中的内容

##### ::placeholder：选中输入框的提示文字



# 函数

---

### **var()**：

用于插入自定义的属性值，如果一个属性值在多处被使用，该方法就很有用。例如：

```css
:root {
    --main-bg-color: coral;
}
#div1 {
    background-color: var(--main-bg-color);
}
```









 
