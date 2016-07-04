REST: Resources and Representations
===================================

REST: Representational state transfer. The term was coined famously by `Roy Fielding`_
in his doctoral dissertation in 2000. It's complex, and a lot of what makes
a REST API hard is understanding and debating the many rules, or constraints
laid out in his document.

When you think about an API, it's pretty common to think about its endpoints,
in other words the URLs. With REST, if you have a URL, then you have
a resource. So, ``/programmers/Namespacinator`` is probably the address to
a single programmer resource and ``/programmers`` is probably the address
to a collection resource of programmers. So even a collection of programmers
is considered one resource.

But we already build URLs that work like this on the web, so this is nothing
new.

Representations
---------------

Now that you understand resources, I want to think about representations.
Suppose a client makes a GET request to ``/programmers/Namespacinator`` and
gets back this JSON response:

REST: 资源和表述
================

REST: Representational state transfer(表述性状态转移)。 这个著名术语是2000年由Roy Fielding在他的博士学位论文里创造的。论文很复杂，使得REST API难以实现的原因是需要理解和讨论很多规则，
论文中限定了很多设计。

当你提到API, 通常会想到它的终点，也就是URLs。 在REST里，如果你有一个URL，那么你就等于有一个资源。
因此， ``/programmers/Namespacinator`` 或许就是指向单一程序员的地址，
``/programmers`` 或许就是指向全部程序员的资源集合的地址。所以甚至一个程序员集合也是被视为一个资源。

我们已经在web里创建过URLs了，没啥新鲜东西可说。

表述
---------------

现在已经理解资源了，我想要认知下表述。假设一个客户端做了一个GET请求给 ``/programmers/Namespacinator``，
并取得JSON的返回：

.. code-block:: json

    {
        "nickname": "Namespacinator",
        "powerLevel": 5
    }

That's the programmer resource, right? Wrong! No!

This is just a *representation* of the programmer resource. It happens to
be in JSON, but the server could have represented the programmer in other
ways, like in XML, HTML or even in JSON with a different format.

The same applies when a client sends a request that contains programmer data:

这是程序员资源，对吧？错，不对！

这仅仅是程序员资源的表述。它由JSON来表现，服务器也可以用其他格式来表述程序员，如XML, HTML或者甚至用不同格式的JSON。

当客户端以发送包含程序员数据的方式发送请求时也是同样的：

.. include:: includes/_post_programmer.rst.inc

The client doesn't send a programmer resource, it just sends a representation.
The server's job is to interpret this representation and update the resource.

客户端没发送一个程序员资源，只是发送了一个表述。服务器的任务就是解释这个表述并更新资源。

Representation State
--------------------

This is exactly how browsing the web works. An HTML page is *not* a resource,
it's just one representation. And when we submit a form, we're just sending
a different representation back to the server

One resource could have many representations. Heck, you could get crazy and
have an API where you're able to request the XML, JSON *or* HTML representations
of any resource. We're just crazy enough that we'll do some of that.

A representation is a machine readable explanation of the current state of
a resource.

Yes, I said the current "state" of the resource, and that's another important
and confusing term. What REST calls state, you probably think of as simply
the "data" of a resource. When the client makes a GET request to ``/programmer/Namespacinator``,
the JSON is a representation of its current state, or current data. And if
the client makes a request to update that programmer, the client is said to
be sending a representation in order to update the "state" of the resource.

In REST-speak, a client and server exchange representations of a resource,
which reflect its current state or its desired state. REST, or Representational state
transfer, is a way for two machines to transfer the state of a resource
via representations.

I know I know. We just took an easy idea and made it insane! But if you can
understand *this* way of thinking, a lot of what you read about REST will
start to make sense.

表述状态
--------

确切的说这里其实是在表述web的工作原理。HTML页并不是一个资源，而只是一个表述。我们提交一个表单时，
我们仅仅是发送一个不同的表述给服务器。

一个资源可以有很多表述。我去，你疯了吗，弄一个API，用来将任意请求的资源表述成XML, JSON或HTML。
我们确实够疯狂，就打算这么办。

一个表述是可以让机器读懂的一个资源当前状态的解释说明。

是的，我说资源的当前“状态”，这是另一个很重要但又让人迷惑的术语。 REST里所说的状态，或许你会简单的理解为任意资源的“数据”。 当客户端做了一个GET请求到 /programmer/Namespacinator, 返回的JSON就是它当前状态的一个表述，或者说当前数据。 如果一个客户端做了一个更新程序员的请求，客户端其实就是为了更新一个资源的“状态”而发送了一个表述。

在REST的语言里，客户端和服务器交换资源表述，其反应的就是它们的当前状态或者渴望的状态。REST就是让两台机器通过表述转变资源状态的方法。

明白，我明白，我们把简单的东西复杂化了！但如果你可以理解这种思维方式，你读的大部分关于REST的文章都会变得可以理解。

.. _`Roy Fielding`: https://twitter.com/fielding
