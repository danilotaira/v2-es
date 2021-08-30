# Entender la API


La versión 2 de la API de AnyMarket es un paso adelante para facilitar la integración de nuestros socios con los distintos mercados disponibles. La creación de la API permite que las aplicaciones existentes o nuevas aplicaciones amplíen sus operaciones de ventas de forma sencilla.

Una vez que haya solicitado su token de acceso a nuestro soporte, es fácil comenzar a integrarse con AnyMarket.

Se puede acceder a todas las URL a través del host sandbox-api.anymarket.com.br. Por ejemplo: puede recuperar todas sus categorías accediendo a la URL con su TOKEN de acceso (reemplace TOKEN con el suyo):


```
http://sandbox-api.anymarket.com.br/v2/categories?gumgaToken=TOKEN
```

Debe ingresar su token de acceso para todas las URL a las que se accederá. Además de usarlo como parámetro en la URL, también es posible pasarlo como encabezado de solicitud. El nombre gumgaToken debe usarse para ambos formularios.

## Limites

Se bueno. Si envía demasiadas solicitudes rápidamente, devolveremos el código de error 429 (demasiadas solicitudes). Tiene un límite de ** 10 solicitudes por segundo ** por token.

## Operaciones

[cadastrar um produto](#497ef920-87bd-4a3f-b91e-19abadb3f7c0) 

Hacemos nuestro mejor esfuerzo para asegurarnos de que todas nuestras URL sean [RESTful](http://en.wikipedia.org/wiki/Representational_state_transfer). Cada URL puede admitir uno de los cuatro tipos diferentes de verbos http:

-   **GET** obtener información sobre un recurso
-   **POST** crear un recurso
-   **PUT** actualiza un recurso
-   **DELETE** eliminar un recurso

## Estructura

### Paginación

Se pagina la gran mayoría de las solicitudes que devuelven una colección de recursos. Por ejemplo, la consulta de categoría superior. Cada respuesta paginada se devuelve en el siguiente formato:

```
{
  "links": [
    {
      "rel": "prev",
      "href": "http://sandbox-api.anymarket.com.br/v2/categories?offset=0"
    },
    {
      "rel": "next",
      "href": "http://sandbox-api.anymarket.com.br/v2/categories?offset=4"
    }
  ],
  "content": [
    ...
  ],
  "page": {
    "size": 2,
    "totalElements": 6,
    "totalPages": 3,
    "number": 1
  }
}
```

Para facilitar la navegación secuencial de datos, proporcionamos enlaces para ir a la página siguiente o regresar a la anterior.

De forma predeterminada, la consulta devuelve 20 recursos por página. Sin embargo, permitimos que este número se incremente a un máximo de 100. A continuación se muestran los parámetros que cambian la forma en que se devuelve la página:


-   **offset:** Indica desde qué recurso se iniciará la consulta
-   **limit:** Indica la cantidad de recursos a devolver, desde 20 hasta un máximo de 100.
-   **sort:** Indica por qué atributo se debe ordenar la consulta
