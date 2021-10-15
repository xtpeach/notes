# 第2章 在HTML中使用JavaScript

只要一提到把JavaScript放到网页中，就不得涉及Web的核心语言——HTML。在当初开发JavaScript的时候，Netscape要解决的一个重要问题就是如何做到让JavaScript既能与HTML页面共存，又不影响那些页面在其他浏览器中的呈现效果。经过尝试、纠错和争论，最终的决定就是为Web增加统一的脚本支持。而Web诞生早期的很多做法也都保留了下来，并被正式纳入HTML规范当中。

## 2.1 <script>元素

向HTML页面中插入JavaScript的主要方法，就是使用<script>元素。这个元素由Netscape创造并在Netscape Navigator 2中首先实现。后来这个元素加入到正式的HTML规范中。HTML 4.01为<script>定义了下列6个属性。

>async：可选。表示应该立即下载脚本，但不应妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。只对外部脚本文件有效。
>charset：可选。表示通过src属性指定的代码的字符集。由于大多数浏览器会忽略它的值，因此这个属性很少有人用。
>defer：可选。表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。IE7及更早版本对嵌入脚本也支持这个属性。
>language：已废弃。原来用于表示编写代码使用的脚本语言（如JavaScript、JavaScript1.2或VBScript）。大多数浏览器会忽略这个属性，因此也没有必要在用了。
>src：可选。表示包含要执行代码的外部文件。
>type：可选。可以看成是language的替代属性；表示编写代码使用的脚本语言的内容类型（也成为MIME类型）。虽然text/javascript和text/ecmascript都已经不被推荐使用，但人们一直以来使用的都还是text/javascript。实际上，服务器在传送JavaScript文件时使用的MIME类型通常是application/x-javascript，但在type中设置这个值却可能导致脚本被忽略。另外，在非IE浏览器中还可以使用以下值：application/javascript和application/ecmascript。考虑到约定俗成和最大限度的浏览器兼容性，目前type属性的值依旧还是text/javascript。不过，这个属性并不是必需的，如果没有指定这个属性，则其默认值仍为text/javascript。

使用<script>元素的方式有两种：直接在页面中嵌入JavaScript代码和包含外部JavaScript文件。

在使用<script>元素嵌入JavaScript代码时，只须为<script>指定type属性。然后，像下面这样把JavaScript代码直接放在元素内部即可：

```html
    <script type="text/javascript">
        function sayHi() {
            alert("Hi!");
        }
    </script>
```

包含在<script>元素内部的JavaScript代码将被从上至下依次解释。就拿前面这个例子来说，解释器会解释一个函数的定义，然后将该定义保存在自己的环境当中。在解释器对<script>元素内部的所有代码求值完毕之前，页面中的其余内容都不会被浏览器加载或显示。

在使用<script>嵌入JavaScript代码时，记住不要在代码中的任何地方出现"</script>"字符串。例如，浏览器在加载下面所示的代码时就会产生一个错误：

```html
    <script type="text/javascript">
        function sayHi() {
            alert("</script>");
        }
    </script>
```

因为按照解析嵌入式代码的规则，当浏览器遇到字符串"</script>"时，就会认为那是结束的</script>标签。而通过转义字符“/”可以解决这个问题，例如：

```html
    <script type="text/javascript">
        function sayHi() {
            alert("<\/script>");
        }
    </script>
```

这样写代码浏览器可以接受，因而也就不会导致错误了。

如果要通过<script>元素来包含外部JavaScript文件，那么src属性就是必需的。这个属性的值是一个指向外部JavaScript文件的链接，例如：

```html
    <script type="text/javascript" src="example.js"></script>
```

在这个例子中，外部文件example.js将被加载到当前页面中。外部文件只须包含通常要放在开始的<script>和结束的</script>之间的那些JavaScript代码即可。与解析嵌入式JavaScript代码一样，在解析外部JavaScript文件（包括下载该文件）时，页面的处理也会暂时停止。如果是在XHTML文档中，也可以省略前面示例代码中结束的</script>标签，例如：

