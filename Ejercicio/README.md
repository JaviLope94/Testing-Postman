

## Ejercicio 1

    1º Crear una nueva colección llamada testing-with-postman

    2º Añadir un nuevo environment con el nombre de variable base_url y con su 'initial value' y
    'current value' = https://jsonplaceholder.typicode.com

    3º Añadir en una nueva pestaña la peticion con url {{base_url}}/photos y añadirla a la collecion testing-with-postman

    4º En el apartado de 'Tests':
        > Crear un nuevo test que:
            - Compruebe que el estado de la petición es de 200
            - Comprobar que la respuesta es un json valido
            - Comprobar que la repsuesta tenga header
            - Comprobar que la respuesta tengo una key en header de tipo 'Content-Type'
            - Comprobar que la respuesta tengo una key en header de tipo 'Cache-Control'

        > Crear un nuevo test: (assert)
            - Comprobar que el valor de la posición '2' del array que devuelve el servicio de 
            la variable title es -> 'reprehenderit est deserunt velit ipsam'
            - Comprobar que existe una cookie con nombre '__cfduid'
            - Comprobar que experamos (con una aserción) un status 200

        > Crear un nuevo test:
            - Compruebe la interfaz de la respuesta de la url -> /photos
            - Añada el esquema a la libreria tiny validator
            - Comprobar que el json del esquema coincide con el de la respuesta real
    
    5º Revisar el runner de postman y comprobar que todo este bien

    6º Exportar la colleción y el environment, añadir los ficheros resultantes al proyecto y ejecutar newman
    y comprobar que esta todo correcto.





