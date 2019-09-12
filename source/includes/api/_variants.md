## Variantes

### Actualizar el stock de una variante

```shell
curl --request PUT \
  --url 'https://api.spincommerce.com/v1/variants/5999' \
  --header 'authorization: Token TU_API_TOKEN' \
  --header 'content-type: application/json' \
  --data '{
  "variant": {
    "stock": 180
  }
}'
```

> Ejemplo de respuesta a este request:

```json
{
  "variant": {
    "id": 5999,
    "product_id": 4321,
    "sku": "8X31",
    "name": "8 X 31 pulgadas",
    "weight": 1250,
    "track_stock": true,
    "stock": 180,
    "available_without_stock": false
  }
}
```

#### HTTP Request

`PUT https://api.spincommerce.com/v1/variants/<variant_id>`