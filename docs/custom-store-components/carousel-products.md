---
title: Carousel Products
description: Carrusel de Productos personalizado.
authors:
  name: Renzo García
  title: Frontend Developer
  # url: https://github.com/wgao19
  # image_url: https://github.com/wgao19.png
tags: [avanzado, carrusel]
---

# CarouselProducts

Este componente nos permite visualizar un carrusel de productos casi idéntico al nativo, pero con un listado de productos que no puede otorgar un carrusel nativo de VTEX.

Para poder utilizar este componente personalizado necesitamos agregar la dependencia de `"custom-store-components"` con su versión correspondiente en la app VTEX deseada de la siguiente manera.

```json title="store-theme/manifest.json"
"dependencies": {
  "custom-store-components": "0.x"
}
```

## Propiedades

Existen diferentes maneras de instanciar el componente para poder visualizarlo, pero como estructura básica se deben especificar algunas propiedades.

| Propiedad  | Valores  | Descripción                                                                                                                                                                                                | Valor por defecto |
| ---------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| `id`       | `string` | Es el identificador clave para saber qué tipo de carrusel de productos debe mostrarse. Para **Últimos Productos Visitados** use `"last-visited-products"` y para **Los Más Vendidos** use `"best-sellers"` | `""`              |
| `title`    | `string` | Texto `<h2>` que se mostrará en la parte superior del carrusel siempre y cuando tenga productos disponibles.                                                                                               | `""`              |
| `maxItems` | `number` | Número máximo de productos que podrán mostrarse.                                                                                                                                                           | `null`            |

## Instanciar

Para lograr instanciar el componente será suficiente con ubicarnos en donde deseamos e insertar `"carousel-products"` seguido del identificador a elección.

```json
"flex-row#home-carousels": {
  "children": [
    "rich-text#home-title"
    // highlight-start
    "carousel-products#home",
    // highlight-end
    "image#home-banner-1"
    "image#home-banner-2"
  ]
}
```

### Carrusel: Últimos Productos Visitados

Este carrusel se encarga de mostrar los últimos productos que el **cliente** acaba de visitar en la web o los productos que llegó a ver en su anterior visita. Puede instanciarse en cualquier página.

```json
"carousel-products#home-last-visited-products": {
  "props": {
    "id": "last-visited-products",
    "title": "Últimos Productos Visitados",
    "maxItems": 20
  }
}
```

**Nota:** La información por cliente se almacena en su sesión y tiene una duración  inalterable de *60 días*.

### Carrusel: Los Más Vendidos

El carrusel va a mostrar los productos más vendidos de la **tienda en general**, se visualizarán ordenados de manera descendente y solo los productos que cuenten con disponibilidad de stock. Puede instanciarse en cualquier página.

```json
"carousel-products#home-best-sellers": {
  "props": {
    "id": "best-sellers",
    "title": "Los Más Vendidos",
    "maxItems": 20
  }
}
```

### Carrusel: Lo Más Agregado al Carrito

### Carrusel: Los Clientes Vieron