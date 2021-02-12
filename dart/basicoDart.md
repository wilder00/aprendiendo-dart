


## Funciones 

	Void(){
		var mensaje = saludar();
		print (mensaje);
	}
	
	String saludar(){
		return "hola";
	}


* creando funciones con parámetros:


	Void(){
		var mensaje = saludar("Hola", "fernando" );
		print (mensaje);
	}
	
	String saludar(String texto, String nombre){
		return "$texto $nombre"; //$ sirven para llamar a una variable declarada dentro de un string
	}


* Creando funciones con parametros Bien definidos para asegurar exactitud al momento de ingresar los valores

`

	Void(){
		var mensaje = saludar(nombre: "fernando", texto: "Hola,");
		print (mensaje);
	}
	
	String saludar({ String texto, String nombre }){ //Parámetro con nombre
		return "$texto $nombre";
	}
`
	

* Creando funciones tipo flechas:


``
Void(){
	var mensaje = saludar(nombre: "fernando", texto: "Hola,");
	print (mensaje);
}

String saludar({ String texto, String nombre }) => "$texto $nombre";
``



## Clases:

*creando clases:

	void main(){
		final wolverine = new Heroe( poder: "Regeneración"  ) // el new en dart es opcional de la versión 2 en adelante, en vez de var puede ser la clase Heroe, tambien un final que se parece a una cosntante
		
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
		
			return "nombre: ${ this.nombre } - poder: ${ this.poder } "
		}
	}
	

## Forma corta de definir propiedades de las clases

	void main(){
		final wolverine = new Heroe( poder: "Regeneración"  ) // el new en dart es opcional de la versión 2 en adelante, en vez de var puede ser la clase Heroe, tambien un final que se parece a una cosntante
		
		print(wolverine);
	}

	class Heroe{
		
		String nombre;
		String poder;
	        
		Heroe({ this.nombre, this.poder }){ //names arguments

		}
		
		
		String toString(){
		
			return "nombre: $nombre - poder: $poder "//no es necesario el this ya que dart se da cuenta de la existencia de esos atributos
		}
	}
		
	
## Constructores con nombre:
	
	import "dart.convert";
	

	void main(){
		//final wolverine = new Heroe("Lagan", "Regeneración";
		
		final rawJson = '{ "nombre": "Logan", "Poder": "Regeneración" }';
		
		final parsedjson = json.decode( rawJson );
		print( parsedjson ) // parsed json es un mapa

		final wolverine = new Heroe.fromJson(parsedJson);

		print(wolverine.nombre));
		print(wolverine.poder)
	}

	class Heroe{
		stirng nombre;
		string poder;

		Heroe(this.nombre, this.poder)
		
		Heroe.fromJson( Map parsedJson ){
			nombre = parsedJson["nombre"];
			poder = parsedJson["poder"];
		}
	}
	




























		
