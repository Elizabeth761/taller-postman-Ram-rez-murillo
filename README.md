# taller-postman-Ram-rez-murillo

Taller de APIs y Postman
Elizabeth Ramirez Murilo
Identificación: 1006293845
Curso: Ingeniería de Software II — Cotecnova

# Marco conceptual

• Que es una Api rest 
son componentes de software que se puede comunicar diferentes aplicaciones entre si mediante protocolos de http y metodos de formatos de datos ayudando a dichas aplicaciones a modificar solicitar eliminar modificar y crear como si fuera un crud.

• Qué significa que una API sea «REST»
que esta diseñada a los principios de diseño de estilo arquitectonico para la organizacion de informacion de datos mediante urls y operaciones de hppt
como si se fuera hacer una solicitud de pedido.

• Qué es un recurso y qué es un endpoint
recurso: cualquier dato o odjecto u elemento de informacion que se pueda consutar o modificar atravez del sistema 
endpoint: es el punto de acceso de la api en donde se pueda  conectar con las urls de las wed que actua como comunicador entre el cliente y el sevidor.

• ejemplo de una aplicación que uses a diario y que dependa de APIs  
whatsApp que utiliza Aips de geolocalizacion y de almacenamiento en la nube de copias de seguridad de informacion y ubicacion (google drive y maps).  

Fuente consultada:¿Qué es una API REST?
https://cloud.google.com/discover/what-is-rest-api?hl=es


# Métodos HTTP

| Método | Operación CRUD | Qué hace |
| :--- | :--- | :--- |
| **GET** | Consultar | Obtener información de una lista |
| **POST** | Crear | Registrar datos |
| **PUT** | Modificar | Modificar los datos |
| **PATCH** | Actualizar | Cambiar datos |
| **DELETE** | Eliminar | Eliminar datos |


# Las familias de códigos de estado

1xx (Informativos): el servidor recibió la solicitud y el proceso continúa todavía no es la respuesta final.
ej:(100 Continue) el cliente puede continuar enviando los datos de la solicitud.

2xx (Éxito): la solicitud fue recibida verficada y analizada correctamente.
ej: (200 OK) da una consulta a GET (usuarios) para mostrar que fue exitosa.

3xx Redirección: se necesita hacer una acción adicional para completar la solicitud que normalmente podra acudir a otra URL o utilizar una respuesta almacenada.
ej: (301 Moved Permanently) el recurso se trasladó permanentemente a otra dirección.

4xx (Error del cliente): la solicitud tiene un problema o no puede cumplirse debido a lo que envió o solicitó el cliente.
ej: (404 Not Found): el endpoint o el recurso solicitado no existe.

5xx (Error del servidor): el servidor no pudo cumplir una solicitud que aparentemente era válida.
ej: (500 Internal Server Error): ocurrió un fallo interno o inesperado en el servidor.

• ¿por qué se separan los errores 4xx de los 5xx? 
el codigo 4xx muestra que el cliente debe de corregir algo ej: en la URL o los credenciales, permisos o el fomato de los datos.
el codido 5xx el servidor o la paguina debe de mirar y corregir algo ej: error de la paguina ,mala configuracion, servicio no disponible o la base de datos. 

Fuente consultada: codigos de estado
https://www.rfc-editor.org/rfc/rfc9110.html



