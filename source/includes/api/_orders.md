## Órdenes

### Obtener todas las órdenes

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.spincommerce.com/v1/orders")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'Token tu-api-token'

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPSConnection("api.spincommerce.com")

payload = ""

headers = { 'Authorization': "Token tu-api-token" }

conn.request("GET", "/v1/orders", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://api.spincommerce.com/v1/orders \
  --header 'Authorization: Token tu-api-token'
```

> Ejemplo de respuesta a este request:

```json
{
  "orders": [
    {
      "id": 35123,
      "code": "29269BC2",
      "status": "paid",
      "created_at": "2017-12-18T11:10:07.144Z",
      "updated_at": "2017-12-18T11:12:25.652Z",
      "currency": "CLP",
      "subtotal": 30000,
      "discount_name": null,
      "discount_total": 0,
      "shipping_option_name": "Envío a todo Chile",
      "shipping_price": 2450,
      "total": 32450,
      "confirmed_at": "2017-12-18T11:11:01.759Z",
      "paid_at": "2017-12-18T11:12:25.636Z",
      "delivered_at": null,
      "payment_type": "bank_transfer",
      "shipping_country": "Chile",
      "shipping_state": "Región Metropolitana de Santiago",
      "shipping_city": "Santiago",
      "shipping_address": "Mi dirección 123",
      "shipping_postal_code": "7750000",
      "custom_fields": null,
      "customer_id": 4600,
      "customer_first_name": "John",
      "customer_last_name": "Lennon",
      "customer_email": "john@lennon.com",
      "customer_phone": "1234567",
      "courier_name": null,
      "courier_tracking_code": null,
      "shipping_comments": null,
      "items": [
        {
          "id": 60822,
          "created_at": "2017-12-18T11:10:07.162Z",
          "updated_at": "2017-12-18T11:10:07.162Z",
          "product_id": 19699,
          "product_name": "Silla Madera",
          "product_url": "https://apitest.spincommerce.com/products/silla-madera",
          "product_images": [
            "https://spincommercecdn.imgix.net/shops/924/products/19699/690215b1-942e-4b4a-97bf-d09916644aef/product.jpg"
          ],
          "variant_name": null,
          "variant_id": 25609,
          "variant_sku": null,
          "unit_price": 30000,
          "units": 1,
          "weight": 0
        }
      ]
    },
    {
      ...
    }
  ],
  "meta": {
    "pagination": {
      "total_count": 2,
      "total_pages": 1,
      "per_page": 50,
      "current_page": "https://api.spincommerce.com/v1/orders?page=1&per_page=50",
      "previous_page": null,
      "next_page": null,
      "first_page": "https://api.spincommerce.com/v1/orders?page=1&per_page=50",
      "last_page": "https://api.spincommerce.com/v1/orders?page=1&per_page=50"
    }
  }
}
```

Este endpoint devuelve todas las órdenes en estado `paid` o `delivered`.

#### HTTP Request

`GET https://api.spincommerce.com/v1/orders`

#### Parámetros

Parámetro | Default | Descripción
--------- | ------- | -----------
status | null | Permite filtrar las órdenes por estado, los valores aceptados son `paid` o `delivered`. 
per_page | 50 | Número de resultados por request, debe ser un número mayor o igual a 1 y menor o igual a 50.
page | 1 | Número de paginación del request, debe ser un número positivo.

### Obtener una orden específica

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.spincommerce.com/v1/orders/35123")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'Token tu-api-token'

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPSConnection("api.spincommerce.com")

payload = ""

headers = { 'Authorization': "Token tu-api-token" }

conn.request("GET", "/v1/orders/35123", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://api.spincommerce.com/v1/orders/35123 \
  --header 'Authorization: Token tu-api-token'
```

> Ejemplo de respuesta a este request:

```json
{
  "order": {
    "id": 35123,
    "code": "29269BC2",
    "status": "paid",
    "created_at": "2017-12-18T11:10:07.144Z",
    "updated_at": "2017-12-18T11:12:25.652Z",
    "currency": "CLP",
    "subtotal": 30000,
    "discount_name": null,
    "discount_total": 0,
    "shipping_option_name": "Envío a todo Chile",
    "shipping_price": 2450,
    "total": 32450,
    "confirmed_at": "2017-12-18T11:11:01.759Z",
    "paid_at": "2017-12-18T11:12:25.636Z",
    "delivered_at": null,
    "payment_type": "bank_transfer",
    "shipping_country": "Chile",
    "shipping_state": "Región Metropolitana de Santiago",
    "shipping_city": "Santiago",
    "shipping_address": "Mi dirección 123",
    "shipping_postal_code": "7750000",
    "custom_fields": null,
    "customer_id": 4600,
    "customer_first_name": "John",
    "customer_last_name": "Lennon",
    "customer_email": "john@lennon.com",
    "customer_phone": "1234567",
    "courier_name": null,
    "courier_tracking_code": null,
    "shipping_comments": null,
    "items": [
      {
        "id": 60822,
        "created_at": "2017-12-18T11:10:07.162Z",
        "updated_at": "2017-12-18T11:10:07.162Z",
        "product_id": 19699,
        "product_name": "Silla Madera",
        "product_url": "https://apitest.spincommerce.com/products/silla-madera",
        "product_images": [
          "https://spincommercecdn.imgix.net/shops/924/products/19699/690215b1-942e-4b4a-97bf-d09916644aef/product.jpg"
        ],
        "variant_name": null,
        "variant_id": 25609,
        "variant_sku": null,
        "unit_price": 30000,
        "units": 1,
        "weight": 0
      }
    ]
  }
}
```

Este endpoint devuelve una orden en estado `paid` o `delivered`.

#### HTTP Request

`GET https://api.spincommerce.com/v1/orders/<id>`

#### Parámetros

Parámetro | Descripción
--------- | ------- | -----------
id | id de la orden.

### Actualizar una orden

```ruby
require 'uri'
require 'net/http'
require 'json'

url = URI("https://api.spincommerce.com/v1/orders/35123")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["Authorization"] = 'Token tu-api-token'
request["content-type"] = 'application/json'
params = { order: {
             status: 'delivered',
             send_status_notification: true,
             courier_name: 'FedEx',
             courier_tracking_code: '54321',
             shipping_comments: 'My comments' 
           }  
         }

request.body = params.to_json

response = http.request(request)
puts response.read_body
```

```python
import http.client

conn = http.client.HTTPSConnection("api.spincommerce.com")

payload = "{\n\t\"order\": {\n\t\t\"status\": \"delivered\",\n\t\t\"send_status_notification\": true,\n\t\t\"courier_name\": \"FedEx\",\n\t\t\"courier_tracking_code\": \"54321\",\n\t\t\"shipping_comments\": \"All good!\"\n\t}\n} "

headers = {
    'Authorization': "Token tu-api-token",
    'content-type': "application/json"
    }

conn.request("PUT", "/v1/orders/35123", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request PUT \
  --url https://api.spincommerce.com/v1/orders/35123 \
  --header 'Authorization: Token tu-api-token' \
  --header 'content-type: application/json' \
  --data '{
  "order": {
    "status": "delivered",
    "send_status_notification": true,
    "courier_name": "FedEx",
    "courier_tracking_code": "54321",
    "shipping_comments": "All good!"
  }
} '
```

> Ejemplo de respuesta a este request:

```json
{
  "order": {
    "id": 35123,
    "code": "29269BC2",
    "status": "delivered",
    "created_at": "2017-12-18T11:10:07.144Z",
    "updated_at": "2017-12-19T13:53:30.803Z",
    "currency": "CLP",
    "subtotal": 30000,
    "discount_name": null,
    "discount_total": 0,
    "shipping_option_name": "Envío a todo Chile",
    "shipping_price": 2450,
    "total": 32450,
    "confirmed_at": "2017-12-18T11:11:01.759Z",
    "paid_at": "2017-12-18T11:12:25.636Z",
    "delivered_at": "2017-12-19T13:53:30.797Z",
    "payment_type": "bank_transfer",
    "shipping_country": "Chile",
    "shipping_state": "Región Metropolitana de Santiago",
    "shipping_city": "Santiago",
    "shipping_address": "Mi dirección 123",
    "shipping_postal_code": "7750000",
    "custom_fields": null,
    "customer_id": 4600,
    "customer_first_name": "John",
    "customer_last_name": "Lennon",
    "customer_email": "john@lennon.com",
    "customer_phone": "1234567",
    "courier_name": "FedEx",
    "courier_tracking_code": "54321",
    "shipping_comments": "All good!",
    "items": [
      {
        "id": 60822,
        "created_at": "2017-12-18T11:10:07.162Z",
        "updated_at": "2017-12-18T11:10:07.162Z",
        "product_id": 19699,
        "product_name": "Silla Madera",
        "product_url": "https://apitest.spincommerce.com/products/silla-madera",
        "product_images": [
          "https://spincommercecdn.imgix.net/shops/924/products/19699/690215b1-942e-4b4a-97bf-d09916644aef/product.jpg"
        ],
        "variant_name": null,
        "variant_id": 25609,
        "variant_sku": null,
        "unit_price": 30000,
        "units": 1,
        "weight": 0
      }
    ]
  }
}
```
Este endpoint actualiza los datos de una orden.

#### HTTP Request 

`PUT https://api.spincommerce.com/v1/orders/<id>`

#### Parámetros

Parámetro | default | Descripción
--------- | ------- | -----------
id | null | id de la orden.
status | null | Estado de la orden, puede ser `paid` o `delivered`.
send_status_notification | false | Boolean que indica si se debe enviar un email de notificación al cliente informando del cambio de estado.
courier_name | null | El nombre de la empresa transportadora de la orden.
courier_tracking_code | null | Código de rastreo del courier.
shipping_comments | null | Comentarios adicionales referentes a la entrega de la orden.