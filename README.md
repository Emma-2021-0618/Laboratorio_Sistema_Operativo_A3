# UCATECI
- Sistemas operativo 2
- Lizandro Jose Ramirez
- Encuentro 7 Teoria

# Autores
- Enmanuel Sanchez Rodriguez 2021-0618
- Albert Francisco Hernandez Sanchez 2019-0126
  

# Barreras con Python.


Los "locks", también llamados "mutex" son objetos con dos estados posibles: adquirido o libre. Cuando un "thread" adquiere la barrera, los demás "threads" que pidan adquirirlo se bloquearán hasta que el "thread" que lo ha adquirido libere la barrera, momento en el cual podrá entrar otro "thread". Un "mutex" se usa en programación concurrente para que un solo procesos o hilo en nuestro caso pueda tomar un recurso compartido por otros.

Este es un ejemplo de código en Python que utiliza el módulo "threading" para crear múltiples hilos y controlar el acceso a una variable compartida llamada "d" utilizando un objeto Lock.

<br>

Empezamos con la Importación de módulos y creación del objeto mutex

~~~~~~~~~~~~~~~~~~
import threading
from time import sleep

mutex = threading.Lock()
~~~~~~~~~~~~~~~~~~ 

<br>

Aquí, se define la clase "Hilo" que hereda de la clase "Thread" de threading. La clase tiene un constructor que toma un argumento "id", que se utiliza para identificar el hilo.

<br>

La clase también tiene un método "run" que se ejecutará cuando se inicie el hilo. En este método, el hilo adquiere el mutex utilizando la función "acquire" del objeto "mutex" y luego espera un tiempo determinado por la fórmula "3 - self.id" utilizando la función "sleep".

<br>

Luego, el hilo imprime un mensaje que incluye el valor de la variable compartida "d" utilizando la función "print". El mensaje incluye el identificador del hilo y el valor actual de la variable "d". Finalmente, el hilo libera el mutex utilizando la función "release" del objeto "mutex".

~~~~~~~~~~~~~~~~~~
class Hilo(threading.Thread):
 
    def __init__(self, id):
        threading.Thread.__init__(self)
        self.id = id

    def run(self):
        mutex.acquire()
        sleep(3-self.id)
        print("Yo soy %s, la variable d tiene el valor %s" % (self.id, d))
        mutex.release()
~~~~~~~~~~~~~~~~~~ 

<br>

Aqui definimos la variable "d" y creamos objetos que en su lista tendran un valor que será un número identificador del mismo.
~~~~~~~~~~~~~~~~~~
d = 1
hilos = [Hilo(1), Hilo(2), Hilo(3)]
~~~~~~~~~~~~~~~~~~ 

<br>

Y para finalizar tenemos este siglo "For" que recorre la lista de hilos y se inicia cada hilo utilizando la función "start" de threading.Thread. Cuando se inicia un hilo, se ejecutará el método "run" del hilo, que adquirirá el mutex, esperará un tiempo determinado y luego imprimirá un mensaje que incluye el valor actual de la variable compartida "d". 
~~~~~~~~~~~~~~~~~~
for h in hilos:
    h.start()
~~~~~~~~~~~~~~~~~~ 

Pequeño video explicando:
