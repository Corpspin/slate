## Productos

### Obtener todos los productos

```shell
curl --request GET \
  --url https://api.spincommerce.com/v1/products \
  --header 'Authorization: Token tu-api-token'
```

> Ejemplo de respuesta a este request:

```json
{
  "products": [
    {
      "id": 4321,
      "name": "Tabla de skate",
      "slug": "tabla-de-skate",
      "description": "La descripción de mi producto",
      "price": 10000,
      "compare_price": 0,
      "status": "enabled",
      "variants": [
        {
          "id": 5999,
          "product_id": 4321,
          "sku": "8X31",
          "name": "8 X 31 pulgadas",
          "weight": 1250,
          "track_stock": true,
          "stock": 180,
          "available_without_stock": false
        }
      ],
      "images": [
        {
          "id": 1234,
          "filename": "tabla.jpg",
          "sort_index": 0,
          "urls": {
            "original": "https://...",
            "small": "https://...",
            "medium": "https://...",
            "large": "https://..."
          }
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
      "current_page": "https://api.spincommerce.com/v1/products?page=1&per_page=50",
      "previous_page": null,
      "next_page": null,
      "first_page": "https://api.spincommerce.com/v1/products?page=1&per_page=50",
      "last_page": "https://api.spincommerce.com/v1/products?page=1&per_page=50"
    }
  }
}

```

#### HTTP Request

`GET https://api.spincommerce.com/v1/products`