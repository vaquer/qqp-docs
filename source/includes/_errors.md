# Errores

<aside class="notice">
Los siguientes códigos son tomados del estandar REST.
</aside>

El API QQP maneja los siguientes códigos de error:


Código | Significado
---------- | -------
400 | Bad Request -- Petición invalida.
401 | Unauthorized -- Petición no autorizada.
403 | Forbidden -- El recurso que solicitas no esta disponible.
404 | Not Found -- El recurso que solicitaste no existe.
405 | Method Not Allowed -- Metodo HTTP invalido.
406 | Not Acceptable -- El recurso solicitado esta con otro formato distinto a JSON.
418 | I'm a teapot.
429 | Too Many Requests -- Se ha detectado un uso intensivo no autorizado del recurso.
500 | Internal Server Error -- Problemas internos en el servidor. Intenta más tarde.
503 | Service Unavailable -- Servicio temporalmente deshabilitado por mantenimiento.
