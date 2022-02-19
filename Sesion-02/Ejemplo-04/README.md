# Ejemplo #4 - Mocka, Chai y otras herramientas

## :dart: Objetivo

- Reconocer la importancia de distintos frameworks de pruebas. 
- Analizar difernetes herramientas para pruebas .



## Desarrollo

### Mocha.js

Mocha es un framework de pruebas de JavaScript que se ejecuta en Node.js. Nos da la posibilidad de crear tanto tests síncronos como asíncronos de una forma muy sencilla. Nos proporciona muchas utilidades para la ejecución y el reporte de los tests.

### Chai.js

Es un librería de aserciones, la cual se puede emparejar con cualquier marco de pruebas de Javascript. Chai tiene varias interfaces: assert, expect y should, que permiten al desarrollador elegir el estilo que le resulte más legible y cómodo a la hora de desarrollar sus tests:

```
Assert:
assert.typeOf( foo, 'string', 'foo is a string' );
assert.equal( foo, 'bar', 'foo equal `bar`' );
assert.lengthOf( foo, 3, 'foo`s value has a length of 3' );
Expect:
expect( foo ).to.be.a( 'string' );
expect( foo ).to.equal( 'bar' );
expect( foo ).to.have.length( 3 );
Should:
foo.should.be.a( 'string' );
foo.should.equal( 'bar' );
foo.should.have.length( 3 );
```

### Opciones adicionales de Chai.js

#### Hooks

Se colocan dentro de un elemento de tipo describe y son muy útiles para algo tan simple y necesario como para inicializar una variable, limpiar la base de datos…

```
before(function() {
    // Se ejecuta antes de todas las pruebas del bloque
  });
  after(function() {
    // Se ejecuta después de todas las pruebas del bloque
  });
  beforeEach(function() {
    // Se ejecuta antes de cada prueba del bloque
  });
  afterEach(function() {
    // Se ejecuta después de cada prueba del bloque
  });
  ```
  
#### Exclusive Tests:

La función only() hace posible ejecutar solo el bloque o el caso de prueba al cual se lo añadamos. Es muy útil si tenemos un gran número de tests y por algún motivo queremos ejecutar un parte de ellos o incluso un único test.

  

```
describe.only('bloque con llamada a función only', function() {
    it.('test1, function() {
      // ...
    });
   it.('test2, function() {
      // ...
    });
 });
```


