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

ECMAScript的不同版本又称为版次，以第x版表示（意即描述特定实现的ECMA-262规范的第x个版本）。ECMA-262的最近一版是第5版，发布于2009年。而ECMA-262的第1版本质上与Netscape的JavaScript1.1相同——只不过删除了所有针对浏览器的代码并作了一些较小的改动：ECMA-262要求支持Unicode标准（从而支持多语言开发），而且对象也变成了平台无关的（Netscape JavaScript1.1的对象在不同平台中的实现不一样，例如Date对象）。这也是JavaScript1.1和1.2与ECMA-262第1版不一致的主要原因。

ECMA-262第2版主要是编辑加工的结果。这一版中内容的更新是为了与ISO/IEC-16262保持严格一致，没有做任何新增、修改或删节处理。因此，一般不使用第2版来衡量ECMAScript实现的兼容性。

ECMA-262第3版才是对该标准第一次真正的修改。修改的内容涉及字符串处理、错误定义和数值输出。这一版还新增了对正则表达式、新控制语句、try-catch异常处理的支持，并围绕标准的国际化做出了一些小的修改。从各方面综合来看，第3版标志着ECMAScript成为了一门真正的变成语言。

ECMA-262第4版对这门语言进行了一次全面的检核修订。由于JavaScript在Web上日益流行，开发人员纷纷建议修订ECMAScript，以使其能够满足不断增长的Web开发需求。作为回应，ECMA TC39重新召集相关人员共同谋划这门语言的未来。结果，出台后的标准几乎在第3版基础上完全定义了一门新语言。第4版不仅包含了强类型变量、新语句和新数据结构、真正的类和经典继承，还定义了与数据交互的新方式。

与此同时，TC39下属的一个小组也提出了一个名为ECMAScript3.1的替代性建议，该建议只对这门语言进行较少的改进。这个小组认为第4版给这门语言带来的跨越太大了。因此，该小组建议对这门语言进行小幅修改，能够在现有JavaScript引擎基础上实现。最终，ES3.1附属委员会获得的支持超过了TC39，ECMA-262第4版在证书发布前被放弃。

ECMAScript3.1称为ECMA-262第5版，并于2009年12月3日正式发布。第5版力求澄清第3版本中已知的歧义并添加了新的功能。新功能包括原生JSON对象（用于解析和序列化JSON数据）、继承的方法和高级属性定义，另外还包含一种严格模式，对ECMAScript引擎解释和执行代码进行了补充说明。

#### 2.什么是ECMAScript兼容

ECMA-262给出了ECMAScript兼容的定义。要想称为ECMAScript的实现，则该实现必须做到：
1. 支持ECMA-262描述的所有“类型、值、对象、属性、函数以及程序句法和语义”；
2. 支持Unicode字符标准；
3. 添加ECMA-262没有描述的“更多类型、值、对象、属性和函数”。ECMA-262所说的这些新增特性，主要是指标准中没有规定的新对象和对象的新属性。
4. 支持ECMA-262没有定义的“程序和正则表达式语法”。（也就是说，可以修改和扩展内置的正则表达式语法。）

上述要求为兼容实现的开发人员基于ECMAScript开发一门新语言提供了广阔的空间和极大的灵活性，这也从另一个侧面说明了ECMAScript受开发人员欢迎的原因。

#### 3.Web浏览器对ECMAScript的支持

1996年，Netscape Navigator3捆绑发布了JavaScript1.1。而相同的JavaScript1.1设计规范随后作为对新标准（ECMA-262）的建议被提交给Ecma。伴随着JavaScript的迅速走红，Netscape豪情满怀地着手开发JavaScript1.2。然而，问题是Ecma当时还没有接受Netscape的建议。

Netscape Navigator3发布后不久，微软也推出了Internet Explorer3。微软在IE的这一版中捆绑了JScript1.0，很多人都认为JScript1.0与JavaScript1.1应该是一样的。但是，由于没有文档依据，加之不适当的特性模仿，JScript1.0还是很难与JavaScript1.1相提并论。

