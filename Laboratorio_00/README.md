# Laboratorio 0: Aplicación Cliente
### Cátedra de Redes y Sistemas Distribuidos 2024


## Objetivos
- Aplicar la comunicación cliente/servidor por medio de la programación de sockets, desde la perspectiva del cliente.
- Familiarizarse con un protocolo de aplicación y su uso por medio de su RFC.
- Leer y comprender código Python no-trivial.


## Hget

hget es un cliente HTTP, desarrollado en Python 3, que obtiene una página desde un servidor y la almacena localmente en un archivo. El protocolo [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) está definido en el [RFC 2616](https://tools.ietf.org/html/rfc2616).


## Tarea

Descargar/clonar el kickstarter desde el repositorio en [Git](https://git.cs.famaf.unc.edu.ar/redes/lab-kickstarters/lab0-kickstarter)
```
$ git clone https://git.cs.famaf.unc.edu.ar/redes/lab-kickstarters/lab0-kickstarter.git
```
Deberán completar el cliente para que funcione. El código de hget está esencialmente ya escrito y se lo damos con solamente una de las funciones incompletas: ```connect_to_server()```.

```
    $ ls
    hget.py
    $ python3 hget.py http://respag.net/aspnet-web-pages.aspx
    Contactando servidor 'respag.net'...
    Contactando al servidor en 143.95.251.39...
    Enviando pedido...
    Esperando respuesta...
    $ ls
    download.html  hget.py
```
Luego de solicitar una página por su URL, obtenemos un archivo llamado download.html. Puede elegirse un nombre de archivo distinto con la opción -o:

```
    $ python3 hget.py http://www.columbia.edu/\~fdc/sample.html -o out.html
    Contactando servidor 'www.columbia.edu'...
    Contactando al servidor en 128.59.105.24...
    Enviando pedido...
    Esperando respuesta...
    $ ls
    download.html  out.html  hget.py
```

Nota: En el código pueden ver que las funciones tienen un docstring que describe su comportamiento. Además de funcionar como documentación, pueden ser utilizados como tests automáticos. Para ejecutar estos tests pueden hacer: 
```
    $ python3 -m doctest hget.py  
```
Además el archivo hget-test.py tiene tests adicionales que deben ser ejecutados con:
```
    $ python3 hget-test.py -v
```

## Tarea Estrella

Opcionalmente, y con la posibilidad de que se otorguen puntos extras en la evaluación parcial, se pide investigar qué mecanismos permiten funcionar a nombres de dominio como:
- http://中文.tw/
- https://💩.la

    Ayuda: investigue sobre el término “encoding”.

## Requisitos del codigo a entregar:
- No se solicita un informe para este laboratorio, salvo para el punto estrella, cuya respuesta deberá estar dada en texto plano o Markdown. Pero el código que escriban debe contener comentarios con detalles de lo que hicieron. 
- Las entregas serán a través del repositorio Git provisto por la Facultad para la Cátedra, con fecha límite el 30/3
- El código debe satisfacer PEP8
- La biblioteca de sockets de Python permite saltearse algunos pasos y omitir algunos argumentos si estamos usando los valores por defecto. No usen eso (para este Lab), así se ven los valores explícitos.