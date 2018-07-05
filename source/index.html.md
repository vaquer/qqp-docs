---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introducción

Bienvenido a la documentación del *API QQP*. Puedes usar los endpoints de esta API para obtener información sobre los precios de los productos registrados por PROFECO.

Estos datos son recabados de la base de datos oficial de PROFECO mediante un proceso de ETL que actualiza los datos cada mes.

# Productos

## Lista de productos

```python
import requests

response = requests.get('https://datos.gob.mx/qqp/api/v1/products',\
  params={'page': 1, 'limit':100})
response.json()
```

```shell
curl "https://datos.gob.mx/qqp/api/v1/products?page=1&limit=100"
```

> El comando anterior regresa una respuesta JSON estructurada de la siguiente manera:

```json
{
"results":
  [
    {
      "id": 1,
      "id_profeco": "0166",
      "nombre": "ACEITE"
    },
    {
      "id": 2,
      "id_profeco": "9000",
      "nombre": "ACEITE DE OLIVA"
    }
  ],
  "meta":
  {
    "page": 1,
    "limit": 100,
    "total": 2500,
    "pages": 250
  }
}
```

Este endpoint regresa la lista de todos los productos registrados en la base de datos de QQP.

### Petición HTTP

`GET https://datos.gob.mx/qqp/api/v1/products`

### Parametros (Query Parameters)

Parametro | Default | Descripción
--------- | ------- | -----------
page | 1 | Página del listado de productos.
limit | 100 | Tamaño de página en el listado de productos.

<aside class="notice">
Nota — El parametro <strong>limit</strong> acepta valores con minimo 50 y maximo 500
</aside>

## Obtener un producto especifico

```python
import requests

response = requests.get('https://datos.gob.mx/qqp/api/v1/products/2')
response.json()
```

```shell
curl "https://datos.gob.mx/qqp/api/v1/products/2"
```

> El comando anterior regresa una respuesta JSON estructurada de la siguiente manera:

```json
{
  "id": 2,
  "id_profeco": "002",
  "nombre": "Producto 2"
}
```
Este endpoint regresa información de un producto especifico por medio de su ID.

### Petición HTTP

`GET https://datos.gob.mx/qqp/api/v1/products/<ID>`

### Parametros de URL

Parametro | Descripción
--------- | -----------
ID | Identificador numerico del producto dentro de la base de datos de QQP


# Precios

## Lista de precios

```python
import requests

response = requests.get('https://datos.gob.mx/qqp/api/v1//prices',\
  params={'page': 1, 'limit':100})
response.json()
```

```shell
curl "https://datos.gob.mx/qqp/api/v1/prices?page=1&limit=100"
```

> El comando anterior regresa una respuesta JSON estructurada de la siguiente manera:

```json
{
  "results":[
    {
      "id_producto": 166,
      "id_marca": "14",
      "id_establecimiento": "62096",
      "marca": "ACEITE CAPULLO BOTELLA 840 ML. CANOLA",
      "establecimiento": "SORIANA SUPER SUCURSAL CUERNAVACA",
      "estado": "",
      "direccion": "APOLO XI 2, ESQ. PODER LEGISLATIVO",
      "cp": "62250",
      "fecha_observacion": "07/06/2018",
      "fecha_actualizacion": "18/05/2018",
      "precio": 12.05
    },
    {
      "id_producto": 166,
      "id_marca": "14",
      "id_establecimiento": "62088",
      "marca": "ACEITE CAPULLO BOTELLA 840 ML. CANOLA",
      "establecimiento": "MEGA COMERCIAL MEXICANA",
      "estado": "",
      "direccion": "VICENTE GUERRERO 205 ENTRE PERICON Y DE LA SELVA",
      "cp": "62270",
      "fecha_observacion": "06/06/2018",
      "fecha_actualizacion": "18/05/2018",
      "precio": 13.05
    }
  ],
  "meta":
  {
    "page": 1,
    "limit": 100,
    "total": 2500,
    "pages": 250
  }
}
```

Este endpoint regresa la lista de precios de los productos vs marcas registrados por PROFECO.

### Petición HTTP

`GET https://datos.gob.mx/qqp/api/v1/prices/?page=1`

### Parametros (Query Parameters)

Parametro | Default | Descripción
--------- | ------- | -----------
page | 1 | Página del listado de productos.
limit | 100 | Tamaño de página en el listado de productos.

<aside class="notice">
Nota — El parametro <strong>limit</strong> acepta valores con minimo 50 y maximo 500
</aside>

## Obtener precios de un producto especifico

```python
import requests

response = requests.get('https://datos.gob.mx/qqp/api/v1/prices/2',\
  params={'page': 1, 'limit':100})
response.json()
```

```shell
curl "https://datos.gob.mx/qqp/api/v1/prices/2/?page=1"
```

> El comando anterior regresa una respuesta JSON estructurada de la siguiente manera:

```json
{
  "results":[
    {
      "id_producto": 2,
      "id_marca": "14",
      "id_establecimiento": "62096",
      "marca": "ACEITE CAPULLO BOTELLA 840 ML. CANOLA",
      "establecimiento": "SORIANA SUPER SUCURSAL CUERNAVACA",
      "estado": "",
      "direccion": "APOLO XI 2, ESQ. PODER LEGISLATIVO",
      "cp": "62250",
      "fecha_observacion": "07/06/2018",
      "fecha_actualizacion": "18/05/2018",
      "precio": 12.05
    },
    {
      "id_producto": 2,
      "id_marca": "14",
      "id_establecimiento": "62088",
      "marca": "ACEITE CAPULLO BOTELLA 840 ML. CANOLA",
      "establecimiento": "MEGA COMERCIAL MEXICANA",
      "estado": "",
      "direccion": "VICENTE GUERRERO 205 ENTRE PERICON Y DE LA SELVA",
      "cp": "62270",
      "fecha_observacion": "06/06/2018",
      "fecha_actualizacion": "18/05/2018",
      "precio": 13.05
    }
  ],
  "meta":
  {
    "page": 1,
    "limit": 100,
    "total": 2500,
    "pages": 250
  }
}
```

Este endpoint filtra la lista de precios por ID de producto y regresa los precios por marca del producto.

### Petición HTTP

`GET https://datos.gob.mx/qqp/api/v1/prices/<ID>`

### Parametros de URL

Parametro | Descripción
--------- | -----------
ID | Identificador numerico del producto dentro de la base de datos de QQP

### Parametros (Query Parameters)

Parametro | Default | Descripción
--------- | ------- | -----------
page | 1 | Página del listado de productos.
limit | 100 | Tamaño de página en el listado de productos.