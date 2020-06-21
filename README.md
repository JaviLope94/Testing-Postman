
## Newman

Ahora cada vez que nosotros o nuestros compañeros usen esta colección de Postman se 
ejecutarán todas las pruebas, ganando en calidad y en detección de errores.
Pero ahora queremos ir un paso más haya y hacer que esas pruebas se lancen
por líneas de comandos. Así por ejemplo, en cada deployment de nuestra API,
se tenga una herramienta por línea de comandos para probar que nuestra API
sigue sirviendo las peticiones como se espera. Para ello, utilizaremos la
librería Nodejs Newman, una herramienta extensible y configurable de línea
de comandos para Postman que ejecuta las peticiones de nuestra colección.



## Run 
newman run -e dev.postman_environment.json curso-testing.postman_collection.json