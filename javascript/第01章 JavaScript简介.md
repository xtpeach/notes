# 第1章 JavaScript简介
    JavaScript诞生于1995年。当时，它的主要目的是处理以前由服务器端语言（如Perl）负责的一些输入验证操作。在JavaScript问世之前，必须把表单数据发送到服务器才能确定用户是否没有填写某个必填域，是否输入了无效的值。Netscape Navigator希望通过JavaScript来解决这个问题。在人们普遍使用电话拨号上网的年代，能够在客户端完成一些基本的验证任务绝对是令人兴奋的。毕竟，拨号上网的速度之慢，导致了与服务器的每一次数据交换，都成了对人们耐心的一次考验。
    
    自此以后，JavaScript逐渐成为市面上常见浏览器必备的一项特色功能。如今，JavaScript的用途早已不再局限于简单的数据验证，而是具备了与浏览器窗口及其内容等几乎所有方面交互的能力。今天的JavaScript已经成为一门功能全面的编程语言，能够处理复杂的计算和交互，拥有了闭包、匿名（lamda，拉姆达）函数，甚至元编程等特性。作为Web的一个重要组成部分，JavaScript的重要性是不言而喻的，就连手机浏览器，甚至那些转为残障人士设计的浏览器等非常规浏览器都支持它。当然，微软的例子更为典型。虽然有自己的客户端脚本语言VBScript，但微软仍然在Internet Explorer的早期版本中加入了自己的JavaScript实现。
    *（对IE而言，当我们提到JavaScript时，实际上就是指IE对JavaScript（ECMAScript）的时限——JScript。最早的JScript基于Netscape JavaScript1.0开发，于1996年8月随同Internet Explorer3.0发布。）
    JavaScript从一个简单的输入验证器发展成为一门强大的编程语言，完全出乎人们的意料。应该说，它既是一门非常简单的语言，又是一门非常复杂的语言。说它简单，是因为学会使用它只需要片刻功夫；而说它复杂，是因为要真正掌握它则需要数年时间。要向全面理解和掌握JavaScript，关键在于弄清楚它的本质、历史和局限性。

## 1.1 JavaScript简史

    在Web日益流行的同时，人们对客户端脚本语言的需求也越来越强烈。那个时候，绝大多数因特网用户都使用速度仅为28.8kbit/s的“猫”（调制解调器）上网，但网页的大小和复杂性却不断增加。为完成简单的表单验证而频繁地与服务器交换数据只会加重用户的负担。想象一下：用户填写完成一个表单，单击“提交”按钮，然后等待30秒钟，最终服务器返回消息说有一个必填字段没有填好……当时走在技术革新最前沿的Netscape公司，决定着手开发一种客户端语言，用来处理这种简单的验证。
    
    当时就职于Netscape公司的布兰登·艾奇（Brendan Eich），开始着手为计划于1995年2月发布的Netscape Navigator2开发一种名为LiveScript的脚本语言——该语言将同时在浏览器和服务器中使用（它在服务器上的名字叫LiveWire）。为了赶在发布日期前完成LiveScript的开发，Netscape与Sun公司建立了一个开发联盟。在Netscape Navigator2正式发布前夕，Netscape为了搭上媒体热炒Java的顺风车，临时把LiveScript改名为JavaScript。
    
    由于JavaScript1.0获得了巨大成功，Netscape随即在Netscape Navigator3中又发布了JavaScript1.1。

## 1.2 JavaScript实现

### 1.2.1 ECMAScript