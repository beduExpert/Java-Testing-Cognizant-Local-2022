# Reto 3 - Entrada de teclado y mouse


## Objetivo

Automatizar la interacción del teclado y mouse con una página web

## ⚙ Requisitos

- IntelliJ IDEA
- Java
- Gradle
- JUnit
- Selenium
- Code with me
- Una cuenta de GitHub

## Desarrollo

### Instrucciones:

- Durante este ejercico utilizaremos el siguiente sitio: http://formy-project.herokuapp.com/keypress
- Crea una nueva prueba en tu proyecto con el nombre `TestSample2.java`
- Coloca el siguiente contenido en el archivo que acabas de crear

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class TestSample2 {
    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "chromedriver.exe");
        WebDriver driver = new ChromeDriver();

        driver.get("http://formy-project.herokuapp.com/keypress");
         
        driver.quit();
    }
}

```

- Agreda el código necesario para:
  - Obtener el elemento `input` utilizando su id
  - Añadir tu nombre al `input` (puede utilizar el metodo `sendKeys`)
  - Obtener el elemento `button` utilizando su id
  - Da click en el elemento `button`
  - Cierra el navegador

<details>
  <summary>Solución</summary>

`TestSample2.java`
```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class TestSample2 {
    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "chromedriver.exe");
        WebDriver driver = new ChromeDriver();

        driver.get("http://formy-project.herokuapp.com/keypress");

        WebElement name = driver.findElement(By.id("name"));
        name.click();
        name.sendKeys("Bedu");

        WebElement button = driver.findElement(By.id("button"));
        button.click();

        driver.quit();
    }
}
```


</details>
