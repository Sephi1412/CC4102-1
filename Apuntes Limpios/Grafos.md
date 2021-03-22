
# **Grafos**

<br>

## **¿Que es un grafo?**
---
> Estructura matemática que permite representar relaciones entre distintos tipos de elementos

## **Caracteristicas básicas**
---
> - Se conforma por un conjunto de vértices $V$ y un conjunto de arcos/aristas $E$, donde el número de vértices se suele representar por convención con una $n$, mientras que la cantiidad de arcos como una $m$
> - Los arcos pueden tener sentido o no. Dependiendo de ello se categorizan como *dirigidos* o *no dirigidos* respectivamente.

## **Representaciones de grafos en memoria**
---
> - **Matriz de adyacencia**: Se puede representar un grafo como una matriz $A$ donde $A[i,j] = 1$ si hay un arco que conecta los vértices $v_{i}$ y $v_{j}$
> - **Listas de adyacencia**: Es similar a la matriz previa. Lo que hace es agrupar a los vecinos de un vertice $v_{i}$ en formato lista. Por ejemplo
> $$
> vecinos[v_{1}] = [v_{2}] \\
> vecinos[v_{2}] = [v_{2}, v_{3}] \\
> vecinos[v_{3}] = [v_{1}, v_{4}] \\
> $$
> > Esto consume, $\Theta(m)$ de la memoriam siendo $m$ la cantidad de arcos.


## **Caminos y Ciclos:**
----
> - Camino: Es literalmente lo que te imaginas. Si usamos una definición formal, un camino es una secuencia de arcos en que el extremo final de un segmento coincide con el extremo inicial del otro segmento.
>   - Camino Simple: No se repiten vértices, **excepto el primero y el último**
> - Ciclo: Es un camino simple pero que está cerrado, es decir, que el *vértice inicial y final del camino es el mismo.*


## **Características de grafos:**
---
> - Aciclico: Se dice que un grafo es acíclico si no tiene que siglos ~~(Vaya, quien lo diría)~~
> - Conexo: Si **todos** los vértices del grafo tienen un camino que los una. Dicho de otro modo, *si todos están transitivamente unidos*. Dicho esto, si un grafo no es conexo, significa que este será como un archipielago, en donde las islas son los vértices y cada conjunto de islas es llamado **componente conexa**.
> - Arbol: Son gráfos **acíclicos** y **conexos**
>   - Todo harbol de $n$ nodos tiene $n-1$ aristas
>   - Si se agrega un arco extra a un árbol, se crea un único ciclo. Infiero que esto se refiere a que si no se agrega un nuevo nodo, pero si un arco y considerando que previamente sabemos que los árboles son conexos, entonces se genera un ciclo.

## **Recorrido de grafos:**
---
> - Búsqueda en profundidad ó Depth-First Search(DFS): Se aleja lo más posible del nodo inicial sin repetir ningún nodo, y luego se devuelve al inicio e intenta tomar otra ruta
> - Búsqueda en amplitud ó Breadth-first search(BFS): Se visita a todos los nodos vecinos y luego a los vecinos de los vecinos 
> 
![alt text](https://github.com/Sephi1412/CC4102-1/blob/main/Img/bfs-dfs.gif)


## **Arbol cobertor mínimo (Minimu Spanning Tree):**
---

> Dentro de los grafos, existe el concepto de "peso" el cual hace alusión al coste que tiene moverse a través de un arco. Esto permite darle aplicaciones más prácticas a los grafos.
> Dicho esto, en ocasiones nos gustaría encontrar la ruta óptima para recorrer un camino específico de un grafo con el menor coste posible. Para ello, existe el concepto de *Árbol cobertor mínimo*, el cual puede ser adquirido mediante distintos tipos de algoritmos.



## **Algoritmo de Kruskal:**
---
> - El **objetivo principal** de este algoritmo es encontrar la ruta menos costosa para conectar el grafo entero
> - Inicialmente, solo tenemos los vértices, ninguna arista. Nos ubicamos en un vertice $x$ del grafo, que tenga acceso a la arista de menor coste posible y la agregamos. Seguimos agregando todas las aristas de una en una, dándole prioridad a aquellas que tienen menos peso. En caso de que se genere un ciclo por agregar una arista, esta se descarga y pasamos a la siguiente arista que tenga el menor peso posible.
>
>![alt text](https://github.com/Sephi1412/CC4102-1/blob/main/Img/kruskal.gif)
> - En sintesis, este algoritmo depende de dos funciones:
>   - La función que une vértices
>   - La función que determina cual es la arista de menor peso que se encuentra disponsible en un momento determinado de la ejecución y que al ser utilizada, no genera un ciclo en el grafo.

## **Algoritmo de Prim:**

> Funciona relativamente similar a *Kruskal*.
> Lo primero que hace es buscar el arco de menor peso posible y se utiliza para unir dos vertices del grafo. Luego, por cada iteración, intenta extender el conjunto de nodos alcanzable siempre agregando los vecinos de los nodos unidos en las iteraciones previas del algoritmo que cumplan:
>   - Tomar esa ruta no genera un cíclo
>   - La ruta que se tome debe ser la que tenga el menor peso posible
> En caso que ninguna de las condiciones deseadas se cumpla, nos devolvemos al último vértice que tenga una arista que cumpla las condiciones previamente mencionadas.
> 
> >![alt text](https://github.com/Sephi1412/CC4102-1/blob/main/Img/prim.gif)
>
> De modo que los pilares principales de la aplicación son:
>   - Tener consciencia de cuales son los vecinos del nodo actual
>   - El peso de las aristas que son accesibles desde el nodo actual
> 
> Por lo que debemos tener funciones que:
>   - Unan vertices
>   - Que permitan detectar cual es la ruta de menor costo y que sea accesible desde el vértice actual.

## **Distancias mínimas en un grafo dirigido:**
---
>
