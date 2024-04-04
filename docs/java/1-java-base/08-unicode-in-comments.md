---
slug: /unicode-in-comments
---

# 8. 什么?注释里面的代码居然能够执行

注释大家都写过，应该都懂。注释就是给人看的，不是给机器看的，自然也就无法执行。

但是今天就有一个例外，快让我们看一下吧。

如果是下面一段代码，大家期望的输出是什么？

~~~java
public class escapesUsage {

    public static void main(String[] args) {
        // \u000d System.out.println("www.flydean.com");
    }
}
~~~

main方法中的System.out.println被注释掉了。我们运行下看：

~~~java
www.flydean.com
~~~

居然输出了结果。为什么呢？ 

我们注意在注释后面，我们添加的是\u000d，这是一个unicode编码，转换成ASCII编码就是换行符。

> 在java中，unicode转换成ASCII是在任何词法翻译之前，所以上面的例子中的unicode会转换成为换行符，最终导致输出结果。

实际上整个java程序都可以使用unicode来编写。

给大家看一个别人写的：

~~~java
\u0070\u0075\u0062\u006c\u0069\u0063\u0020\u0020\u0020\u0020
\u0063\u006c\u0061\u0073\u0073\u0020\u0055\u0067\u006c\u0079
\u007b\u0070\u0075\u0062\u006c\u0069\u0063\u0020\u0020\u0020
\u0020\u0020\u0020\u0020\u0073\u0074\u0061\u0074\u0069\u0063
\u0076\u006f\u0069\u0064\u0020\u006d\u0061\u0069\u006e\u0028
\u0053\u0074\u0072\u0069\u006e\u0067\u005b\u005d\u0020\u0020
\u0020\u0020\u0020\u0020\u0061\u0072\u0067\u0073\u0029\u007b
\u0053\u0079\u0073\u0074\u0065\u006d\u002e\u006f\u0075\u0074
\u002e\u0070\u0072\u0069\u006e\u0074\u006c\u006e\u0028\u0020
\u0022\u0048\u0065\u006c\u006c\u006f\u0020\u0077\u0022\u002b
\u0022\u006f\u0072\u006c\u0064\u0022\u0029\u003b\u007d\u007d
~~~

上面的代码输出”hello world“，不信可以自己去试试。

> 本文作者：flydean程序那些事
> 
> 本文链接：[www.flydean.com](http://www.flydean.com)
> 
> 本文来源：flydean的博客
> 
> 欢迎关注我的公众号:程序那些事，更多精彩等着您！



