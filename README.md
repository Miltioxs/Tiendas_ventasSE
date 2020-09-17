#Sistema de ventas en linea solucion de codigo por Milton Mejia
IDE  utilizado JupyterNotebook

archivo utilizado costos.txt, este archivo se encuentran cada uno de los items que necesitan ser evaluados para determinar una inversion de una tienda de ventas en linea.

Regla de negocio: Una empresa de ventas en linea necesita un programador que desarrolle un codigo para poder realizar una inversion, esta tienda cuenta con la cantidad de un millon de usuarios, estos tienen una seleccion en sus listas de deseos, la cual, cada una de estas selecciones se encuentran en el archivo antes mencionado "costos.txt".
Esta tienda como estrategia de fidelizacion de clientes, para la festividad de la natividad del 2020 la compañia regalara dichos items que se encuentren dentro de las lista de deseos seleccionados por cada usuario, si este tiene un costo menor a $25.

El programador debera desarrollar 2 propuestas para darle solucion a la regla de negocios antes planteada, este debera corroborar la eficiencia de este codigo en base al tiempo de ejecucion. 

##Primeros Pasos
1. se importar las librerias que utilizaremos, en este caso son las siguientes: 

import time
import numpy as np

2. Se le manda a invocar los datos que se encuentran almacenados en la lista de deseos "costos.txt"

with open('costos.txt') as costos: #Aqui se abre  el documento .txt y se le asigna un alias.
    lista_deseos = list(map(int, costos.read().split('\n'))) # a la variable lista_deseos se #almacena la lectura de los datos que estan en "costos.txt"
    #map(int, costos.read()) esta transformando cada uno de los datos que estan en esa lista en #numeros enteros, por que a la hora de operarlos, me los tomaba como str, entonces asi los #transformo y luego los transformo en forma de una lista con list(map(int, costos.read()))

##Propuesta 1 

inicio =time.time() #se calcula el tiempo de inicio desde que se ejecuta el codigo.

inversion_tienda = [] #en inversion_tienda se alacenara el precio del item que se encuentra en la #lista_deseos, que no exceda los $25.

for item in lista_deseos: # aqui se recorre cada uno de uno de los elementos de la lista_deseos y #se almacenan en la variable items.

    if item <= 25: #Este condicional evalua cada uno de los item si es menor o igual a 25

        inversion_tienda.append(item) #si la condicion anterior se cumple, item se almacera en la #lista almacenada en la variable inversion_tienda

print ('El total de la inversion es: ', '$',sum(inversion_tienda)) #se imprime y se hace el #calculo de la suma de la inversion total de la tienda de ventas en linea.

print ('Duracion: {} segundos'.format(time.time() - inicio)) #Aqui se calcula el tiempo final, #invocando el modulo time y restandole  el inicio para calcular el tiempo que duro la ejecucion de #este codigo. 


##Propuesta2
inicio =time.time() #igual que la propuesta 1 se calcula el tiempo inicial de la ejecucion. 

lista_deseos_array = np.array(lista_deseos) #aqui se convierte la lista_deseos en un array, para #poder realizar operaciones de comparacion, exactamente por que me deja utilizar (<=) este tipo de #operadores.

inversion_tienda = lista_deseos_array[lista_deseos_array <= 25] #Aqui se realizaran la #comparacion de los item de la lista_deseos [lista_deseos_array <= 25] esta parte me devuelve un #array con un contenido boleano, es decir, si se cumple la condicion que necesito me devuelve un #True o False y lo almacena en la variable inversion_tienda, lista_deseos_array[lista_deseos_array #<= 25] ya todo este segmento me devuelve los valores numericos que son True, y los almacena en #invesion_tienda.

inversion_tienda = np.sum(inversion_tienda) #Aqui se sobreescribira inversion_tienda por que #realizamos la sumatoria de esos valores que se encuentran alamacenados en la lista inversion_#tienda, utilizando una funcion de numpy np.sum, para sumarlos.

print ('El total de la inversion es: ', '$',inversion_tienda) #Aqui imprimimos de una vez el valor #de inversion_tienda
print ('Duracion: {} segundos'.format(time.time() - inicio)) #Aqui se calcula el tiempo final, #invocando el modulo time y restandole  el inicio para calcular el tiempo que duro la ejecucion de #este codigo. 

##Conclusion
por pruebas de ambos codigos el que tiene menos tiempo de ejecucion es la Propuesta numero 2, ronda aproximadamente entre 0.5----- y 0.6 ------ Segundos, mientras que la Propuesta numero 1, ronda aproxidamente entre 0.7---- y 0.9 ------  Segundos, entonces, ya que como estamos tomando el tiempo de duracion como calificador para demostrar la eficiencia de ambos codigos, como la Propuesta 2 tiene menor tiempo de ejecucion que la Propuesta numero 1, se puede determinar que la Propuesta 2 es la solucion mas eficiente.