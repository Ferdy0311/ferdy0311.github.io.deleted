---
layout: post
title:  "First Time Flask"
date:   2021-02-14 13:43:00 +0700
categories: flask
---

How to run `flask` on your local machine

{% highlight bash %}
# Install venv
$ python3 -m venv venv
{% endhighlight %}

{% highlight bash %}
# Activate venv
$ . venv/bin/activate
{% endhighlight %}

{% highlight bash %}
# Install flask for the first time in activated env
$ pip install Flask
{% endhighlight %}

<!-- {% highlight bash %}
# Deactivate venv
deactivate
{% endhighlight %} -->

{% highlight bash %}
# Export FLASK_APP
$ export FLASK_APP=<APP_NAME>.py
{% endhighlight %}

{% highlight bash %}
# Change FLASK_ENV

# to Development Environment
$ export FLASK_ENV=development

# to Production Environment
$ export FLASK_ENV=production
{% endhighlight %}

{% highlight bash %}
# Run Flask
$ flask run
{% endhighlight %}

{% highlight bash %}
# Run specific host Flask
$ flask run --host=0.0.0.0
{% endhighlight %}

