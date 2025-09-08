# Laboratorio-2
## Elaborado por: Laura Rodríguez y Diana Bernal 
## 1. Coreografía con Pepper desde Choregraphe
Primeramente se realiza la instalacion de Choregraphe
<img width="866" height="529" alt="image" src="https://github.com/user-attachments/assets/d566e1ec-ac58-49dd-b417-a19fd0745125" />

Ingresamos a Choreographe y veremos lo siguiente
<img width="1918" height="1015" alt="image" src="https://github.com/user-attachments/assets/f69281b7-ddb1-4ca4-8965-1bbac56e9e21" />
Importante, conectarse a la misma red de Pepper, osea, "Ciego"</br>

Al conectarse hacemos click en el icono de red y aparecera esta pantalla y deberia aparecer la opción de seleccionar a pepper.
<img width="888" height="576" alt="image" src="https://github.com/user-attachments/assets/5c4fbc5c-7206-4565-850e-0d20e0c9ab58" />

Luego de seleccionarlo apareceran todas las librerias y archivos que tiene Pepper para realizar movimientos y todo lo que Pepper puede hacer.</br>
Al visulizar sus carpetas veremos los bloques y podremos hacer las conexiones para crear la coreografia que queramos, como se observa a continuación:
<img width="1102" height="703" alt="image" src="https://github.com/user-attachments/assets/d71cb368-8a0f-40c2-bd15-65ca59442cae" />
Le damos click en el icono de ejecutar y Pepper iniciara a moverse tal y como se modifico los bloques en choreographe:</br>

Video Pepper coreografia:</br>

## 2. Coreografía con Pepper desde Ubuntu
Para realizar una coreografía con Pepper es necesario seguir una serie de pasos. Lo primero, es el ingreso al terminal de Ubuntu y conectarnos con Pepper. A continuación, se escribirá como son los comandos de conexión con él:</br>
+ ssh nao@192.168.0.104 </br>

Inmediatamente el terminal pedirá una contraseña de acceso se debe escribir:
+ nao

Lo siguiente a realizar es ingresar a los directorios de Pepper. Para ello, se debe digitar el siguiente comando:</br>

+ cd

Para visualizar los directorios que hay dentro de Pepper es necesario digitar el siguiente comando:</br>

+ ls

En nuestro caso, se ingresó a uno llamado "Presentaciones" con el siguiente comando:</br>

+ cd presentaciones/

Dentro de él, se creó un nuevo archivo tipo py (Python) que es el que fue el que permitió  que se realizara código con Lenguaje Python. Para ello, se empleó la siguiente línea de instrucción: </br>

+ nano Lab2.py

Después del paso anterior, se tuvo en cuenta una serie de librerías que son necesarias importar para lograr el funcionamiento correcto de Pepper. La librerías que se emplearon son las siguientes: </br>

+ import qi
+ import argparse
+ import sys
+ import almath
+ import math
+ import motion
+ import time
+ import webbrowser
+ import os

Luego de esto, se realizó la conexión con Pepper empleando los siguientes comandos: </br>

+ session = qi.Session()
+ session.connect("tcp://192.168.0.104:9559")

Para lograr el resultado obtenido en la Coreografía, fue esencial el uso de tres invocaciones. Las cuales serán mostradas enseguida: </br>

+ animated_speech_service = session.service("ALAnimatedSpeech")
+ motion_service = session.service("ALMotion")
+ tablet_service=session.service("ALTabletService")

Para mostrar una imagen, se debe emplear la siguiente línea de instrucción: 

+ tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen3.jpg")

Para lograr el movimiento del Robot, se debe usar lo siguiente:

+ motion_service.setAngles(["LShoulderPitch","RShoulderPitch"], [0.0, 0.0], 0.5)

De lo anterior, es importante mencionar que lo que se encuentra en comillas son las partes del cuerpo de Pepper. Por ende, ahí se debe poner la parte del cuerpo que se desea mover. En el caso anterior, ahí se mueven los hombros. </br>

Por otro lado para que Pepper hable, se debe usar el siguiente comando: </br>

+ animated_speech_service.say("Hola Soy Pepper ")

En el caso de un video en la Tablet , se debe usar las siguientes líneas de código: </br>

+ tablet_service.enableWifi()
+ tablet_service.playVideo("http://198.18.0.1/apps/usta/Banca.mp4")

Dicho esto, es necesario tener en cuenta los tiempos para que en el coreografía halla una sincronía y empiece a tomar forma la presentación de Pepper. El comando para lograrlo es el siguiente: </br>

+ time.sleep(164)

