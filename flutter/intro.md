# Introducción a flutter

## ¿Qué es un widget?

Es una clase que puede tener argumentos posiciones y argumentos con nombre. Todo en flutter son widgets.
Son Como bloques de lego.
Ejemplos:

```
AppBar(
	title: Text( "Hola Mundo" ),
)

```

```
FloatingActionButton(
	onPressed: null,
	child: Icon( Icons.add ),
)
```

Analizando la Clase AppBar:

```
AppBar(
	title: Text( "Hola Mundo" ),
)

//la clase Text( "Hola Mundo" )

class Text{
	String mensaje;
	Text(this.mensaje); //constructor
}

//la clase AppBar

class AppBar {
	Text title;
	AppBar({ this.title }); //constructor
}

//Metiendolo en una variable

final appBar = new AppBar(
	title: Text( "Hola" )
);
```
hay dos tipos de widgets, ambos son clases abstractas.

### StatelessWidget

sin estado, no puede seguir los cambios de sus propiedades.
ejemplo:

```
class ContactoScreen{
	final nombre = "Fernando";
}
```
- No puede redibujarse a si mismo porque no tiene el método.

### StatefullWidget

con estado, permite al widget seguir su estado, saber si alguna de su propiedad cambie.
Ejemplo:

```
class ContactoScreen{
	String nombre = "Fernando";
}
```
- Puede redibujarse cuando sucede algún cámbio.

---

## Arbol de widget

Siempre hay un widget principal, y las demás se ramifican. El problema estaría en cómo pasar datos entre ellos.


## Estructura de un proyecto en flutter

* .gitignore : archivo para ignorar otros archivos para el control de versiones
* lib : La carpeta en la que estaremos trabajando la mayor parte del tiempo
* Android: carpeta que contiene la aplicación de android y contienen archivos que pueden ser generador por el framework
* build: Se encuentra los archivos que se van a correr en el modo desarrollo o produccion de android
* test: carpeta para desarrollar pruebas
* .metadata: archivo que genera el proyecto y es modificada de forma automática, le sirve a flutter para hacer su seguimiento.
* .package: otro archivo que no debemos tocar.
* flutter_app2: es un archivo que tiene el nombre de la app segun el nombre del proyecto generado
* pubspec.lock : dice al proyecto de qué manera es contruida el archivo pubspec.yaml, pobspec.lock es un archivo que no debemos tocar.
* pubspec.yaml : es un archivo manipulable, es como el package.json, es un archivo que permite instalar de forma remota las dependencias de la aplicación, dependencias de desarrollo. Las tabulaciones son importantes. ```flutter packages get ``` es el comando para actualizar los packetes registrados en pubspec.yaml, si eliminamos algun paquete registrado con el comando lo actualizamos en el proyecto. Por defecto dispara este comando de forma automática. Para que el proyecto corriendo vizualice los cambios se debe hacer un full restart. ¿¿(bondol)??
* README.md : es un archivo para describir el proyecto.



