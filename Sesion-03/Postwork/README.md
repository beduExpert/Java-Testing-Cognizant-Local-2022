# Postwork

[Ver en Google docs](https://docs.google.com/document/d/1WCMWMi-sLFNS9DE5Mph2jx67Ng4pvS_Ra4cAl2EqVO8/edit?usp=sharing)


## 馃幆 OBJETIVOS

- Comparar el funcionamiento de JUnit y TestNG en escenarios similares
- Analizar c贸mo funciona la ejecuci贸n en paralelo en JUnit 5
- Analizar c贸mo funciona la ejecuci贸n en paralelo en TestNG

## 馃殌 DESARROLLO

Antes de comenzar con la actividad te recomendamos revisar el siguiente recurso para que comprendas que hay detr谩s de la ejecuci贸n de pruebas en paralelo utilizando JUnit 5:

[Ejecuci贸n Paralela](https://junit.org/junit5/docs/5.3.0-M1/user-guide/index.html#writing-tests-parallel-execution)

Continuaremos con el desarrollo del software de entrevistadores y exploraremos la paralelizaci贸n de pruebas con JUnit realizando el siguiente ejercicio:

- Configura tu proyecto e instala las dependencias necesarias 

- Paralelizar la ejecuci贸n de tus pruebas

### Sigue estas instrucciones:

- En tu archivo build.grade asegurate de tener junit en su versi贸n 5.3 o superior
- En el mismo archivo asegurate que la configuraci贸n test luzca de la siguiente forma


```
test {
    useJUnitPlatform()
    systemProperty 'junit.jupiter.execution.parallel.enabled', 'true'
}
```

-Ejecuta las pruebas
-Cambia la configuraci贸n anterior a false y observa las diferencias en los tiempos de ejecuci贸n


Para cerrar nuestro postwork, revisemos el siguiente video que realiza un benchmark de la ejecuci贸n en paralelo entre diferentes frameworks de pruebas:

[驴Cu谩l tecnolog铆a es m谩s eficiente para ejecutar los tests en paralelo?](https://www.youtube.com/watch?v=omX2IQvHA1A)


## Indicaciones generales

驴Terminaste la actividad? responde las siguientes preguntas:

驴Notaste alguna diferencia en el tiempo de ejecuci贸n de las pruebas?
_________________________________________________________________________________________________________________________________________________________________________________________________________________________________

驴Qu茅 ventajas consideras que aporta la ejecuci贸n en paralelo?
_________________________________________________________________________________________________________________________________________________________________________________________________________________________________
驴Crees que existe alguna desventaja de ejecutar nuestras pruebas en paralelo?
_________________________________________________________________________________________________________________________________________________________________________________________________________________________________


隆Mucho 茅xito y reta tu potencial!

## 鉁? Checklist 

Aseg煤rate que tu postwork contenga todo lo siguiente, ya que esto se evaluar谩 al t茅rmino del m贸dulo.

- [ ] Tu archivo de configuraci贸n build.grade cuenta la configuraci贸n  systemProperty 'junit.jupiter.execution.parallel.enabled', 'true'  




- [ ] Tus pruebas se ejecutan en paralelo




- [ ] Al cambiar la configuraci贸n `systemProperty 'junit.jupiter.execution.parallel.enabled', 'false鈥檂 tus pruebas se ejecutan secuencialmente  