Basicamente la coreografía que se logró fue mediante lo explicado anteriormente. Ahora, se presentará el resultado del código de Python completo: </br>


         import qi
         import argparse
         import sys
         import almath
         import math
         import motion
         import time
         import webbrowser
         import os

         session = qi.Session()
         session.connect("tcp://192.168.0.104:9559")
         animated_speech_service = session.service("ALAnimatedSpeech")
         motion_service = session.service("ALMotion")
         tablet_service=session.service("ALTabletService")

         a = 1
         while a == 1:
				tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen3.jpg")
    
				speed=0.5
    	  		animated_speech_service.say("Hola Soy Pepper ")
    	  		time.sleep(2)
    
   			 	motion_service.setAngles(["LShoulderPitch","RShoulderPitch"], [0.0, 0.0], 0.5)
    	  		time.sleep(1)
          		motion_service.setAngles(["LShoulderPitch","RShoulderPitch"], [0.0, 0.0], 0.5)
          		time.sleep(2)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-1.0, 1.0], 0.5)
          		time.sleep(2)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-0.3, 0.3], 0.5)
          		time.sleep(1)

    	  		names = ["RShoulderPitch", "RShoulderRoll", "RElbowYaw", "RElbowRoll"]
    	  		angles = [math.radians(-40), math.radians(-10), math.radians(60), math.radians(80)]
    	  		motion_service.setAngles(names, angles, speed)
    	  		time.sleep(1.5)
        	
          		tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen2.jpg")
          		animated_speech_service.say("Les voy a hablar sobre algunas operaciones básicas que puedo realizar")
          		time.sleep(2)
 
          		motion_service.setAngles(["LShoulderPitch","RShoulderPitch"], [0.0, 0.0], 0.5)
          		time.sleep(1)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-1.0, 1.0], 0.5)
          		time.sleep(2)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-0.3, 0.3], 0.5)
          		time.sleep(1)

          		names = ["RShoulderPitch", "RShoulderRoll", "RElbowYaw", "RElbowRoll"]
          		angles = [math.radians(-40), math.radians(-10), math.radians(60), math.radians(80)]
          		motion_service.setAngles(names, angles, speed)
          		time.sleep(1.5)

          		motion_service.setAngles(["LShoulderPitch","RShoulderPitch"], [0.0, 0.0], 0.5)
          		time.sleep(1)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-1.0, 1.0], 0.5)
          		time.sleep(2)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-0.3, 0.3], 0.5)
          		time.sleep(1)

          		animated_speech_service.say("Imaginemos un día de Gym: Al primero, puedes levantar 10 kilogramos en Press de Banca")
          		time.sleep(2)
          		animated_speech_service.say("Al segundo,  puedes levantar 5  kilogramos más ")
          		time.sleep(2)
          		animated_speech_service.say("La pregunta sería ¿Cuánto he progresado en el Gym?")
          		time.sleep(2)
	      		num_1="15"
	      		num_2="kilogramos"
	      		mensaje= num_1+num_2
		
          		animated_speech_service.say("Felicidades has progresado en un total de:"+mensaje)
          		time.sleep(2)

          		tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen3.jpg")

        
	      		animated_speech_service.say("¡Que tal si vemos un video de la técnica correcta del Press de Banca!")
          		time.sleep(2)
        
	   			animated_speech_service.say("Vamos a verlo")
          		time.sleep(2)
        
          		tablet_service.enableWifi()
          		tablet_service.playVideo("http://198.18.0.1/apps/usta/Banca.mp4")
	      		time.sleep(164)
	
          		tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen5.png")
          		time.sleep(3)

          		animated_speech_service.say("Ahora vamos a hablar un poco sobre nutrición")
          		time.sleep(2)
	
          		tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen5.png")
          		time.sleep(3)

          		motion_service.setAngles(["LShoulderPitch","RShoulderPitch"], [0.0, 0.0], 0.5)
          		time.sleep(1)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-1.0, 1.0], 0.5)
          		time.sleep(2)
          		motion_service.setAngles(["LElbowRoll","RElbowRoll"], [-0.3, 0.3], 0.5)
          		time.sleep(1) 
	
          		animated_speech_service.say("La nutrición se le conoce como la ciencia y el proceso  mediante el cual los organismos obtienen y utilizan los nutrientes de los alimentos 				para crecer,mantenerse y obtener energía." )
          		time.sleep(2)
	
          		animated_speech_service.say("Eso fue todo por esta sesión informativa")
          		time.sleep(2)
          		animated_speech_service.say("Gracias, nos vemos en una próxima")
          		time.sleep(2)

          		tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen6.jpeg")
          		time.sleep(3)
	  
	      		tablet_service.showImage("http://198.18.0.1/apps/usta/Imagen3.jpg")
	      		time.sleep(2)
				
       	  		a = 0 

+ El resultado obtenido se puede visualizar en el siguiente link:</br>

  https://www.youtube.com/watch?v=fJzGaVWrneo&t=3s
   























