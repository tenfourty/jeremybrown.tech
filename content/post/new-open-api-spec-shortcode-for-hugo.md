+++
categories = ["Blog Posts", "APIs", "Technology"]
date = "2016-07-13T15:08:39+02:00"
description = ""
keywords = []
title = "New OpenAPI Specification Shortcode for Hugo"
slug = "new-open-api-spec-shortcode-for-hugo"
type = "post"
draft = "true"

+++

One of the things I've been meaning to try for a while is to experiment with combining [Open API Spec](https://openapis.org) (formerly known as Swagger Spec) and static websites. So I've hacked together a quick experiment that allows you to embed OpenAPI Spec inside a [Hugo](https://gohugo.io/) site.

You can see an example of this in action [here](/hugo-OAI-swagger-example/).

<!--more-->

The way I got this to work is I created a [Hugo Shortcode](https://gohugo.io/extras/shortcodes/) which I call like this:

```go
{{</* oai-spec url="http://petstore.swagger.io/v2/swagger.json" api_key="special-key" */>}}
```

The shortcode embeds [Swagger UI](https://github.com/swagger-api/swagger-ui) as a iframe and renders the OpenAPI Spec from the url you've passed in.

The full source of my hack is on GitHub as [hugo-openapispec-shortcode](https://github.com/tenfourty/hugo-openapispec-shortcode).

I'm quite happy about how this turned out for a simple proof of concept, however if I was building this out a bit further or wanted to document an API properly I might consider writing a new template for Hugo that pulled the OpenAPI Spec from the [Hugo `data` directory](https://gohugo.io/extras/datafiles/) and render it using HTML/CSS templates, I think this approach might produce quite an awesome statically generated API docs site.