```html
    <script type="text/javascript" src="example.js" />
```

但是，不能在HTML文档使用这种语法。原因是这种语法不符合HTML规范，而且也得不到某些浏览器（尤其是IE）的正确解析。

按照惯例，外部JavaScript文件带有.js扩展名。但这个扩展名不是必须的，因为浏览器不会检查包含JavaScript的文件的扩展名。这样一来，使用JSP、PHP或其他服务端语言动态生成JavaScript代码也就成为可能。但是，服务器通常还是需要看扩展名决定为响应应用哪种MIME类型。如果不使用.js扩展名，请确保服务器能返回正确的MIME类型。

需要注意的是，带有src属性的<script>元素不应该在其<script>和</script>标签之间再包含额外的JavaScript代码。如果包含了嵌入的代码，则只会下载并执行外部脚本文件，嵌入的代码会被忽略。

另外，通过<script>元素的src属性还可以包含来自外部域的JavaScript文件。这一点既让<script>元素倍县强大，又让它备受争议。在这一点上，<script>与<img>元素非常相似，即它的src属性可以是指向当前HTML页面所在域之外的某个域中的完整URL，例如：

```html
    <script type="text/javascript" src="http://www.somewhere.com/afile.js"></script>
```

这样，位于外部域中的代码也会被加载和解析，就像这些代码位于加载它们的页面中一样。利用这一点就可以在必要时通过不同的域来提供JavaScript文件。不过，在访问自己不能控制的服务器上的JavaScript文件时则要多加小心。如果不幸遇到了怀有恶意的程序员，那他们随时都可能替换该文件中的代码。因此，如果想包含来自不同域的代码，则要么你是那个域的所有者，要么那个域的所有者值得信赖。

无论如何包含代码，只要不存在defer和async属性，浏览器都会按照<script>元素在页面中出现的先后顺序对它们依次进行解析。换句话说，在第一个<script>元素包含的代码解析完成后，第二个<script>包含的代码才会被解析，然后才是第三个、第四个……

### 2.1.1 标签的位置

按照传统的做法，所有<script>元素都应该放在页面的<head>元素中，例如：

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Example HTML Page</title>
        <script type="text/javascript" src="example1.js"></script>
        <script type="text/javascript" src="example2.js"></script>
    </head>
    <body>
        <!-- 这里放内容 -->
    </body>
</html>
```html

这种做法的目的就是把所有外部文件（包括CSS文件和JavaScript文件）的引用都放在相同的地方。可是，在文档的<head>元素中包含所有JavaScript文件，意味着必须等到全部JavaScript代码都被下载、解析和执行完成以后，才能开始呈现页面的内容（浏览器在遇到<body>标签时才开始呈现内容）。对于那些需要很多JavaScript代码的页面来说，这无疑会导致浏览器在呈现页面时出现明显的延迟，而延迟期间的浏览器窗口中将是一片空白。为了避免这个问题，现代Web应用程序一般都把全部JavaScript引用放在<body>元素中页面内容的后面，如下例所示：

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Example HTML Page</title>
    </head>
    <body>
        <!-- 这里放内容 -->
        <script type="text/javascript" src="example1.js"></script>
        <script type="text/javascript" src="example2.js"></script>
    </body>
</html>
```html

这样，在解析包含的JavaScript代码之前，页面的内容将完全呈现在浏览器中。而用户也会因为浏览器窗口空白页面的时间缩短而感到打开页面的速度加快了。

### 2.1.2 延迟脚本

HTML 4.01为<script>标签定义了defer属性。这个属性的用途是表明脚本在执行时不会影响页面的构造。也就是说，脚本会被延迟到整个页面解析完毕后再运行。因此，在元素<script>中设置defer属性，相当于告诉浏览器立即下载，但延迟执行。

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Example HTML Page</title>
    </head>
    <body>
        <!-- 这里放内容 -->
        <script type="text/javascript" defer="defer" src="example1.js"></script>
        <script type="text/javascript" defer="defer" src="example2.js"></script>
    </body>
</html>
```html





