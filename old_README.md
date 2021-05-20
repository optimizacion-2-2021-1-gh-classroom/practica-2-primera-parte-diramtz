**Parte 1 de la práctica 2 del curso de Optimización 2 2021-1: uso de minikube, kubeflow y kale para construcción de un pipeline de procesamiento de forma automática y experimentación del paquete construído por cada equipo en la práctica 1 para resolver problemas de optimización convexa.**

Antes de iniciar a trabajar: 


* **Sólo una persona de cada equipo debe darle click a la liga** que está indicada en la publicación del *google classroom*. Una vez que le dé click a la liga tal persona **invite** a sus integrantes de su equipo como **Admin**. Para invitar a su integrante ir dentro del repo a Settings -> Manage Access y enviar la invitación ingresando user de github de su integrante.

* **Su primer *commit* debe ser para renombrar este archivo `README.md` por `old_README.md` para que guarden su contenido y crear otro `README.md` donde me escriban la división de su equipo en una tabla que contenga en una columna *user* de github y en otra columna la tarea a realizar por tal persona (más detalles sobre las tareas en dinámica)**.    
   

# Dinámica

Dividir a su equipo para realizar cuatro tareas. **Ustedes deciden qué integrante resuelve qué tarea (algunas personas tendrán que hacer más de una tarea)**:

1. 1 persona que levante los servicios de minikube, kale y kubeflow. Que realice lanzamientos con diferentes valores de parámetros de su paquete para resolver el problema de optimización convexa que hayan decidido en la práctica 1 (experimentación). Si encuentra errores entonces debe reportarle a las personas que se reimplemente su paquete.

2. 2 personas que apoyen a la reimplementación del paquete por los posibles errores encontrados durante la experimentación. Al terminar de realizar la reimplementación apoyan en la tarea 3.

