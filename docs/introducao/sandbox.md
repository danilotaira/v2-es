# Entorno de caja de arena

Para permitir que el integrador pruebe su funcionalidad y se asegure de que funcionará sin errores en el entorno de producción, AnyMarket proporciona el entorno sandbox. Las pruebas realizadas en este entorno certifican a la aplicación que se están aplicando todas las reglas de la API.

El entorno sandbox de AnyMarket tiene las mismas operaciones que el entorno de producción, sin embargo, la información es diferente del entorno de producción. Los entornos sandbox y de producción están aislados y no tienen acceso entre sí.

Los tokens de acceso obtenidos al ponerse en contacto con AnyMarket dan acceso a ambos entornos, pero cada entorno requiere su propio token. No es posible acceder al entorno de producción con el token de sandbox y viceversa.

Una vez que se obtiene el token de Sandbox, la aplicación funciona de manera idéntica al entorno de producción. La principal diferencia es que la Aplicación debe apuntar al entorno Sandbox en lugar de a Producción.

URL de la zona de pruebas:


```
http://sandbox-api.anymarket.com.br/v2
```

URL de producción:

```
http://api.anymarket.com.br/v2
```