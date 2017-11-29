---
title: SpinCommerce Developers

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby

toc_footers:
  - <a href='https://github.com/lord/slate' target="blank">Documentado con Slate</a>

includes:
  - errors

search: true
---

# Introducción

Bienvenido a la documentación para desarrolladores de SpinCommerce. Aquí podrás encontrar todo lo necesario para desarrollar tus propias aplicaciones conectadas al API de nuestra plataforma.

Si tienes alguna duda, no dudes en escribirnos a [soporte@spincommerce.com](mailto:soporte@spincommerce.com).

<aside class="notice">
Para poder hacer uso del API de SpinCommerce, necesitas contratar una tienda en el plan Profesional o plan Corporativo.
</aside>

# Versionamiento

**Esta documentación corresponde a la versión 1 (o V1) del API.**

El endpoint base de la versión 1 es `https://api.spincommerce.com/v1/` 

Implementaciones futuras del API que no sean compatibles con esta versión, serán implementados en un endpoint distinto, con el fin de garantizar que tus desarrollos no se vean afectados.

# Autenticación

> Ejemplo de un request autenticado

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
curl "https://api.spincommerce.com/v1/orders" \
  -H "Authorization: Token tu-api-token"
```

<aside class="notice">
Todos los requests deben ser realizados sobre HTTPS. Requests hechos sobre HTTP serán rechazados.
</aside>

Para autenticar tus requests, solo debes incluir un API Token en el Header de cada request. Puedes crear un API Token en [https://app.spincommerce.com/api_tokens](https://app.spincommerce.com/api_tokens)

`Authorization: Bearer tu-api-token`

Todos los API Tokens tienen permiso de lectura, que acceder a endpoints del API con método `GET`. Para poder acceder a endpoints con métodos `POST, PATCH y DELETE`, debes generar un API Token con permisos de escritura.



# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

