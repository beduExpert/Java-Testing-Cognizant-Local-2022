# Ejemplo 6 - Automatizar formulario

## :dart: Objetivos

- Automatizar el flujo para completar un formulario


## Desarrollo

A continuación utilizaremos la siguiente [página](http://formy-project.herokuapp.com/form) que contiene un formulario

![imagen](https://user-images.githubusercontent.com/5317347/155855182-a0dda693-b30b-4a5b-a8a2-d36c676bff13.png)


Ahora crearemos nuestro siguiente archivo de pruebas para automatizar este flujo y validar que al completarlo correctamente nos muestra el mensaje esperado:

```java
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import static org.junit.Assert.assertEquals;

public class Form {
    public static void main(String[] args) {

        System.setProperty("webdriver.chrome.driver", "chromedriver.exe");

        WebDriver driver = new ChromeDriver();

        driver.get("https://formy-project.herokuapp.com/form");

        driver.findElement(By.id("first-name")).sendKeys("Juan");

        driver.findElement(By.id("last-name")).sendKeys("Perez");

        driver.findElement(By.id("job-title")).sendKeys("QA Engineer");

        driver.findElement(By.id("radio-button-2")).click();

        driver.findElement(By.id("checkbox-2")).click();

        driver.findElement(By.cssSelector("option[value='1']")).click();

        driver.findElement(By.id("datepicker")).sendKeys("05/28/2019");
        driver.findElement(By.id("datepicker")).sendKeys(Keys.RETURN);

        driver.findElement(By.cssSelector(".btn.btn-lg.btn-primary")).click();

        WebDriverWait wait = new WebDriverWait(driver, 10);
        WebElement alert = wait.until((ExpectedConditions.visibilityOfElementLocated(By.className("alert"))));

        String alertText = alert.getText();

        assertEquals("The form was successfully submitted!", alertText);

        driver.quit();
    }
}

```


