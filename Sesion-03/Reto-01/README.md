# Reto 1 - Migrar pruebas de JUnit 4 a JUnit5 

## :dart: Objetivo

- Realizar la migración de pruebas de JUnit 4 a JUnit 5

## ⚙ Requisitos

- IntelliJ IDEA
- Java
- Gradle
- JUnit
- JUnit 5
- Code with me

## Desarrollo

Dado el siguiente código de una calculadora básica con pruebas en JUnit 4 migrar las pruebas a JUnit 5.

`Calculator.java`
```java
public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int multiply(int a, int b) {
        int result = 0;
        for (int i = 0; i < b; i++) {
            result = add(result,a);
        }
        return result;
    }
}
```

`CalculatorTest.java`
```java
public class CalculatorTest {
    private int a,b;
    
    
    @Before
    public void setUp(){
        a = ThreadLocalRandom.current().nextInt();
        b = ThreadLocalRandom.current().nextInt();
    }

    @Test
    public void testAdd() {       
        int result = calculator.add(a, b);

        assertEquals("Resultado incorrecto de la suma", a + b, result);
    }

    @Test(expected = Exception.class)
    public void testAddThrowsExceptionWhenIsCalledWithInvalidParams() {
        String c = "hello";
        int result = calculator.add(a, c);

        assertEquals("Resultado incorrecto de la suma", a + b, result);
    }

    @Test
    public void testMultiply() {
        int additionResult = calculator.add(a, b);

        assumeNotNull(additionResult);

        int multiplicationResult = calculator.multiply(a, b);

        Assertions.assertEquals("Resultado incorrecto de la multiplicación",a * b, multiplicationResult);
    }
}
```

<details>
  <summary>Solución</summary>


`build.gradle`
```
   plugins {
    id 'java'
}

group 'org.example'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'
    testImplementation 'org.junit.jupiter:junit-jupiter-params:5.8.1'
}

test {
    useJUnitPlatform()
}
```
    
`CalculatorTest.java`
```java
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.condition.EnabledIfEnvironmentVariable;
import org.junit.jupiter.api.condition.EnabledOnOs;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;
import org.junit.jupiter.params.provider.ValueSource;

import static org.junit.jupiter.api.Assertions.*;
import static org.junit.jupiter.api.condition.OS.*;

class CalculatorTest {

    @Test
    @EnabledOnOs(WINDOWS)
    void returns_the_sum_of_two_positive_numbers() {
        Calculator calculator = new Calculator();

        assertEquals(5, calculator.add(2,3));
    }

    @Test
    @EnabledOnOs({LINUX, MAC})
    void returns_the_sum_of_two_negative_numbers() {
        Calculator calculator = new Calculator();

        assertEquals(-3, calculator.add(-2,-1));
    }

    // Modifing env vars on windows https://www.computerhope.com/issues/ch000549.htm
    @Test
    @EnabledIfEnvironmentVariable(named = "ENV", matches = "development")
    void returns_the_sum_of_two_numbers_one_positive_and_one_negative() {
        Calculator calculator = new Calculator();

        assertEquals(-3, calculator.add(-2,-1));
    }


    // To run this we need to include the following dependency: testImplementation 'org.junit.jupiter:junit-jupiter-params:5.8.1'
    @ParameterizedTest
    @CsvSource({"1,1", "0,0", "5,3"})
    void returns_the_sum_of_two_numbers(int n1, int n2) {
        Calculator calculator = new Calculator();

        assertEquals(n1+n2, calculator.add(n1,n2));
    }


    @ParameterizedTest
    @CsvSource({"1,1", "0,10", "5,3"})
    void returns_the_multiplication_of_two_numbers(int n1, int n2) {
        Calculator calculator = new Calculator();

        assertEquals(n1*n2, calculator.multiply(n1,n2));
    }

    @Test
    @DisplayName("this is a different name")
    void returns_the_multiplication_of_two_positive_numbers() {
        Calculator calculator = new Calculator();

        assertEquals(6, calculator.multiply(2,3));
    }
}
```

</details>
