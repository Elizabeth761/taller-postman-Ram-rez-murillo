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
• El código de estado: 200 OK
• Cuántos elementos trae la respuesta: Trae 1 solo elemento en respuesta de la terminar con el metodo de json.
• Qué campos tiene cada elemento: presenta 4 campos que son userId, id, title y body

GET/posts/.
• El código de estado: 200 OK
• Cuántos elementos trae la respuesta: trae la lista completa de los elementos de la terminal de json devolviendo
un resultado de 100 publicaciones.
• Qué campos tiene cada elemento: presenta los mismos 4 campos de get post/1 userId, id, title y body

# ¿en qué se diferencian los criterios de aceptación cuando pides un recurso y cuando pides una colección?



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