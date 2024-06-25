# Pokedex

#Librería para hacer peticiones HTTP.
import requests
#Librería para trabajar con datos en formato JSON.
import json
#Librería para interactuar con el sistema operativo.
import os

#Definimos la función y tomamos como parámetro nombre que es el nombre del pokemón que se quiere consultar.
def obtener_datos_pokemon(nombre):
#Colocamos la url con la API de PokeAPI.
    url = f"https://pokeapi.co/api/v2/pokemon/{nombre.lower()}"
#Hacemos la petición HTTP GET a la url y almacena la respuesta en la variable respuesta.
    respuesta = requests.get(url)
    
#Comprobamos la petición fue exitosa.
    if respuesta.status_code == 200:
#Convierte la respuesta JSON en un diccionario de python y la guarda en la variable data.
        data = respuesta.json()

  #Agregamos la url de la imagen  del Pokémon que se quiere consultar.
        imagen_url = data['sprites']['front_default']

  #Se muestra el peso y tamaño del pokemón.
        peso = data['weight']
        tamaño = data['height']

   #Se muestran las habilidades en forma de lista.
        habilidades = [ability['ability']['name'] for ability in data['abilities']]
        
   #Se muestra el tipo de pokemón en forma de lista.
        tipos = [type['type']['name'] for type in data['types']]

   #Mostramos la información completa del pokemón a consultar.
        print(f"Imagen del Pokémon: {imagen_url}")
        print(f"Peso: {peso}")
        print(f"Tamaño: {tamaño}")
        print("Movimientos:") 
  #Con los bucles for se muestra la manera de imprimir movimientos, habilidades y tipos en forma de list numerada.
        for idx, move in enumerate (movimientos, start=1):
            print(f"{idx}. {move}")
        print("Habilidades:") 
        for idx, ability in enumerate (habilidades, start=1):
            print(f"{idx}. {ability}")
        print("Tipo de Pokemón:") 
        for idx, type in enumerate (tipos, start=1):
            print(f"{idx}. {type}")

  #Guarda la información en un archivo JSON.
        pokemon_info = {
            "nombre": nombre.capitalize(),
            "imagen": imagen_url,
            "peso": peso,
            "tamaño": tamaño,
            "movimientos": movimientos,
            "habilidades": habilidades,
            "tipos": tipos
        }

   #Crea una carpeta pokédex si no existe.
        if not os.path.exists('pokedex'):
            os.makedirs('pokedex')

   #Guarda en un archivo JSON dentro de la carpeta pokédex.
        with open(f"pokedex/{nombre.lower()}.json", 'w') as outfile:
            json.dump(pokemon_info, outfile, indent=4)
  #Si el nombre ingresado del pokemón no es correcto mostrará en pantalla el mensaje de error.
    else:
        print(f"No se encontró un Pokémon con el nombre '{nombre}'.")

   #Pide al usuario que introduzca el nombre de un pokemón a consultar y llama a la función obtener_datos_pokemón.
   
     nombre_pokemon = input("Introduce el nombre de un Pokémon: ")
     obtener_datos_pokemon(nombre_pokemon)

==================================================================================================================================================

# Reflexión:
Con este código aprendí a usar la librería requests, json y os y el usar archivos HTTPP, a pesar de tener dificultades para poder compilar el código y se muestre la información correctamente, ya que en Visual Studio Code no podía acceder a la consola, descargué el editor de código Spyder donde logré acceder y editar de manera más fluida.
Aquí dejó las imágenes del código compilado y la imagen del pokemón :).

![codigo](https://github.com/AlexandraRosales/Pokedex/assets/89891121/1781d1ac-eec3-4553-99a5-ad8b94fc001a)
![codigo1](https://github.com/AlexandraRosales/Pokedex/assets/89891121/cee7ec60-db54-4295-95aa-017ab47a2e32)
![codigo2](https://github.com/AlexandraRosales/Pokedex/assets/89891121/e67ecbf1-647e-43ed-8655-4da3b7bebfa9)
![codigo3](https://github.com/AlexandraRosales/Pokedex/assets/89891121/09ebd7c7-ef1c-41ce-80a5-68138a9e6b27)
![130](https://github.com/AlexandraRosales/Pokedex/assets/89891121/69065d05-01c4-4edb-8171-0cceec7dc34f)