3. 1 persona que utilice [kale](https://github.com/kubeflow-kale/kale) para la construcción de pipelines de procesamiento de forma automática del paquete construído en la práctica 1.

4. 1 persona que sea *project manager* (más detalles de este rol en las notas). Que realice lanzamientos con diferentes valores de parámetros de su paquete para resolver el problema de optimización convexa que hayan decidido en la práctica 1 (experimentación). Si encuentra errores entonces debe reportarle a las personas que se reimplemente su paquete.

Entre todos los y las integrantes tienen que dar *feedback* si es necesario en la resolución de las tareas que haya duda entre ustedes. El *feedback* consiste en resolver/explicar las dudas que existan. **Las personas asignadas a la tarea correspondiente son las que realizan los *commits* una vez resueltas las dudas**.

Los puntos 1, 2, 3 y 4 anteriores los realizan de forma iterativa hasta finalizar las tareas y que estén en acuerdo las y los integrantes de cada equipo con las soluciones.

**Deben usar `git` para llevar la historia de cambios en la realización de sus notebooks o cualquier otro archivo y subirlos a sus repos. No se revisarán aquellos archivos que tengan un commit con todas las respuestas. El trabajo es incremental.**

**Deben usar la funcionalidad de github**: *issues*, *milestones*, *projects*, *reviewers*, *asignees* o lo que ustedes consideren de github que les ayudará a comunicarse/organizarse (no tienen que usar todas las funcionalidades anteriores y cada equipo decide qué usar). Ver por [ejemplo video para crear proyectos en github](https://youtu.be/z4Xpif7HI04).

# Lenguajes de programación

Ustedes eligen el lenguaje de programación a usar.

# Calificación

La calificación de esta primera parte es la mitad de la práctica 2. Se asgina una calificación individual por tarea asignada y una calificación por equipo. Se calificará de acuerdo a los *commits* realizados y a los avances que realizan en su trabajo incremental. 

# AWS

Agendar reunión con el prof para que muestren el lanzamiento de los pipelines de procesamiento con kale vía kubeflow y minikube.

Adjunten *screenshots* en un directorio de su repo para mostrar su uso de AWS, debe aparecer en el *screenshot* su nombre, clave única u otra forma de identificar su trabajo. En los *screenshots* incluyan la lista de experimentos ejecutados en *kubeflow* y algunos de los resultados, del *pipeline*.

Pueden usar las cuentas de *Educate* si no usan GPUs, si quieren usar GPUs envíenme un mensaje por gitter para usar la cuenta no de *Educate*. También pueden usar las cuentas de *AWS* en las que tengan configurados los servicios necesarios para el despliegue de kale, kubeflow y minikube. **Recuerden que la imagen a utilizar es: `opt2-aws-educate-17-03-2021` y la localizan en la región de Virginia**.

# Referencias

Ver [video](https://www.youtube.com/watch?v=xL91E3FBgAg) en donde se muestra el *set up* de kale, kubeflow y minikube en AWS y además se muestra el lanzamiento de algunos *pipelines*. En este video se sigue la guía en [6.Minikube-y-AWS](https://github.com/ITAM-DS/analisis-numerico-computo-cientifico/wiki/6.Minikube-y-AWS)

Utilicen los [reference notebooks](reference_notebooks) para revisar la identificación de las celdas de los *notebooks* de *jupyter* y el panel de kale (ver video anterior para entender mejor este enunciado).

Ver [palmoreck/dockerfiles/jupyterlab/kale](https://github.com/palmoreck/dockerfiles/tree/master/jupyterlab/kale) para ejemplos de Dockerfiles que utilizan kale (ver video anterior para entender mejor este enunciado).

Ver [analisis-numerico-computo-cientifico/deployments/minikube/hostpath_pv](https://github.com/ITAM-DS/analisis-numerico-computo-cientifico/tree/master/deployments/minikube/hostpath_pv) para los *deployments* que utilizarán para el despliegue del servicio de *jupyterlab* y de su *pipeline* de procesamiento (ver video anterior para entender mejor este enunciado).

Todas las personas del equipo conocen cómo levantar, configurar instancias de AWS y desplegar servicios allí. Uds elijan a una persona que sea la encargada de realizar lo anterior.

# ¿Qué hay que entregar/mostrar?

En la práctica 1 se realizaron las configuraciones necesarias para la construcción automática de *tests*, documentación de su paquete e imagen de *docker* con *github actions*. Hay que reutilizar lo realizado en esa práctica 1 (mejorar si es necesario) para construir una imagen de docker que tenga a Kale instalado. Esta imagen de docker llámenla diferente que la que hicieron en la práctica 1.

Actualicen la documentación de su paquete indicando que existen imágenes de *docker* que ayudan a utilizar su paquete (sin y con Kale). Los *tests* que realizaron en la práctica 1 les ayudarán a revisar que están resolviendo correctamente los ejemplos en los *pipelines* de procesamiento.

El objetivo es realizar experimentos con las herramientas de kale, kubeflow, minikube para detectar con qué valores no funcionan sus programas. Cambien puntos iniciales, cambien criterios de paro, elijan diferentes ejemplos que los que utilizaron en los *tests* por ejemplo y reimplementen sus métodos que están en su paquete para mejorarlo y robustecerlo. Estos cambios de implementación deben de reflejarse automáticamente con *github actions* en la documentación del paquete, *tests* y en sus imágenes de *docker*.

Coloquen su botón de *binder* en su `README.md`.

Designen un horario en el mes de abril para que nos reunamos uds y yo y me muestren el lanzamiento de los *pipelines* de procesamiento corriendo en AWS. Esto lo agendamos vía *gitter* :)

# Notas

* **De su práctica 1 deben utilizar los tres archivos que crearon para uso de *github actions*: el que automáticamente actualiza la documentación de su paquete, el que automáticamente construye la imagen de *docker* y la sube a su cuenta de *dockerhub*, el que automáticamente realiza *testing* para cambios en su paquete.**

* **Para la entrega crear un archivo con nombre:** `reporte_equipo_<aquí colocar_número>_parte_1_practica_2.ipynb` que contiene ejecución del paquete para los ejemplos elegidos y es el que me mostrarán en la reunión. Este *notebook* debe tener la identificación de las celdas con el panel de kale para que si clono su repo y despliego su *notebook* con mi infraestructura de minikube y kubeflow entonces el despliegue del *pipeline* termina exitosamente sin hacer modificaciones al *notebook*. En la reunión uds levantan la infraestructura de *minikube* con *kubeflow* y lanzan su *pipeline* con kale.

* Es muy importante la **experimentación** para resolver problemas en la ciencia. En esta práctica este es uno de los **objetivos** para robustecer sus implementaciones con ambientes controlados :)

* *Project manager*: es la persona más importante para el éxito del proyecto. Conoce el/los objetivo(s) a resolver, detalla las tareas que realizarán el grupo de programación y el grupo de revisión (creación de *tests* en nuestro caso), organiza y asigna a personas a ambos grupos, crea tarjetas en el [project board de github](https://help.github.com/en/github/managing-your-work-on-github/creating-a-project-board) y [milestones](https://help.github.com/en/github/managing-your-work-on-github/tracking-the-progress-of-your-work-with-milestones) para dar seguimiento a [issues](https://help.github.com/en/github/managing-your-work-on-github/creating-an-issue). Mantiene un contacto directo con el prof para dudas que tengan y para avisar en qué fase se encuentran. Les explica a su equipo de trabajo la correcta creación de *issues*, solución de los mismos y el uso de *milestones* y del *project board*.

* La división de las tareas y roles está está inspirada en el *framework* [scrum](https://www.youtube.com/watch?v=b02ZkndLk1Y&feature=emb_logo) en un ambiente laboral real (y en esta práctica estamos super-simplificando tal *framework*).

* Añadan referencias utilizadas para su trabajo en su `README.md`.

* **Los commits deben tener un mensaje explicatorio, no hacer lo siguiente:**

```
git commit -m "create 1" -i archivo1.txt

git commit -m "update 1" -i archivo1.txt #qué es update 1?

git commit -m "update 2" -i archivo1.txt #qué es update 2?

git commit -m "update 3" -i archivo1.txt #qué es update 3?
```

**así también para los *issues*, *projects*, *milestones*...**

* Esta organización es nuestro *playground* utilicen los repos de aquí para practicar :)

* Recuerden:

    * usar `git` para llevar la historia de sus cambios en sus repos :)
    * poner las referencias que utilizan (aún si le preguntan a una compañera o compañero de la clase coloquen esto en su entrega) pues no está permitido copiar y escribir que lo hicieron sin citar sus fuentes.


* Para dudas creen un *room* de gitter e ínvitenme :) (si ya lo hicieron omitan este enunciado)

* **Su trabajo individual y su tiempo es muy valioso e importante, también el trabajo en equipo. Si alguna persona del equipo no realizó su tarea asignada, esperaría que lo resolvieran entre ustedes, si no lo resuelven avísenme y no realicen su tarea asignada. Si tienen algún problema (familiar, salud,...) infórmenme con tiempo para ver qué podemos hacer :)**


