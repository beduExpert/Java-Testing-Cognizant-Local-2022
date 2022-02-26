# Ejemplo 4 - Selenium

## :dart: Objetivos

- Comparar y distinguir las diferencias entre las disntitas utilidades ofrecidas por Selenium


## Desarrollo

### Herramientas de Selenium

El Proyecto Selenium ofrece la API WebDriver, que es una poderosa API de cliente que tiene controladores para cada uno de los principales navegadores. La API permite llamadas nativas al navegador y emula acciones del usuario como: hacer clic, escribir e interactuar con elementos web. 

Los controladores del navegador son proporcionados por los proveedores del navegador. Anteriormente, Selenium era responsable del mantenimiento de todos los controladores, pero en la última versión, 3.0, los proveedores de navegadores que conocen y poseen el código de su navegador administrarán su propio controlador. 

La especificación W3C para la automatización de un navegador se basa en el controlador web de código abierto, por lo que habrá estándares y pautas sobre cómo se usa la API. 

Selenium WebDriver es la opción más popular y más utilizada. Pero también hay otros proyectos bajo el paraguas de Selenium. El primero es Selenium Grid. Selenium Grid proporciona un centro, o una ubicación central, para permitir que varias pruebas de Selenium se ejecuten simultáneamente en servidores locales y remotos en muchas plataformas y navegadores. Y permite que las pruebas se ejecuten mucho más rápido y con mucha más personalización.

También está el IDE de Selenium, este es un complemento de Firefox que registra cada interacción de una aplicación como pasos de prueba. Después de grabar todos estos pasos, se guardan como un script que se puede ejecutar una y otra vez. Con el código de prueba IDE se pueden generar pruebas mucho más rápido y fácil que nunca. El IDE es una excelente opción para aquellos que desean familiarizarse más con los localizadores de elementos y la creación de scripts de prueba. Sin embargo, los scripts creados a partir del IDE no se mantienen ni se amplían fácilmente con el tiempo. Debido a esto, se recomienda que aquellos que son nuevos en Selenium comiencen con el IDE y cuando se sientan cómodos con la funcionalidad, usen la API de WebDriver. 

En este curso, nos centraremos principalmente en Selenium WebDriver. Pero, no está de más conocer todas las ofertas de proyectos y lo que está disponible. 


### Selenium webdriver

A continuación procederemos a descargar el driver de selenium correspondiente a nuestra versión del navegador del siguiente [link](https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/), en este caso utilizaremos Chrome.

Iniciaremos un nuevo proyeto con Maven como manejador. Nuestro archivo `pom` contendra las siguientes dependencias

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>TestSample</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <java.version>1.8</java.version>
        <junit.version>4.12</junit.version>
    </properties>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.7.0</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-server</artifactId>
            <version>3.11.0</version>
        </dependency>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-chrome-driver</artifactId>
            <version>3.11.0</version>
        </dependency>

        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>${junit.version}</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```
Creamos un archivo de test con el siguiente contenido:

```java
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.By;

public class TestSample  {
    public static void main(String[] args) {

        // Set the property for webdriver.chrome.driver to be the location to your local              download of chromedriver
        System.setProperty("webdriver.chrome.driver", "chromedriver.exe");

        // Create new instance of ChromeDriver
        WebDriver driver = new ChromeDriver();

        // And now use this to visit Google
        driver.get("http://www.google.com");

        // Find the text input element by its name
        WebElement element = driver.findElement(By.name("q"));

        // Enter something to search for
        element.sendKeys("Bedu");

        // Now submit the form
        element.submit();

        //Close the browser
        driver.quit();
    }
}

```

Y procedemos a ejecutralo. Una nueva ventana del navegador debe de aparecer, ir a Google, realizar la busqueda y cerrar el navegador.
