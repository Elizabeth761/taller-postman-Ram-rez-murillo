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

Fuentes Consultadas
- https://developer.mozilla.org/en-US/docs/Glossary/Idempotent

- https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-idempotency-key-header

- https://www-freecodecamp-org.translate.goog/news/idempotency-in-http-methods/?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc


# Peticiones con el PUT y POST

PUT: al hacerlo varias veces seguidas el resultado siguie siendo el mismo y no cambia las repeticiones.

POST: al hacerlo varias veces seguidas al ejecutar la misma petición el servidor debería crear un recurso nuevo cada vez con un id distinto incremental (101, 102, 103...) confirmardo que no es idempotente.


# Cabeceras de la respuesta (Headers)

1. Content-Type

- Valor observado: application/json; charset=utf-8

- Qué significa: indica el formato del cuerpo de la respuesta json codificado en UTF-8.

- Por qué es importante al probar una API: 

Se necesita saber como interpretar los datos recibidos antes de procesarlos si esta cabecera dijera algo distinto ej:(`text/html`) pero el body fuera json cualquier programa que intente parsearlo como json fallaría aunque el código de respuesta fuera 200 ok Como tester verificar el tipo de contenido que permite detectar inconsistencias entre lo que el servidor dice que envía y lo que realmente envía.

2. Cache-Control

- Valor observado: max-age=43200

- Qué significa: indica por cuánto tiempo (en segundos) el cliente puede guardar esta respuesta en caché antes de tener que pedirla de nuevo al servidor 43200 segundos equivalen a 12 horas.

- Por que es relevante: al probar en una API esta cabecera importa porque si un valor cambia en el servidor ej:(se actualiza un post) pero el cliente sigue mostrando la versión en caché el usuario vería datos desactualizados sin que esto sea técnicamente un error del servidor Es util para diferenciar un defecto real de un simple efecto de caché.

3. ETag

- Valor observado: W/"6b80-Ybsq/K6Gwwqr YkAsFxqDXGC7DoM"

- Qué significa: es un identificador unico que representa la versión exacta de un recurso en un momento dado si el recurso cambia el ETag cambia.

- Por que es relevante: permite que el cliente compare si tiene la versión más reciente de un recurso sin necesidad de descargarlo completo de nuevo comparando solo el ETag En pruebas sirve para verificar que una actualización (PUT/PATCH) realmente generó una nueva versión del recurso ya que el ETag debería cambiar tras la modificación.



# Encuetra el Limite 

- Id más alto que devuelve 200: 100

- Primer id que devuelve 404: 101

- ¿cómo se llama ese tipo de caso de prueba? 

se llama prueba de valores de limite Consiste en probar justo en el borde entre lo que es válido y lo que no en lugar de probar solo casos cómodos en medio del rango.

- ¿Por qué se dice que los defectos se concentran ahí?

Porque los errores de programación mas comunes ocurren en las condiciones que definen ese límite ej: un desarrollador escribe `id <= 100` en vez de `id < 100` (o viceversa) provoca que el id 100 fallara o que el 101 funcionara cuando no debería Probar solo con valores intermedios (como el id 50) que no detecta ese tipo de error porque ese id sería valido sin importar si la condición esta bien o mal escrita Los valores límite son justamente donde ese tipo de error se manifiesta.

