
## Mostrar la Api a consultar

https://jsonplaceholder.typicode.com/


## Crear colleción

## Mostrar los Environments

## Crear la primera petición y guardarla en una collecion

https://jsonplaceholder.typicode.com/users


## Mostrar los test

/users


pm.test('nombre_del_test', function() {
    // sintaxis que contendrá todos las pruebas
});

pm.test("the server response is correct", function () {
     pm.response.to.not.be.error;
     pm.response.to.be.ok; // equivalente a decir que valide que sea 200
     pm.response.to.have.status; // equivalente a decir que valide que sea 200
     pm.response.to.be.withBody; // body tiene que exitir
     pm.response.to.be.json; // además que sea un JSON válido
});

// Pedimos a nuestro response payload que tengo Content-Type en el header
pm.test("Content-Type is present", function () {
    pm.response.to.have.header("Content-Type");
});

// Y comprobamos que la petición se haya servido en un determinado tiempo
pm.test("Response time is less than 200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(200);
});

## Mostrar como comprobar el valor de la respuesta

/users

pm.test('response value', function() {
    var jsonData = pm.response.json();
    pm.expect(jsonData[0].id).to.eql(1);

pm.test('async test', function (done) {
    setTimeout(() => {
        pm.expect(pm.response.code).to.equal(200);
        pm.expect(pm.response).to.have.property('code', 200);
        pm.expect(pm.response).to.have.property('status', 'OK');
        done();
    }, 1500);
});

## to.have

pm.response.to.have.status(code:Number)
pm.response.to.have.status(reason:String)
pm.response.to.have.header(key:String)
pm.response.to.have.header(key:String, optionalValue:String)
pm.response.to.have.body()
pm.response.to.have.body(optionalValue:String)
pm.response.to.have.body(optionalValue:RegExp)
pm.response.to.have.jsonBody()
pm.response.to.have.jsonBody(optionalExpectEqual:Object)
pm.response.to.have.jsonBody(optionalExpectPath:String)
pm.response.to.have.jsonBody(optionalExpectPath:String, optionalValue:*)
pm.response.to.have.jsonSchema(schema:Object)
pm.response.to.have.jsonSchema(schema:Object, ajvOptions:Object)

##  to.be
pm.response.to.be.info // Comprueba el código de estado 1XX

pm.response.to.be.success // Comprueba el código de estado 2XX

pm.response.to.be.redirection // Comprueba el código de estado 3XX

pm.response.to.be.clientError // Comprueba el código de estado 4XX

pm.response.to.be.serverError // Comprueba el código de estado 5XX

pm.response.to.be.error // Comprueba el código de estado 4XX o 5XX

pm.response.to.be.ok // El código de estado debe ser 200

pm.response.to.be.accepted // El código de estado debe ser 202

pm.response.to.be.badRequest // El código de estado debe ser 400

pm.response.to.be.unauthorized // El código de estado debe ser 401

pm.response.to.be.forbidden // Código de estado 403

pm.response.to.be.notFound // El código de estado de respuesta se verifica como 404

pm.response.to.be.rateLimited // Comprueba si el código de estado de respuesta es 429

## asserts

https://learning.postman.com/docs/postman/scripts/test-examples/#assertion-library-examples


## Esquema


// Postman integra la librería Tiny Validator que usa las especificaciones de JSON schema v4
para validar objetos JSON, lo cual nos facilita mucho el trabajo.

var schema = {
    "type": "object",
    "items": { "$ref": "mainSchema" }
};

var mainSchema = {
    "properties": {
        "id": { "type": "integer" },
        "name": { "type": "string" },
        "username": { "type": "string" },
        "email": { "type": "string" },
        "address": { "$ref": "addressSchema" },
        "phone": { "type": "string" },
        "website": { "type": "string" },
        "company": { "$ref": "companySchema" },
    }
};

var addressSchema = {
    "properties": {
        "street": { "type": "string" },
        "suite": { "type": "string" },
        "city": { "type": "string" },
        "zipcode": { "type": "string" },
        "geo": { "$ref": "geoSchema" }
    }
};

var geoSchema = {
    "properties": {
        "lat": { "type": "string" },
        "lng": { "type": "string" }
    }
};

var companySchema = {
    "properties": {
        "name": { "type": "string" },
        "catchPhrase": { "type": "string" },
        "bs": { "type": "string" }
    }
};

tv4.addSchema('mainSchema', mainSchema);
tv4.addSchema('addressSchema', addressSchema);
tv4.addSchema('geoSchema', geoSchema);
tv4.addSchema('companySchema', companySchema);

pm.test('schema is valid', function () {
    pm.expect(tv4.validate(pm.response.json(), mainSchema)).to.be.true;
});


## Mostrar runner Postman

## Mostrar newman

newman run -e dev.postman_environment.json curso-testing.postman_collection.json

## Comandos pm 

https://learning.postman.com/docs/postman/scripts/postman-sandbox-api-reference/