1997年，内置JavaScript1.2的Netscape Navigator4发布；而到这一年年底，ECMA-262第1版也被接受并实现了标准化。结果，虽然ECMAScript被认为是基于JavaScript1.1制定的，但JavaScript1.2与ECMAScript的第1版并不兼容。

JScript的升级版是Internet Explorer4中内置的JScript3.0（随同微软IIS3.0发布的JScript2.0从来也没有移植到浏览器中）。微软通过媒体大肆宣传JScript3.0是世界上第一个ECMA兼容的脚本语言，但当时的ECMA-262尚未定稿。于是，JScript3.0与JavaScript1.2都遭遇了相同的尴尬局面——谁都没有按照最终的ECMAScript标准来实现。

Netscape决定要更新其JavaScript实现，即在Netscape Navigator4.06中发布JavaScript1.3，从而做到了与ECMA-262的第一个版本完全兼容。在JavaScript1.3中，Netscape增加了对Unicode标准的支持，并在保留JavaScript1.2新增特性的同时实现了所有对象的平台中立化。

在Netscape以Mozilla项目的名义开放其源代码时，预期JavaScript1.4将随同Netscape Navigator5一道发布。然而，一个激进的决定，彻底重新设计Netscape代码，打乱了原有计划。后来，JavaScript1.4只发布了针对Netscape Enterprise Server的服务器版，而没有内置于Web浏览器中。

到了2008年，五大主流Web浏览器（IE、Firefox、Safari、Chrome和Opera）全部做到了与ECMA-262兼容。IE8是第一个着手实现ECMA-262第5版的浏览器，并在IE9中提供了完整的支持。Firefox4也紧随其后做到兼容。下表列出了ECMAScript受主流Web浏览器支持的情况。

### 1.2.2 文档对象模型（DOM）

文档对象模型（DOM，Document Object Model）是针对XML但经过扩展用于HTML的应用程序编程接口（API，Application Programming Interface）。DOM 把整个页面映射为一个多层节点结构。HTML 或 XML页面中的每个组成部分都是某种类型的节点，这些节点又包含着不同类型的数据。看下面这个HTML页面：

```html
    <html>
        <head>
            <title>Sample Page</title>
        </head>
        <body>
            <p>Hello World!</p>
        </body>
    </html>
```

在浏览器开发者调试工具中，我们可以清楚看到其分层节点结构。

通过DOM创建的这个表示文档的树形图，开发人员获得了控制页面内容和结构的主动权。借助DOM提供的API，开发人员可以轻松自如地删除、添加、替换或修改任何节点。

### 1.2.3 浏览器对象模型（BOM）

BOM, Browser Object Model。

开发人员使用BOM可以控制浏览器显示的页面以外的部分。而BOM真正与众不同的地方（也是经常导致问题的地方），还是它作为JavaScript实现的一部分但却没有相关的标准。这个问题在HTML5中得到了解决，HTML5致力于把很多BOM功能写入正式规范。HTML5发布后，很多关于BOM的困惑烟消云散。

从根本上讲，BOM只处理浏览器窗口和框架；但人们习惯上也把所有针对浏览器的JavaScript扩展算作BOM的一部分。下面就是一些这样的扩展：

1. 弹出新浏览器窗口的功能；
2. 移动、缩放和关闭浏览器窗口的功能；
3. 提供浏览器详细信息的navigator对象；
4. 提供浏览器所加载页面的详细信息的location对象；
5. 提供用户显示器分辨率详细信息的screen对象；
6. 对cookies的支持；
7. 像XMLHttpRequest和IE的ActiveXObject这样的自定义对象。

由于没有BOM标准可以遵循，因此每个浏览器都有自己的实现。虽然也存在一些事实标准，例如要有window对象和navigator对象等，但每个浏览器都会为这两个对象乃至其他对象定义自己的属性和方法。现在有了HTML5，BOM实现的细节有望朝着兼容性越来越高的方向发展。

### 1.3 JavaScript版本