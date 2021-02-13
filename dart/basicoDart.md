

## Funciones 


	void main(){
		var mensaje = saludar();
		print (mensaje);
	}
	
	String saludar(){
		return "hola";
	}


* creando funciones con parámetros

```
	void main(){
	var mensaje = saludar("Hola", "fernando" );
		print (mensaje);
	}
	
	String saludar(String texto, String nombre){
		return "$texto $nombre"; //$ sirven para llamar a una variable declarada dentro de un string
	}
```

* Creando funciones con parametros Bien definidos para asegurar exactitud al momento de ingresar los valores


```
	void main(){
		var mensaje = saludar(nombre: "fernando", texto: "Hola,");
		print (mensaje);
	}
	
	String saludar({ String texto, String nombre }){ //Parámetro con nombre
		return "$texto $nombre";
	}
```

* Creando funciones tipo flechas:

```
	void main(){
		var mensaje = saludar(nombre: "fernando", texto: "Hola,");
		print (mensaje);
	}

	String saludar({ String texto, String nombre }) => "$texto $nombre";
```


## Clases:

*creando clases:

	void main(){
		final wolverine = new Heroe( poder: "Regeneración"  ); // el new en dart es opcional de la versión 2 en adelante, en vez de var puede ser la clase Heroe, tambien un final que se parece a una cosntante
		
		print(wolverine);
	}

	class Heroe{
		
		String nombre;
		String poder;
	        
		Heroe({ String nombre = "sin nombre", String poder }){ //names arguments
			this.nombre = nombre;
			this.poder = poder;
		}
		
		
		String toString(){
		
			return "nombre: ${ this.nombre } - poder: ${ this.poder } ";
		}
	}
	

## Forma corta de definir propiedades de las clases

	void main(){
		final wolverine = new Heroe( poder: "Regeneración"  ); // el new en dart es opcional de la versión 2 en adelante, en vez de var puede ser la clase Heroe, tambien un final que se parece a una cosntante
		
		print(wolverine);
	}

	class Heroe{
		
		String nombre;
		String poder;
	        
		Heroe({ this.nombre, this.poder }){ //names arguments

		}
		
		
		String toString(){
		
			return "nombre: $nombre - poder: $poder "; //no es necesario el this ya que dart se da cuenta de la existencia de esos atributos
		}
	}
		
	
## Constructores con nombre:

	
```
import "dart:convert";


void main(){
	//final wolverine = new Heroe("Lagan", "Regeneración";
	
	final rawJson = '{ "nombre": "Logan", "poder": "Regeneración" }';
	
	final parsedJson = json.decode( rawJson );
	print( parsedJson ); // parsed json es un mapa

	final wolverine = new Heroe.fromJson(parsedJson);

	print(wolverine.nombre);
	print(wolverine.poder);
}

class Heroe{
  String nombre;
	String poder;

	Heroe(this.nombre, this.poder);
	
	Heroe.fromJson( Map parsedJson ){
		nombre = parsedJson["nombre"];
		poder = parsedJson["poder"];
	}
}

```



## getter and setters

```
void main(){
	final cuadrado = new Cuadrado();

	cuadrado.lado = 10; // estamos usando el setter lado para dar valor a _lado
	
	print( cuadrado );
	print( 'área: ${ cuadrado.area }' ); // obtenemos area con su getter
}

class Cuadrado{

	double _lado; //con guión bajo se declara como privado la variable
	//double _area;

	set lado( double valor ){
		if( valor <= 0 ){
			throw( "El lado no puede ser menor o igual a 0" );
		}
		
		_lado = valor;
	}
	
	double get area{  // el getter no lleva parentesis.  [ tipo de dato, la funcion get ,  nombre para el exterior]
		return _lado * _lado;
	}
	//otra forma
	// double get area => _lado * _lado;

	toString()=>'Lado: $_lado';
}



```

## Clases Abstractas

Las clases abstractad nos van a servir para obligar a otras clases a implementar los métodos y propiedades establecidos

