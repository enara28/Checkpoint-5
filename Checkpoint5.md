# Conceptos teóricos de Python

## ¿Qué es un condicional?

Una condicional nos permite delimitar el radio de acción de una función a una situación específica. Esto quiere decir que las acciones que encerremos dentro de la condicional solo se llevarán a cabo si la condición se cumple.

La sintaxis básica de las condicionales tiene tres elementos importantes: "if", "elif", else. Colocamos "if" (se traduciría como el "si" de una frase condicional en castellano) al comienzo de la condicional y después añadimos la condición que se debe cumplir seguida de dos puntos. Tras las acciones relacionadas con la condición, podemos añadir "elif" (responde a else if y quiere decir "y si...") para concatenar otra condición al mismo nivel y "else" (se traduciría como "si no...") que afectará a cualquier otra condición que no se englobe en cualquiera de las anteriores. Es importante recalcar que "elif" y "else" son opcionales.

A continuación, presento diferentes ejemplos que muestras posibles usos de las condicionales.
La primera es una condicional que podemos utilizar para restringir el acceso a una página, es decir, utilizaremos la condicional para crear un proceso de autentificación de un usuario en una página.

~~~
if usuario == "enara":
	print(f"Hola, {usuario}")
else:
	print("Acceso denegado")
~~~

Otro ejemplo sería utilizar la condicional para la autorización al ver una película para mayores de 16 años:

~~~
if usuario >=16:
	print(f"Hola, {usuario}")
else:
	print("Acceso denegado")
~~~

Si es una actividad para personas entre 18 y 25 años, podríamos hacer lo siguiente:

~~~
if usuario > 25:
	print("No puedes acceder")
elif usuario < 18:
	print("No puedes acceder")
else:
	print(f"Hola, {usuario}")
~~~

Hay varios operadores que podemos utilizar para crear las condicionales, algunas ya las he mencionado, pero esta es la lista completa:

- == operador de igualdad
- != operador de desigualdad
- <> operador de desigualdad; su uso ha quedado obsoleto
- < menor que
- \> mayor que
- <= menor que o igual a
- \>= mayor que o igual a

Además, tenemos formas de concatenar condicionales, para lo que utilizamos la siguiente sintaxis:
- if condicional and condicional => ambas condiciones se deben cumplir.
- if condicional or condicional => que se cumpla una de las dos condiciones es suficiente.
- if condicional and not condicional => la primera condición debe ser cierta y la segunda falsa, es decir, la primera debe cumplirse y la segunda tiene que no cumplirse.

Ejemplos:

~~~
if usuario == "enara" and constraseña == "1234":
~~~

En este caso se deben cumplir ambas condiciones para poder acceder.

~~~
if usuario > 25 or usuario < 18:
~~~

En este caso, el usuario debe ser o mayor de 25 o menor de 18.

Si no utilizamos operadores comparativos, estaremos pretendiendo que la variable, por ejemplo, sea verdad (True) para que se cumpla la condición.

***

## ¿Cuáles son los diferentes tipos de bucles en Python? ¿Por qué son útiles?

Tenemos dos tipos de bucles en Python: los for in y los while. Estos bucles nos permiten desarrollar una acción por cada elemento de una lista, de una cadena de caracteres, etc. En el caso de los for in, el bucle termina cuando se ha llegado al último elemento de la lista, cadena, etc. En cambio, los while requieren que le digamos cuando parar, de lo contrario, el bucle seguirá de forma infinita y esto puede generar problemas a nuestro sistema. A continuación, presentaré la sintaxis y el uso de estos bucles por medio de ejemplos:

~~~
números = [1, 2, 3, 4]
for número in números:
	print(número)
~~~

for e in son los elementos que generan el bucle, números hace referencia a la variable que hemos creado, donde el bucle irá de elemento en elemento. Por su parte, número hace referencia a cada elemento dentro de la lista, por lo que cuando decimos print(número), queremos decir que se impriman en la consola los números de la lista de uno en uno. Cada vuelta del bucle imprime el siguiente número hasta llegar al final; al terminar el bucle, este para sin que tengamos que hacer nada.

