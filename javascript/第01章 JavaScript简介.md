# 第1章 JavaScript简介

JavaScript诞生于1995年。当时，它的主要目的是处理以前由服务器端语言（如Perl）负责的一些输入验证操作。在JavaScript问世之前，必须把表单数据发送到服务器才能确定用户是否没有填写某个必填域，是否输入了无效的值。Netscape Navigator希望通过JavaScript来解决这个问题。在人们普遍使用电话拨号上网的年代，能够在客户端完成一些基本的验证任务绝对是令人兴奋的。毕竟，拨号上网的速度之慢，导致了与服务器的每一次数据交换，都成了对人们耐心的一次考验。
    
自此以后，JavaScript逐渐成为市面上常见浏览器必备的一项特色功能。如今，JavaScript的用途早已不再局限于简单的数据验证，而是具备了与浏览器窗口及其内容等几乎所有方面交互的能力。今天的JavaScript已经成为一门功能全面的编程语言，能够处理复杂的计算和交互，拥有了闭包、匿名（lamda，拉姆达）函数，甚至元编程等特性。作为Web的一个重要组成部分，JavaScript的重要性是不言而喻的，就连手机浏览器，甚至那些转为残障人士设计的浏览器等非常规浏览器都支持它。当然，微软的例子更为典型。虽然有自己的客户端脚本语言VBScript，但微软仍然在Internet Explorer的早期版本中加入了自己的JavaScript实现。
*（对IE而言，当我们提到JavaScript时，实际上就是指IE对JavaScript（ECMAScript）的时限——JScript。最早的JScript基于Netscape JavaScript1.0开发，于1996年8月随同Internet Explorer3.0发布。）

JavaScript从一个简单的输入验证器发展成为一门强大的编程语言，完全出乎人们的意料。应该说，它既是一门非常简单的语言，又是一门非常复杂的语言。说它简单，是因为学会使用它只需要片刻功夫；而说它复杂，是因为要真正掌握它则需要数年时间。要向全面理解和掌握JavaScript，关键在于弄清楚它的本质、历史和局限性。

## 1.1 JavaScript简史

在Web日益流行的同时，人们对客户端脚本语言的需求也越来越强烈。那个时候，绝大多数因特网用户都使用速度仅为28.8kbit/s的“猫”（调制解调器）上网，但网页的大小和复杂性却不断增加。为完成简单的表单验证而频繁地与服务器交换数据只会加重用户的负担。想象一下：用户填写完成一个表单，单击“提交”按钮，然后等待30秒钟，最终服务器返回消息说有一个必填字段没有填好……当时走在技术革新最前沿的Netscape公司，决定着手开发一种客户端语言，用来处理这种简单的验证。
    
当时就职于Netscape公司的布兰登·艾奇（Brendan Eich），开始着手为计划于1995年2月发布的Netscape Navigator2开发一种名为LiveScript的脚本语言——该语言将同时在浏览器和服务器中使用（它在服务器上的名字叫LiveWire）。为了赶在发布日期前完成LiveScript的开发，Netscape与Sun公司建立了一个开发联盟。在Netscape Navigator2正式发布前夕，Netscape为了搭上媒体热炒Java的顺风车，临时把LiveScript改名为JavaScript。
    
由于JavaScript1.0获得了巨大成功，Netscape随即在Netscape Navigator3中又发布了JavaScript1.1。Web虽然羽翼未丰，但用户关注度却屡创新高。在这样的背景下，Netscape把自己定位为市场领袖型 公司。与此同时，微软决定向与Navigator竞争的自家产品Internet Explorer浏览器投入更多资源。Netscape Navigator3发布后不久，微软就在其Internet Explorer3中加入了名为JScript的JavaScript实现（命名为JScript是为了避开与Netscape有关的授权问题）。以现在的眼光看，微软在1996年8月为进入Web浏览器领域而实施的这个重大举措，是导致Netscape日后蒙羞的一个标志性事件。然而，这个重大举措同时也标志着JavaScript作为一门语言，其开发向前买进了一大步。

微软推出其JavaScript实现意味着有了两个不同的JavaScript版本：Netscape Navigator中的JavaScript、Internet Explorer中的JScript。与C及其他编程语言不同，当时还没有标准规定JavaScript的语法和特性，两个不同版本并存的局面已经完全暴露了这个问题。随着业界担心的日益加剧，JavaScript的标准化问题被提上议事日程。

1997年，以JavaScript1.1为蓝本的建议被提交给了欧洲计算机制造商协会（ECMA，European Computer Manufacturers Association）。该协会指定39号技术委员会（TC39，Technical Committee #39）负责“标准化一种通用、跨平台、供应商中立的脚本语言的语法和语义”。TC39由来自Netscape、Sun、微软、Borland及其他关注脚本语言发展的公司的程序员组成，他们经过数月的努力完成了ECMA-262——定义一种名为ECMAScript（发音为“ek-ma-script”）的新脚本语言的标准。

第二年，ISO/IEC（International Organization for Standardization and International Electrotechnical Commission，国标标准化组织和国际电工委员会）也采用了ECMAScript作为标准（即ISO/IEC-16262）。自此以后，浏览器开发商就开始致力于将ECMAScript作为各自JavaScript实现的基础，也在不同程度上取得了成功。

## 1.2 JavaScript实现

虽然JavaScript和ECMAScript通常都被人们用来表达相同的含义，但JavaScript的含义却比ECMA-262中规定的要多得多。没错，一个完整的JavaScript实现应该由下列三个不同的部分组成。（ECMAScript、DOM、BOM）
1. 核心（ECMAScript）
2. 文档对象模型（DOM）
3. 浏览器对象模型（BOM）

### 1.2.1 ECMAScript

由ECMA-262定义的ECMAScript与Web浏览器没有依赖关系。实际上，这门语言本身并不包含输入和输出定义。ECMA-262定义的只是这门语言的基础，而在此基础之上可以构建更完善的脚本语言。我们常见的Web浏览器只是ECMAScript实现可能的宿主环境之一。宿主环境不仅提供基本的ECMAScript实现，同时也提供该语言的扩展，以便语言与环境之间对接交互。而这些扩展——如DOM，则利用ECMAScript的核心类型和语法提供更多具体的功能，以便实现针对环境的操作。其他宿主环境包括Node（一种服务端JavaScript平台）和Adobe Flash。

既然ECMA-262标准没有参照Web浏览器，那它规定了些什么内容呢？大致说来，它规定了这门语言的下列组成部分：
1. 语法
2. 类型
3. 语句
4. 关键字
5. 保留字
6. 操作符
7. 对象

ECMAScript就是对实现该标准规定的各个方面内容的语言的描述。JavaScript实现了ECMAScript，Adobe ActionScript同样也实现了ECMAScript。

#### 1.ECMAScript的版本

ECMAScript的不同版本又称为版次，以第x版表示（意即描述特定实现的ECMA-262规范的第x个版本）。ECMA-262的最近一版是第5版，发布于2009年。而ECMA-262的第1版本质上与Netscape的JavaScript1.1相同——只不过删除了所有针对浏览器的代码并作了一些较小的改动：ECMA-262