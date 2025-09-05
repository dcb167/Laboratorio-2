# Laboratorio-2
## 1. Coreografía con Pepper desde Choregraphe

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























