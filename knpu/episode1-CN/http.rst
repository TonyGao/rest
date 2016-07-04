HTTP 基础
===========

是的 我们需要一些理论知识。等等，回来！这里的知识超重要，但同样吸引人。集中精力，我们投入其中。

HTTP
----

一切都从HTTP开始：这几个缩写字母描述的是一个客户端请求信息并从服务器返回信息的格式。如果你认为API就像一个功能，
request就像输入，response就像输出，很简单的道理。

HTTP 请求
~~~~~~~~~~~~

.. code-block:: text

    GET /api/programmers HTTP/1.1
    Host: CodeBattles.io
    Accept: application/json,text/html

这是基础的请求，它包含3个重要部分：

1. ``/api/programmers`` 是URI: uniform resource identifier. 这里提到了
   **resource**! 每个URI都是一个资源唯一的地址，就像你的房子只有一个唯一的住址一样。
   如果你有5个URI，那就意味着5个资源。

2. ``GET`` 是HTTP方法，用来描述你想通过什么动作来操作资源。你应该已经知道GET和POST了，还有其他类似DELETE, 
PUT和臭名昭著的PATCH. 还有一些其他的，估计你也就不感兴趣了。

3. 头信息里第一行后的每一行都是冒号分隔的列表。这个请求只有两行，但客户端可以发送任何信息。

With that in mind, a POST request might look like this:

心里想着这些，一个POST请求可能长这样：

.. include:: includes/_post_programmer.rst.inc

It's the same, except the method is POST and we're sending data in the body
of the request. We also have 2 extra headers, one for authentication and
one that tells the server that the body has JSON-formatted stuff in it.

这是一样的，除了方法使用了POST，我们从这次请求的body正在发送数据。我们还有两个额外的头信息，
一个是作者，一个告诉服务器body里有JSON格式的信息。

HTTP Response
~~~~~~~~~~~~~

HTTP 响应
~~~~~~~~~~~~~

The response message is similar:

返回信息类似：

.. code-block:: text

    HTTP/1.1 200 OK
    Content-Type: application/json
    Cache-Control: no-cache, private

    {
        "nickname": "Namespacinator",
        "avatarNumber": 5,
        "tagLine": "",
        "powerLevel": 25
    }

The 200 status code is the first important piece, and of course means that
everything went just great. Status codes are a *big* part of APIs. But people
also like to argue about them. We'll see the important ones as we build.

The headers tell the client that the response is JSON and that the response
shouldn't be cached. And of course, the JSON body is at the end.

HTTP is awesome and really simple. Got it? Great, let's move onto something
harder.

这个状态代码200是第一个重要的部分，意思是一切都运转正常。状态编码是API的重要部分。
同时也是人们争论的焦点。我们将看到我们是怎么创建这个重要部分的。

头信息告诉客户端返回的是JSON，返回结果不应该被缓存。当然JSON的主体在末尾。

HTTP非常赞，而且真的很简单。学会了吗？好，咱们开始些更难的。
