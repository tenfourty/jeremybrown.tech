+++
author = "Jeremy Brown"
date = "2016-07-12"
type = "page"
title = "Open API Initiative Spec (Swagger) with Hugo - PetStore Example"
url = "/hugo-OAI-swagger-example/"
draft = "false"

+++

This is an example of using [Open API Spec](https://openapis.org) (formerly known as Swagger Spec) with [Hugo](https://gohugo.io/) to generate documentation from your spec files.

The example uses [Hugo Shortcodes](https://gohugo.io/extras/shortcodes/) to embed the Open API Spec in the page, the source code for the shortcode is hosted on GitHub [here](https://github.com/tenfourty/hugo-openapispec-shortcode).

To embed the API documentation below you just need to include the following shortcode:

```go
{{</* oai-spec url="http://petstore.swagger.io/v2/swagger.json" api_key="special-key" */>}}
```

There are just two options:

* **url (required)** - the url of the Open API Spec
* **api_key (optional)** - the API Key you want embedded in your document

The resulting output will look like the page below.

{{< oai-spec url="http://petstore.swagger.io/v2/swagger.json" api_key="special-key" >}}
