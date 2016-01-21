---
layout: post
title:  Advanced API modeling with Swagger
---

Building APIs is not easy. Nor is documenting them.

...


You might not feel the need for documentation in a team, where both API and its clients are developed by the same
engineers. However, when it's not the case and different people are working on different platforms, they better have a
centralized communication knowledge which both teams are working against. And this is where API documentation can play a
significant role.

...

We will use the [OpenAPI Specification] (formerly known as Swagger specification).

[OpenAPI Specification]: https://github.com/OAI/OpenAPI-Specification

...

If you're not familiar with JSON Schema yet, I strongly recommend to get started with it. This is essential for working
with Swagger.

...

Starting from version 2.0 of its specification, Swagger allows to use YAML to accompany previously exclusive JSON format
to model the schema. Whether you want to use YAML or JSON - this is purely up to your preference, but let me bring them
both together to help you making the decision.

YAML:

{% highlight yaml %}
swagger: '2.0'
info:
    title: The Cake Factory
    version: 1.0
{% endhighlight %}

JSON:

{% highlight json %}
{
    "swagger": "2.0",
    "info": {
        "title": "The Cake Factory",
        "version": "1.0"
    }
}
{% endhighlight %}

Since it's easy to convert YAML to JSON and vice versa, what matters for me is how much code I need to write and how
readable it is. So my strong preference goes to YAML which will be used through the rest of the article.