~~~
números = [1, 2, 3, 4]
contador = 0
while contador < 4:
	print(números.pop())
	contador += 1
~~~

En este caso, le decimos al bucle while que continúe siempre que el contador sea menor de 4, por lo que sabe cuando parar. Para ello, hemos tenido que crear una variable de contador y decirle al bucle que lo incremente por uno cada vuelta. Además, hemos vaciado la lista para imprimir cada número. Para este tipo de acciones, vemos que los for in son mucho más eficientes.

En general, optaremos por los bucles for in porque son más claros e intuitivos, pero habrá casos en los que se necesite un bucle while. En la siguiente página se explican diferentes casos en los que un bucle while es necesario o preferido ante un for in:

<https://www.snakify.org/es/lessons/while_loop/>

***

## ¿Qué es una lista por comprensión en Python?

Las listas por comprensión son una forma de crear listas de forma más compacta. Lo explicaré por medio de ejemplos para que sea más sencillo de comprender. Imaginemos que tenemos una lista con los números del 1 al 5 y queremos crear otra lista que contenga estos números multiplicados por 2. La forma de hacerlo sin utilizar las listas por comprensión sería la siguiente:

~~~
lista_1 = [1, 2, 3, 4, 5]
lista_2 = []
for num in list_1:
	lista_2.append(num*2)
~~~

Con la lista por comprensión se vería de la siguiente manera:

~~~
lista_1 = [1, 2, 3, 4, 5]
lista_2 = [num*2 for num in lista_1]
~~~

Estas dos líneas de código nos dan el mismo resultado que la forma anterior. Además, podríamos añadir a la lista una condicional al final. La sintaxis con todos los elementos sería la siguiente:

~~~
lista = [acción for x in y if condición]
~~~

***

## ¿Qué es un argumento en Python?

Los argumentos son elementos que utilizamos al definir una función y que se reemplazarán por valores al utilizar esta función. La manera más fácil de comprenderlo es mediante un ejemplo:

~~~
def nombre_de _función(argumento_1, argumento_2):
	acción de la función
~~~

En la función anterior vemos que los argumentos se colocan entre paréntesis pegados al nombre que le demos a la función. Los nombres que utilizemos para los argumentos pueden ser cualquier cosa que deseemos, pero se recomienda que representen su contenido de forma clara. Hay funciones que no necesitan argumentos y otras que tendrán una gran cantidad de ellos (la cantidad no está limitada). Cuando llamamos una función, utilizamos el nombre de la función y los paréntesis pegadas a ella, donde colocaremos los valores que queremos que se utilicen en la función y que reemplazan a los argumentos. Un breve ejemplo:

Definición de la función:

~~~
def nombre_completo(nombre, apellido):
	return f"{nombre} {apellido}"
~~~

Llamada de la función:

~~~
nombre_completo("enara", "armendariz")
~~~

La función devuelve la cadena formateada: "enara armendariz"

Podemos ver cómo se van a aplicar los argumentos en la función y sabemos qué tipo de valor reemplazará el argumento, porque los nombres que hemos elegido son explícitos.

En este caso hemos utilizado los argumentos por mapeo, es decir, el primer argumento se reemplaza con el primer valor (nombre => "enara") y el segundo con el segundo (apellido => "armendariz"); pero hay más tipos de argumentos:

- Si no conocemos el orden de los argumentos, podemos llamarlos del siguiente modo: argumento = "valor". Siguiendo con el ejemplo anterior:

~~~
nombre_completo(nombre = "enara", apellido = "armendariz")
~~~

- Si tenemos una cantidad indeterminada de argumentos, utilizamos *args como argumento, lo que nos permitirá utilizar los valores que queramos al llamar la función. El nombre args no es obligatorio, podríamos utilizar cualquier nombre, pero es una convención utilizar args. Ejemplo:

~~~
def nombre_completo(*args):
	print(args)
~~~

Esta función nos devuelve los valores que introduzcamos en forma de tupla y hay que tener en cuenta que, al usarse el argumento en la función, no lleva el asterisco.