```

void main(){
	// final perro = new Animal() // no funcionará porque Animal es una clase abstract
	
	final perro = new Perro();
	perro.emitirSonido();

	final gato = new Gato();
	gato.emitirSonido();
}

abstract class Animal{
	int patas;
	
	void emitirSonido();
	
}

class Perro implements Animal{
	int patas;
	int colas;

void emitirSonido() => print("GUAAAUUUU!!!");

}

class Gato implements Animal{
	int patas;
	
	void emitirSonido() => print("MIAAUUU!!!!");
}

```




## Extends

```
void main(){
	
	final superman = new Heroe();
	superman.nombre = "Clark kent";	

	final luthor = new Villano(); 
	luthor.nombre = "Lex Luthor";
	
}

abstract class Personaje { // con abstract evitamos que se instancie una clase Personaje porque no es completo, solo define las bases de los personajes
	String poder;
	String nombre;
}


class Heroe extends Personaje{
	int valentia;

}

class Villano extends Personaje{
	int maldad;
}

```


## Mixins
para entender los mixins es recomendable utilizar el siguiente [enlace](https://medium.com/flutter-community/dart-what-are-mixins-3a72344011f3)

```


abstract class Animal{
	
}

abstract class Mamifero extends Animal{
	
}

abstract class Ave extends Animal{

}
abstract class Pez extends Animal{

}


abstract class Volador{  // en vez de class se puede poner mixin
	void volar() => print("Estoy volando!! ");
}

abstract class Caminante{
	void caminar() => print("Estoy caminando!! ");
}

abstract class Nadador{
	void nadar() => print("Estoy Nadando!! ");
}

class Delfin extends Mamifero with Nadador{}

class Murcielago extends Mamifero with Caminante, Volador{}

class Gato extends Mamifero with Caminante{}

class Paloma extends Ave with Caminante, Volador{}

class Pato extends Ave with Caminante, Volador, Nadador{}

class Tiburon extends Pez with Nadador{}

class PezVolador extends Pez with Nadador, Volador{}

void main(){
	final pato = new Pato();
	pato.volar();
	pato.caminar();
	pato.nadar();

	final pezVolador = new PezVolador();
	pezVolador.volar();

}


```

## Futures
Es similar a promesas en javascript
Tarea Asincrona que se realiza en un hilo independiende al hilo principal y cuando se resuelve nosotros podemos obtenerlo y seguir con la tarea.

```
// el Future se usa como una lista, es un tipo de retorno de datos.

Future<String> httpGet(String url){ // <String> se puede definir cualquier tipo de variable, httpGet es el nombre de la funición que le pusimos
	//ya que hemos especificado que httpGet debe retornar un dato tipo Future<String> hacemos un return con Future utilizando su constructor nombrado delayed
	return Future.delayed( new Duration( seconds: 4 ), (){ //El constructor delayed pide un parámetro de clase Duration, el cual es pasado como instancia que necesita un parámetro nombrado seconds [Argumento con nombre]
		return "Hola Mundo";	//el segundo parámetro de delayed es una función a ejecutarse depués de una duración.
	} );
}


void main(){
	print("Estamos a punto de pedir todos");
	
	httpGet("http://seudoAPI_solo texto").then( (data){
		print(data);
	
	} );
	print( "ultima línea ");
}

//RESULTADO:
// Estamos a punto de pedir todos
// ultima línea
// Hola Mundo

```

## Async Await
Async : permite transformar una función en una tarea asincrona
Await : permite esperar hasta que se resuelva el Async, ya sea que de un error o se resuelva

```
// se busca un resultado:
// EStamos a punto de pedir todos
// Hola Mundo
// ultima linea

void main() async {
	
	print("Estamos a punto de pedir todos");
	
	//String data = httpGet("https://api.nadaasdf"); //un future que regresa un String no es compatible con un String normal, a menos que se le ponga un Await que resilverá el Future para que regrese un string normal
	String data = await httpGet("https://api.nadaasdf"); //await solo puede funcionar si está dentro de un async
	
	print( data );
  	print('Ultima línea');
}


Future<String> httpGet(String url){ 
	
	return Future.delayed( new Duration( seconds: 4 ), (){ 
		return "Hola Mundo";
	} );
}

/*
Class Heroe{
	Heroe() async{ //no se puede usar async con un constructor 
		
	}
}
*/

```
