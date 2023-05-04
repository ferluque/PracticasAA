# Apuntes Práctica 2

## Ejercicio 1

### Ejercicio 1.1 a)

Por H entendemos el *Hypothesis Set*, es decir, el conjunto de fórmulas candidatas para resolver nuestro problema. Al aplicar un algoritmo de aprendizaje, somos capaces de quedarnos con una única hipótesis final $g$, que intenta aproximar a $f$, la función objetivo desconocida.

<img src="C:\Users\fl156\AppData\Roaming\Typora\typora-user-images\image-20220404174243458.png" alt="image-20220404174243458" style="zoom: 67%;" />

Clasificamos con una función conocida y el error es de 0%

### Ejercicio 1.1 b)

Metemos un 10% de ruido y vemos que ya el error de clasificación es del 10%

### Ejercicio 1.1 c)

Usamos otras fronteras de decisión para clasificar y determinar:

* ¿Funciones más complejas son mejores clasificadores?
* ¿Es posible superar/mejorar ese 10% de error de clasificación?
* Si clasificamos con estas funciones e introducimos un 10% de ruido, ¿conseguimos bajar el 10% de error?

Básicamente concluir que aunque tengamos un clasificador perfecto, siempre que haya ruido habrá malas clasificaciones.

## Ejercicio 2

### Ejercicio 2.1 Perceptrón

Algoritmo básico. Itera en toda la muestra, si acierta no cambia nada si falla aplica el update a w.

Cuando haya recorrido la muestra una vez y no haya cambiado nada sale del bucle y finaliza.

Como medida de error usamos el porcentaje de errores

<u>Apuntes a tener en cuenta</u>:

* Si un conjunto es linealmente separable: Converge siempre
* Si no lo es: Nunca converge.
* Necesita muchas iteraciones. Iteración = recorrer 1 elemento, Época = recorrer una vez el conjunto
* Es muy sensible a la inicialización (realizar análisis con distintos valores iniciales)

### Ejercicio 2.2: Regresión logística

<img src="C:\Users\fl156\AppData\Roaming\Typora\typora-user-images\image-20220404180920367.png" alt="image-20220404180920367" style="zoom:67%;" />

La regresión logística es un "punto medio" entre clasificación lineal y regresión lineal. Usa la sigmoide sobre la función de salida. Aunque usa  el término "regresión" es una técnica de clasificación.

<img src="C:\Users\fl156\AppData\Roaming\Typora\typora-user-images\image-20220404181207378.png" alt="image-20220404181207378" style="zoom:67%;" />

El clasificador establece que si el valor de la sigmoide sobre nuestra salida (pesos por entrada) es mayor o igual que 0.5 pertenece a una etiqueta y si es menor pertenece a otra.

<img src="C:\Users\fl156\AppData\Roaming\Typora\typora-user-images\image-20220404181541199.png" alt="image-20220404181541199" style="zoom:67%;" />

Ahora, el gradiente se ha modificado, ya que es el gradiente de la <u>entropía cruzada</u>.

Como criterio de parada tenemos el número máximo de iteraciones o cuando la diferencia entre los pesos al principio y final de una época, sea menor de 0.01

**El tamaño de learning rate y de tamaño de batch debe ser seleccionado.**

#### Aclaraciones

**¿Qué es un modelo lineal?** Cuando hablamos de modelos lineales hablamos de linealidad en los pesos: $w_0+w_1x_1+w_2x_2^2=y$ es un modelo lineal, los pesos son lineales. Se pueden usar modelos lineales para crear fronteras de decisión no lineales (como hicimos en la práctica 1)

**¿Cómo puede ser que regresión logítica sea un modelo lineal si usa una función de activación no lineal?** Porque podemos escribir las predicciones en términos de una función lineal. 

<img src="C:\Users\fl156\AppData\Roaming\Typora\typora-user-images\image-20220404183241646.png" alt="image-20220404183241646" style="zoom:67%;" />

**¿Por qué una red neuronal es un modelo no lineal si es una combinación de múltiples unidades logísticas?** Precisamente la combinación de unidades logísticas encadenadas hace que no sea lineal

<img src="C:\Users\fl156\AppData\Roaming\Typora\typora-user-images\image-20220404183650130.png" alt="image-20220404183650130" style="zoom:67%;" />

**Por tanto ¿cómo sabemos exactamente si un modelo, sistema o función es lineal?** Porque verifica las propiedades de homogeneidad y superposición: $f(ax_1+bx_2)=af(x_1)+bf(x_2)$

## Bonus

<u>Usar regresión lineal como inicialización para los otros métodos</u>: Podemos aplicar la pseudo-inversa para obtener un punto inicial y así iterar con otros métodos.

También hay que hablar de errores fuera de la muestra (que no de test) y acotarlos y estudiar las dos acotaciones.