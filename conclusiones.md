# Idempotencia

- qué significa que un método HTTP sea idempotente. Luego determina cuáles de los cinco métodos lo son y cuáles no.

el metodo idempotente es que pueda realizar o reintentar una solicitud sin provocar el mismo cambio de los datos 
ej: reiniciar una paguina si se mantiene puslando de icono de reinicio simplemte se mantiane en el estado en el que se quedo tras la pulsacion.

- Los métodos funcionales 

GET: Sí Solo consulta información repetir la consulta no debería modificar el recurso.
PUT: Sí	Reemplaza el recurso con la representación enviada; repetir la misma solicitud deja el mismo contenido final.
DELETE:	Sí La primera solicitud elimina el recurso y repetirla mantiene el recurso eliminado.

- Los métodos no funcionales

PATCH: No garantizado Aplica una modificación parcial que puede acumularse si se repite.
POST: Normalmente cada solicitud crea un nuevo recurso o ejecuta una nueva operación.

fuentes consultadas
- https://developer.mozilla.org/en-US/docs/Glossary/Idempotent

- https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-idempotency-key-header

- https://www-freecodecamp-org.translate.goog/news/idempotency-in-http-methods/?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc