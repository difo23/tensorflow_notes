# Revisión TensorFlow 1.0 a 2.0



## Vídeos relacionales

- [Dot CSV -  Aprende a programar una RED NEURNAL - Tensorflow - Keras - Sklearn](https://www.youtube.com/watch?v=qTNUbPkR2ao)

  

  - Versatilidad nivel bajo -> Nivel 0 : Python puro y duro.
  - Nivel 1: Librerías de Python Diferenciación automática - Tensorflow y Pytorch
  - Nivel 2: Keras - Composición de capas - Módulos de Tensorflow
  - Facilidad Nivel alto-> Nivel 3: Sklearn - Modelos 

## Fuentes a consultar

- https://github.com/difo23/awesome-tensorflow#github-tutorials
- https://developers.google.com/machine-learning/crash-course/ml-intro
- https://www.tensorflow.org/
- https://github.com/difo23/tensorflow_notes

## Instalación versión 1.x

## Especificando la versión de TensorFlow

Ejecutando "importar tensorflow" importará la versión por defecto (actualmente 2.x). Puedes usar la 1.x ejecutando una celda con la "versión mágica de tensorflow" **antes de ejecutar "importar tensorflow".

### Si no funciona hacer el pip install

```bash
!pip install tensoflow==1.13.1
%tensorflow_version 1.x
```

## Importando tensorflow

```python
import tensorflow as tf
```

## Constantes y variables

### Definir constantes

Estos son la diferencia principal entren Tensorflow 1.0 y 2.0.

```python
# Definir una constante en TensorFlow: 2 filas y 2 columnas
tensor = tf.constant([[23, 4], [32, 51]])
```

Un `tensor` con dos dimensiones `<tf.Tensor 'Const:0' shape=(2, 2) dtype=int32>` No presenta el valor del tensor. Para entrar al valor necesitamos  el método `.eval()`. 

```python
# Si la session no ha sido inicializada, no se pueden acceder a los valores de la constante
tensor.eval()
```

```bash
ValueError: Cannot evaluate tensor using `eval()`: No default session is registered. Use `with sess.as_default()` or pass an explicit session to `eval(session=sess)`
```

Las variables y constantes en Tensorflow se deben inicial `session` como un tensor. 

### Consultar los valores de la constante

```python
session = tf.Session()
session.run(tf.global_variables_initializer())
tensor_value = session.run(tensor)
tensor_value
```

Salida con los valores del tensor constante.

```bash
array([[23,  4],
       [32, 51]], dtype=int32)
```

### Definir variables

```python
# Definir una variable de TensorFlow 
variable = tf.Variable([[30, 20], [10, 45]])

variable
```

Salida obtenida de una variable sin inicial `session`  :

```bash
<tf.Variable 'Variable:0' shape=(2, 2) dtype=int32_ref>
```

Sucede lo mismo que con las constantes, necesitas agregarla a una `session` (Ojo que esto me parece canson!)

```python
# Si la session no ha sido inicializada, no se podrán acceder a los valores de la variable
variable.eval()
```

El error mostrado es el siguiente.

```bash
ValueError: Cannot evaluate tensor using `eval()`: No default session is registered. Use `with sess.as_default()` or pass an explicit session to `eval(session=sess)`
```

### Consultar los valores de una variable

```python
# Inicializar una session
session = tf.Session()

# Inicializar TODAS las variables de la session
session.run(tf.global_variables_initializer())

# Ejecutar el método eval en el entorno con la sesión iniciada para recuperar los valores del mismo
variable.eval(session)
```

Salida de una variable en `session`

```bash
array([[30, 20],
       [10, 45]], dtype=int32)
```

Nota: Tensorflow 2.0 esto se simplifica gracias a DIOS!! :happy:

