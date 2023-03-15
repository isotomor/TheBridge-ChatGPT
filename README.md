![](img/TheBridge_logo.png)

# Masterclass ChatGPT

![](img/Chat_GPT.png)

En este repositorio se va a ver todo lo relacionado con la masterclass de ChatGPT orientada a cloud. 


## Preguntas sobre ChatGPT

- ¿Conoces ChatGPT?
- ¿Tienes una cuenta de ChatGPT?
- ¿Has usado ChatGPT en tu trabajo?
- ¿Has preguntado a ChatGPT dudas fuera de tu trabajo?

## ¿Qué es ChatGPT?

Es un modelo de lenguaje natural de gran escala desarrollado por OpenAI que utiliza técnica sde procesamiento de 
lenguaje natural (NLP) y aprendizaje automático (ML)

En términos simples ChatGPT es un programa que puede "conversar" con los usuarios a través de texto, de manera similar a 
como lo haría un humano. 

En resumen, ChatGPT es una herramienta de procesamiento de lenguaje natural impulsada por inteligencia artificial que 
permite a los usuarios "conversar" con un modelo de lenguaje de gran escala utilizando texto. El modelo utiliza técnicas 
de aprendizaje automático para mejorar continuamente su capacidad para entender y generar respuestas coherentes y 
relevantes en una variedad de temas y contextos.

### Historia de versiones

- GPT (2018)
- GPT-2 (2019)
- GPT-3 (2020) -> llegada de chatGPT
- GPT-3.5 (2022) 

GPT-4  (Incluye la capacidad de responder como si fuera un humano. Sus respuestas e interacciones serán más precisas y 
coherentes, por lo que sumará puntos a la hora de enfrentarse al test de Turing.

## ¿Cómo funciona ChatGPT?

### Algoritmo

ChatGPT está basado en GPT3. GPT3 o Generative pre-trained transformer 3 es un Modelo

Un modelo es un programa, algoritmo, función que intenta replicar el comportamiento de un sistema. 

Un modelo podría ser predecir cuantas altás se van a producir en una página WEB. Coges datos de entrada y el modelo genera una predicción:

![](img/ejemplo_modelo.png)

En el siguiente enlace puedes hacer pruebas con modelos de imagen, sonido video.. Pincha [aquí](https://teachablemachine.withgoogle.com/train/)

GPT como hemos visto anteriormente es un modelo de lenguaje. En concreto es un modelo generativo, dado un texto, genera palabras.
A diferencia de los modelos que hemos visto de imagen o sonido. 
El modelo te dice cual es la palabra más probable que habrá a continuación en un texto.

La version de ChatGPT 3.5 está especialmente configurada para completar respuestas como si estuviéramos en un chat.
Todas las respuestas que te devuelve están generadas y son únicas, no está copiado de páginas web. 

Para poder hacer esto, GPT está basado en redes renuronales. Una red neuronal está diseñado para aprender a hacer tareas.

![](img/Ejemplo_red_neuronal.png)

Hay cosas que una máquina no sabe que es hasta que se lo dices, para solucionar esto se creó el aprendizaje automático 
(machine learning), y las redes neuronales son un tipo de aprendizeje automático.

En el caso del lenguaje natural hay varios problemas a la hora de que un ordenador nos pueda entender. Por ejemplo si escribes 
"móvil", tu te imaginas un móvil pero el ordenador solo sabe de números o 0 y 1 en concreto. Todo lo que recibe un ordenador 
lo transforma en 0 y 1, imagenes, videos, audio, texto.. 

Para poder entrenar una red neuronal, para que nos entienda, hay que tener esto en cuenta, que solo va a ver números. 

Vamos a ver como funcinaría esta red neuronal teniendo en cuenta estas premisas. 

Siguiendo la imagen de un poco más arriba, vemos que una red neuronal recibe datos de entrada, estos serán las frases 
que se han usado de entrenamiento transformadas en números. 

![](img/Algoritmo_chatGPT_01.png)

Si analiza muchas secuencias de estos números la red neuronal puede encontrar patrones

![](img/Algoritmo_chatGPT_02.png)

Hay que recordar que el ordenador no lo interpreta como texto, sino como número y para poder entenderlo mejor, el modelo lo transforma en tokens.

![](img/Algoritmo_chatGPT_03.png)

El siguiente paso es utilizar marcadores para identiciar patrones. 

En el ejemplo anterior vemos que el la palabra "Vamos" está relacionada con "a". 

O por ejemplon que ChatGPT está relacioanada en muchos textos con Redes neuronales o NLP. De esta forma se puede encontrar
relacionles entre tokens. 

El resultado quedaría algo así:

![](img/Algoritmo_chatGPT_04.png)

Con gran cantidad de textos se podría crear una gran clasificación de términos y distintos patrones que irá encontrando. 

ChatGPT puede tener más de 300 marcadores por cada token con cercanía entre palabras. 

Otra forma de representarlo sería con una red neuronal, donde cada token se uniría con otro según la distancia a la que esté:

![](img/Algoritmo_chatGPT_05.png)

A este proceso de agrupar palabras similares se le llama embedding. También podríamos verlo con la siguiente representación:

![](img/Algoritmo_chatGPT_06.png)

Esto ya es útil por si solo porque tenemos un sitio donde buscar palabras similares que es algo parecido a lo que usa el buscador de google. 

La diferencia con GPT3 es que GPT3 no solo recuerda tokens a nivel de palabra sino también a nivel de frases. Crando así mas de 1000 marcadores por cada frase, 
y relacionar así frases entre sí. 
 
![](img/Algoritmo_chatGPT_07.png)

El proceso sabe que dentro de una frase sería complejo almacenar todo, por lo que almacena las frases tras realizar una limpieza. 
Por ejemplo en la frase anterior "una", "de", "en" aportan poco, podríamos decir "Estamos haciendo masterclass ChatGPT TheBridge". 
O Recucirlo más usando lematización, que es reducir la palabra al lema correspondiente:

![](img/Algoritmo_chatGPT_08.png)

>Todas las frases que nos devuelve ChatGPT lo devuelve de su sistema de embedding.

Cuando ChatGPT genera texto hace consultas a su embedding y lo que saca son estas secuencias de tokens que son frases comprimidas. 
Y posteriormente tiene que convertirlas a algo que entienda el lector buscando el token en en los embeddings, por eso no siempre te devuelve lo mismo
porque busca en los embedding y puede tener varios tonkens similares. 

Reduce y comprime al sistema básico y cuando lo tiene que devolver reconstruye con sus propias palabras.

Además de esto, utiliza una técnica que se llama **sampling** que es algo parecido a generar un número aleatorio para moverse dentro del embedding. 
Eso le hace moverse entre distintas frases. **Dando a parecer que se está inventando frases pero realmente son grases que ha aprendido en otro momento.**

### Transformers

Uno de los problemas en este tipo de redes que resuelve chatGPT es recordar la conversación anterior. Porque en lo que hemos visto anteriormente 
no estamos contando con que chatgpt si le has hecho varias preguntas recuerda las anteriores y te puede contestar en función de dos preguntas. 

Una técnica para solucionar esto es con LSTM (Long Short-term memory). Puedes consultar que son estas redes [aquí](https://blog.gft.com/es/2018/11/06/como-usar-redes-neuronales-lstm-en-la-prediccion-de-averias-en-las-maquinas/#:~:text=Las%20LSTM%20son%20un%20tipo,decidir%20cu%C3%A1l%20ser%C3%A1%20el%20siguiente.)

El problema es que dentro de una conversación muy larga este sistema no funciona y además tampoco se puede paralelizar. 

La solución a esto fue con una solución que plantearon unos empleados de google que llamaron "Transformers". En los 
transformers se añade una nueva capa. Que los investigadores llamaron "atención" que hace referencia a como los humanos vemos.

![](img/Transformers.png)

Puedes consultar el paper que publicaron [aquí](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://proceedings.neurips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf)

El cambio es que por cada frase se mira las palabras que hay cerca prestando atención a las más importantes, lo que permite saber el contexto y con ello, 
si tienes la palabra banco saber si hablas de banco de peces, de banco de sentarse o de dinero. 

Puedes entender un poco más viendo el siguiente video: [enlace](https://www.youtube.com/watch?v=aL-EmKuB078)

### Entrenamientos ChatGPT:

- Cuando entrenaron a GPT2 usaron 1.5 miles de millones de parametros. 
- Cuando entrenaron ChatGPT (GPT-3) usaron 175 miles de millones de parámetros. 


## Microsoft y ChatGPT

Microsoft tiene mucha relación con chatGPT porque para entrenar ChatGPT se ha usado el CPD de Microsoft Azure. 
Además recientemente han llegado a un acuerdo para incluir una vesión de ChatGPT en el buscador de Microsoft Bing. 
Microsoft tiene el 49% de ChatGPT. 

## Versión ChatGPT de Google 

La solución que creó google y presentó a comienzos del 2023 fue Bard. Pero tuvieron un fallo en directo y se produjo una caída del 8% en bolsa de Google. 

En el Google I/O de mayo quieren resarcirse y presentar una nueva versión. 

## Ejemplos de ChatGPT

- [Montar una Masterclass de ChatGPT](https://sharegpt.com/c/AUwCInc)
- [Ejercicio en Ansible](https://shareg.pt/LwEWxqb)
- [Montar un viaje con chatGPT](https://shareg.pt/RVH3Hhz)
- [Solicitud de un texto legal.](https://shareg.pt/QZdpzJq)


