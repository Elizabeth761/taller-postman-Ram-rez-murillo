# Tabla de observaciones del Postman

| # | Petición | Código esperado | Código obtenido | ¿Coincide? |
| :---: | :--- | :---: | :---: | :---: |
| 1 | GET /posts/1 | 200 | 200 | Sí |
| 2 | GET /posts | 200 | 200 | Sí |
| 3 | GET /posts/9999 | 404 | 404 | Sí |
| 4 | POST /posts | 201 | 201 | Sí |
| 5 | PUT /posts/1 | 200 | 200 | si |
| 6 | PATCH /posts/1 | 200 | 200 | si |
| 7 | DELETE /posts/1 | 200 | — | — |


# Ejecucion de las peticiones 1 y 2 de la tabla

GET/posts/1.
* El código de estado: 200 OK
* Cuántos elementos trae la respuesta: Trae 1 solo elemento en respuesta de la terminar con el metodo de json.
* Qué campos tiene cada elemento: presenta 4 campos que son userId, id, title y body

GET/posts/.
* El código de estado: 200 OK
* Cuántos elementos trae la respuesta: trae la lista completa de los elementos de la terminal de json devolviendo
un resultado de 100 publicaciones.
* Qué campos tiene cada elemento: presenta los mismos 4 campos de get post/1 userId, id, title y body

# ¿en qué se diferencian los criterios de aceptación cuando pides un recurso y cuando pides una colección?

* Recurso 
se valida la existencia de una entidad o los comportamientos funcionales de un elemento u usurio 
* Coleccion
se valida la existencia de la lista y la correcta entrega de un cojuntos de elementos ej: catalogo de productos


# investigaciion del caso de prueba error 404 

* ¿qué pasaría si esa misma petición hubiera devuelto 200 con un cuerpo vacío? 
cuando se le pidio que hiciera dicha peticion que no existe el comportamiento de salida del postman fue dar 404 not found diciendonos que claramente que hay un error porque no existe
en cambio cuando la salida espereada respondio con 200 ok con un cuerpo vacio el programa interpreto que la 
peticion fue exitosa y que hay algo cuando no paso nada y sigue en blanco el sistema nos esta diciendo que todo esta bien cuando en realidad hubo un problema eso prodria demostrar que es un error peligroso porque nos puedes llegar a confundir ya sea si una la app, pagina o aplicacion demuestra que todo esta bien sin ningún mensaje de error

* ¿Sería un defecto?
no seria un defecto ya que esto define el comportamiento en salida de una api si no esta configurada para salir
demostrando que el recuso /posts/9999 no existe y los resultado tanto como de salida como de ingresando siempre va ser 
404 not found ya que esto es una regla estandar de http

# POST /posts (creación de un recurso)

se hizo la peticion: POST https://jsonplaceholder.typicode.com/posts con la pestaña Body en modo raw con formato JSON
para que saliera los siguiente.

{ "title": "Mi primera prueba", 
"body": "Taller de Ingeniería de Software II", 
"userId": 1 } 

con el codigo odtenido 201 al hacer las 5 peticiones 

• ¿qué observaste? 
al ejecutar la peticion 5 veces seguidas salia lo mismo sin ningun cambio o repeticion o aunmento se quedaba
ahi estatico que se supone que POST debe de crear un nuevo id distinto

• ¿Por qué crees que ocurre eso? 
Porque https://jsonplaceholder.typicode.com/posts/ es una API de práctica que simula tener datos reales detras cuando recibe ordenes url desde la aplicacion de potsman calculando que id le va a tocar al siguiente recurso y lo devuelve en la respuesta pero nunca guarda el nuevo post en ningún lado sin importar cuántas veces se repita la petición el resultado simulado es siempre igual.

• ¿Cómo comprobarías, en una API real, que el recurso se creó de verdad?
- Haciendo un **GET** al endpoint del recurso usando el `id` que devolvió el POST (ej. `GET /posts/101`) y verificando que el recurso exista y tenga los mismos datos que enviaste.
- Haciendo un **GET** a la colección completa y confirmando que el nuevo elemento aparece en la lista.
- Revisando directamente la base de datos del sistema si se tiene acceso.
- Repitiendo el POST varias veces y verificando que cada vez se genera un **id distinto** (si el id se repite como en JSONPlaceholder es señal de que no se está persistiendo realmente).







# Las diferencias entre PUT y PATCH

PUT: al pedir un recurso la api esta actualizando los datos por la parte del body (raw) a travez de la peticion que 
nosotros le pedimos que hiciera PUT https://jsonplaceholder.typicode.com/posts/1 

{
  "title": "Cuentos del Olimpo"
}

y el servidor me esta devolviendo con el codigo 200 y { userId, id, title, body } en modo json con los datos de 
ese elemento

{
  "title": "Cuentos del Olimpo",
  "id": 1
}


PATCH: al pedir  que contiene múltiples objetos con la misma estructura.

PATCH https://jsonplaceholder.typicode.com/posts/1