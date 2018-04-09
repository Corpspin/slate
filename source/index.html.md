---
title: SpinCommerce Developers

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python

toc_footers:
  - <a href='https://github.com/lord/slate' target="blank">Documentado con Slate</a>

includes:
  - api/orders
  - shops
  - errors

search: true
---

# Introducción

Bienvenido a la documentación para desarrolladores de SpinCommerce. Aquí podrás encontrar todo lo necesario para desarrollar tus propias aplicaciones conectadas al API JSON de nuestra plataforma o personalizar el diseño y funciones de tu tienda.

Si tienes alguna duda, no dudes en escribirnos a [soporte@spincommerce.com](mailto:soporte@spincommerce.com).

<aside class="notice">
Para poder hacer uso del API de SpinCommerce, necesitas contratar una tienda en el plan Profesional o plan Corporativo.
</aside>

# API

## Versionamiento

**Esta documentación corresponde a la versión 1 (o V1) del API.**

El endpoint base de la versión 1 es `https://api.spincommerce.com/v1/`.

Implementaciones futuras del API que no sean compatibles con esta versión, serán implementados en un endpoint distinto, con el fin de garantizar que tus desarrollos no se vean afectados.

## Autenticación

> Ejemplo de un request autenticado:

```ruby
require 'net/http'
require 'json'

url = URI('https://api.spincommerce.com/v1/orders')
request = Net::HTTP.new(uri)
# Recuerda reemplazar tu-api-token por tu propio Token
headers = {
  'Authorization' => 'Token tu-api-token',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}
response = request.get(uri, headers)
JSON.parse(response)
```

```shell
# Recuerda reemplazar 'tu-api-token' por tu propio Token
curl --request GET \
  --url https://api.spincommerce.com/v1/orders \
  --header 'Authorization: Token tu-api-token'
```

<aside class="notice">
Todos los requests deben ser realizados sobre HTTPS. Requests hechos sobre HTTP serán rechazados.
</aside>

Para autenticar tus requests, solo debes incluir un API Token en el Header de cada request. Puedes generar un API Token en [https://app.spincommerce.com/api_tokens](https://app.spincommerce.com/api_tokens).

`Authorization: Token tu-api-token`

Todos los API Tokens tienen permiso de lectura, que permite acceder a endpoints del API con método `GET`. Para poder acceder a endpoints con métodos `POST, PATCH y DELETE`, debes generar un API Token con permisos de escritura.






