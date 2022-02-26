# Ejemplo 5 - Flujo para un autocomplete y ejecución de código JavaScript

## :dart: Objetivos

- Automatizar el flujo para un elemento de autocomplete
- Ejecutar código JavaScript en el navegador utilizando Selenium


## Desarrollo

### Autocomplete

A continuación utilizaremos la siguiente [página](https://formy-project.herokuapp.com/autocomplete) que incluye un elemenot `autocomplete`, que conforme vamos escribiendo nos va mostrando opciones

![imagen](https://user-images.githubusercontent.com/5317347/155854008-91ac91cd-66dc-488c-af2d-4f12ac6f96ef.png)

Ahora crearemos nuestro siguiente archivo de pruebas para automatizar este flujo:

```java
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.By;

public class Autocomplete {
    public static void main(String[] args) throws InterruptedException {

        System.setProperty("webdriver.chrome.driver", "/Users/meaghanlewis/Downloads/chromedriver");

        WebDriver driver = new ChromeDriver();

        driver.get("https://formy-project.herokuapp.com/autocomplete");

        WebElement autocomplete = driver.findElement(By.id("autocomplete"));
        autocomplete.sendKeys("Colima, Roma Norte");
        Thread.sleep(1000);

        WebElement autocompleteResult = driver.findElement(By.className("pac-item"));
        autocompleteResult.click();

        driver.quit();
    }
}

```

Es importante notar la siguiente instrucción:

```java
Thread.sleep(1000);
```

Sie ejecutamos nuestra prueba sin esta instrucción fallará, porque no estamos dando el tiempo suficiente para que se muestren las distintas opciones. Por ello debemos esperar 1000 milisegundos (1 segundo)

A continuación implementa algo similar para la busqueda en Google.


### Ejecución de código JavaScript

#### JavaScriptExecutor

JavaScriptExecutor es una interfaz que ayuda a ejecutar JavaScript a través de Selenium Webdriver. JavaScriptExecutor proporciona dos métodos `executescript` y `executeAsyncScript` para ejecutar javascript en la ventana seleccionada o en la página actual.

![imagen](https://user-images.githubusercontent.com/5317347/155854277-503f1489-b2da-4297-a5e8-fb9e9c611df5.png)

En Selenium Webdriver, los selectores como XPath, CSS, etc. se utilizan para identificar y realizar operaciones en una página web.

En caso de que estos selectores no funcionen, puedes usar JavaScriptExecutor. Puedes usar JavaScriptExecutor para realizar una operación deseada en un elemento web.

Selenium es compatible con javaScriptExecutor. No hay necesidad de un plugin adicional. Solo necesitas importar (`org.openqa.selenium.JavascriptExecutor`) en el script para usar JavaScriptExecutor.
