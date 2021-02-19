---
layout: post
title:  "Simple Method That Will Make Our Code Cleaner"
date:   2021-02-19 20:37:00 +0700
categories: clean code
---

Today, I want to share about how i make my code cleaner with simple method.
This technique is about to make project more easier to maintain.
And the technique is

`Don't directly assign the variable with value`

Yes, assigning or changing the variable directly is bad in my opinion, especially in `Object Oriented Programming` world. Here is why.

First, imagine we have `Product` model in our application.
Let say Product model like this.

{% highlight python %}
# illustration written using python
class Product:
    def __init__(self):
        self.id
        self.name
        self.price
{% endhighlight %}

and we may instantiate the model like this.

{% highlight python %}
product = Product()
{% endhighlight %}

and sometimes we need to change value attribute of our model like this.

{% highlight python %}
product = Product()
product.name = "Dummy"
{% endhighlight %}

Imagine we have large scale application that need to change property value like the code above in many place. And after that in the future we need to reformat the value before we assign the value to variable.
let say we have 100 line of code that assign value of `product.name`. It will take a few hour to change the format one by one.

It also hard to debug if there is an error in application that return `product.name` with the wrong name. We need a few hour to search what line of code that change the value.

and This is the solution to make the code more easier to maintain by using.

`Method or function to change the value of properties`

So our model will become like this.

{% highlight python %}
class Product:
    def __init__(self):
        self.id
        self.name
        self.price

    def setId(self, id):
        self.id = id

    def setName(self, name):
        self.name = name

    def setPrice(self, price):
        self.price = price
{% endhighlight %}

If we want to reformat the value assigned to the property, we can update the `setName` method like this:

{% highlight python %}
    def setName(self, name):
        self.name = 'The' + name
{% endhighlight %}

Instead of formatting the value one by one, just reformat the value directly from the method.

And if we had an error in our application. We can trace that problem by adding breakpoint in our `setName` method.

In Visual Studio Code, you can trace where is the caller of our method. So we can directly know what cause an error.

And thats all my opinion to make our code more cleaner.

Thank you.