`saludo("enara", "armendariz", "aramendia")` => devuelve `("enara", "armendariz", "aramendia")`, lo que es una tupla. Si queremos conseguir el resultado de las funciones anteriores, debemos añadir la función `.join()` que une los valores intercalando el elemento que añadamos:

~~~
def saludo(*args):
	print(" ".join(args))
~~~

- Por último, tenemos los argumentos con clave que, de forma convencional, se crean así: **kwargs. Son argumentos opcionales y generan diccionarios cuando los llamamos. Al ser opcionales, podemos crear condicionales con ellos:

Podemos utilizar la clave o no:

Definición:

~~~
def saludo(**kwargs):
	if kwargs:
		print(f"Hola, {kwargs[nombre]} {kwargs[apellido]} ")
~~~

Llamada:

`saludo(nombre= "enara", apellido = "armendariz")` => `"Hola, enara armendariz"`

Definición:

~~~
def tareas(**kwargs):
	if kwargs:
		for key, val in kwargs.items():
			print(f"{key}=>{val}")
~~~

Llamada:

`tareas(primero = "lavadora", segundo = "basura")` => Imprime:

~~~
primero=>lavadora
segundo=>basura
~~~

Como se puede observar, en este último caso se ha tratado el argumento como un diccionario y se ha podido imprimir tanto la clave como el valor.

Todos los tipos de argumentos que se han mencionado en este apartado se pueden combinar entre sí.

***

## ¿Qué es una función Lambda en Python?

Las funciones lambda son funciones anónimas, es decir, no definimos su nombre, por lo que no se pueden reutilizar. Nos permiten generar una función de forma reducida y se suelen utilizar cuando las funciones son breves y no necesitamos utilizarlas en otra parte de la aplicación. Se pueden guardar en variables, utilizar dentro de funciones que creemos, etc. La sintaxis para utilizarlas es la siguiente:

~~~
lambda argumentos: acción
~~~

La mejor forma de entender cómo funcionan es por medio de un ejemplo y en comparación con una función común.

Queremos crear una función que sume dos números de forma dinámica:

~~~
lambda num_1, num_2: num_1 + num_2
~~~

"lambda" es lo que utilizamos para crear la función, num_1 y num_2 son los argumentos que hemos añadido (la cantidad de argumentos no está limitada a dos). Tras los argumentos, colocamos los dos puntos y la acción, en este caso, la suma de los dos argumentos. Podríamos guardar esta función en una variable para llamarla en otra parte del programa del siguiente modo: nombre_de_variable(valores que queremos pasar a la función).

Si quisiéramos crear la función anterior de manera convencional:

~~~
def suma(num_1, num_2):
	return num_1 + num_2
~~~

En el siguiente enlace encontraráa más casos de uso de funciones lambda:

<https://www.freecodecamp.org/espanol/news/expresiones-lambda-en-python/>

***

## ¿Qué es un paquete pip?

Pip es un sistema que nos permite gestionar e instalar paquetes de Python. Por su parte, un paquete es una carpeta que contiene módulos de Python (documentos escritos en lenguaje Python) que podemos utilizar en nuestros programas. Estos paquetes nos facilitan el trabajo, ya que nos dan acceso a funciones que han creado otros programadores. Para poder utilizarlos necesitamos, primero, descargar e instalar el programa pip a través del siguiente enlace:

<https://pypi.org/project/pip/>

Después, instalamos y ejecutamos el programa desde nuestra línea de comandos.

Tras instalar pip, podremos instalar los distintos paquetes a los que tenemos acceso desde el [Índice de Paquetes de Python](https://pypi.org/), además de otros índices. Para poder utilizar los paquetes, los instalaremos desde nuestra línea de comandos de la siguiente manera:

~~~
nombre_del_paquete install
~~~

Cuando tengamos el paquete instalado correctamente, podremos utilizarlo en nuestros programas importando el paquete, un módulo específico o una función concreta. La sintaxis para importar un módulo es la siguiente:

~~~
from nombre_del_paquete import nombre_del_módulo
~~~