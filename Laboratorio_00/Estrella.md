# Mecanismos que permiten nombres de dominio 
En este corto informe se buscará dar respuesta a la pregunta de ¿qué mecanismos permiten funcionar a nombres de dominio como **http://中文.tw/** **https://💩.la**?

## Dominios
Primero que todo, es necesario entender que es un dominio. Un dominio es una cadena de caracteres que identifica a una entidad en internet, en otras palabras, representan direcciones legibles por humanos para acceder a recursosen la web.
Los mismos los podemos dividir en dos casos, los dominios estándar y los dominios internacionales (IDN).

### Dominios estándar
Los dominios estándar son aquellos que solo contienen caracteres alfanuméricos (a-z, 0-9)y el guión medio (-). Estos dominios son los más comunes y son los que se han utilizado desde el inicio de internet. Un ejemplo de un dominio estándar es **www.google.com**.

### Dominios internacionales (IDN)
Los dominios internacionales son aquellos que contienen caracteres no ASCII, es decir, caracteres que no pertenecen al alfabeto inglés. Estos dominios permiten que los usuarios puedan acceder a sitios web utilizando su propio idioma. Un ejemplo de un dominio internacional es **http://中文.tw/**.
Para que se puedan utilizar estos dominios, es necesario que se utilice un sistema de codificación que permita la conversión de los caracteres no ASCII a un formato que pueda ser interpretado por los servidores DNS. El sistema de codificación que se utiliza es el **Punycode**. 

### Punycode
El **Punycode** es un sistema de codificación que permite representar cadenas de caracteres Unicode utilizando un subconjunto restringido de caracteres ASCII. Este sistema de codificación es utilizado para convertir los caracteres no ASCII a un formato que pueda ser interpretado por los servidores DNS.
El **Punycode** utiliza el formato **xn--** seguido de una cadena de caracteres ASCII que representa el dominio en formato **Punycode**. Un ejemplo de un dominio en formato **Punycode** es **http://xn--fiq228c.tw/**. Este dominio es equivalente a **http://中文.tw/**. 

## Mecanismos de trabajo
Los mecanismos que permiten el funcionamiento de los dominios internacionales son los siguientes:
1. **Registro de dominios**: Los dominios internacionales son registrados de la misma forma que los dominios estándar. La única diferencia es que se debe especificar que el dominio es internacional.
2. **Resolución de dominios**: Los dominios internacionales son resueltos de la misma forma que los dominios estándar. La única diferencia es que los servidores DNS deben ser capaces de interpretar los dominios internacionales. Para esto, los servidores DNS deben ser capaces de interpretar el formato **Punycode**.
3. **Navegación web**: Los navegadores web deben ser capaces de interpretar los dominios internacionales. Para esto, los navegadores web deben ser capaces de interpretar el formato **Punycode**.

## Ejercitación local
Si deseamos ver de forma simple como realizan esta conversión los registradores de dominios, podemos realizar el siguiente programa en python3 utilizando la librería `idna` que nos permite realizar la conversión de un dominio internacional a su formato **Punycode**.

```python
import idna

# Función que convierte un nombre de dominio a punycode
def convert_to_punycode(domain):
  try:
    # Convertir el nombre del dominio a punycode
    punycode = idna.encode(domain)
    # Decodificar el punycode a ascii
    return punycode.decode('ascii')
  # Capturar errores
  except idna.IDNAError as e:
    print("Error al convertir el nombre del dominio:", e)

# Nombre del dominio
nombre_dominio = "中文.tw"
print("El nombre del dominio es:", nombre_dominio)
# Convertir el nombre del dominio a punycode
punycode = convert_to_punycode(nombre_dominio)
print("El nombre del dominio punycode es:", punycode)
```
En este ejemplo, el nombre del dominio es **中文.tw**. Al ejecutar el programa, se obtiene que el nombre del dominio en formato **Punycode** es **xn--fiq228c.tw** impreso en la consola.

## Conclusión
Los dominios internacionales como **http://中文.tw/** y **https://💩.la** permiten que los usuarios puedan acceder a sitios web utilizando su propio idioma (o caracteres o emojis). Para que esto sea posible, es necesario que se utilice un sistema de codificación que permita la conversión de los caracteres no ASCII a un formato que pueda ser interpretado por los servidores DNS. El sistema de codificación que se utiliza es el **Punycode**. Los mecanismos que permiten el funcionamiento de los dominios internacionales son el registro de dominios, la resolución de dominios y la navegación web.

## Referencias
- https://en.wikipedia.org/wiki/Domain_name
- https://en.wikipedia.org/wiki/Internationalized_domain_name
- https://en.wikipedia.org/wiki/Punycode
- https://dinahosting.com/ayuda/que-es-punycode/
- https://pypi.org/project/idna/
- https://www.w3schools.com/python/python_try_except.asp