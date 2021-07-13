# Introducción a Tensoflow 2.0

Todos estos ejemplos los realizamos en  `Google Colab`.

## Instalación

```python
#!pip install tensorflow-gpu==2.0.0-alpha0
%tensorflow_version 2.x

# Consultar version
tf.__version__
```

```python
import tensorflow as tf
import numpy as np
```

## Constantes

### Definir una constante

```python
# Definir una constante en TensorFlow 2.0
tensor_20 = tf.constant([[23, 4], [32, 51]])
```

```python
tensor_20
```

Salida

```bash
<tf.Tensor: id=0, shape=(2, 2), dtype=int32, numpy=
array([[23,  4],
       [32, 51]], dtype=int32)>
```

```python
# Obtener el tamaño de un tensor
tensor_20.shape
```

Salida

```bash
TensorShape([2, 2])
```

### Consultar los valores de una constante

```python
# Obtener los valores directamente desde una constante de TensorFlow con numpy, sin necesidad de una session
tensor_20.numpy()
```

```bash
array([[23,  4],
       [32, 51]], dtype=int32)
```

```python
# Podemos convertir un array de numpy a un tensor de TensorFlow directamente
numpy_tensor = np.array([[23,  4], [32, 51]])
tensor_from_numpy = tf.constant(numpy_tensor)
tensor_from_numpy
```

### Variables

```python
tf2_variable = tf.Variable([[1., 2., 3.], [4., 5., 6.]])
tf2_variable
```

```bash
<tf.Tensor: id=3, shape=(2, 2), dtype=int64, numpy=
array([[23,  4],
       [32, 51]])>
```

```python
# Consultar los valores de una variable
tf2_variable.numpy()
```

```python
# Cambiar un valor especifico de una variable
tf2_variable[0, 2].assign(100) # Fila 0 y columna 2 se cambia por 100
```

```bash
<tf.Variable 'UnreadVariable' shape=(2, 3) dtype=float32, numpy=
array([[  1.,   2., 100.],
       [  4.,   5.,   6.]], dtype=float32)>
```

```python
tf2_variable
```

```bash
<tf.Variable 'Variable:0' shape=(2, 3) dtype=float32, numpy=
array([[  1.,   2., 100.],
       [  4.,   5.,   6.]], dtype=float32)>
```

## Operaciones con tensores

```python
tensor = tf.constant([[1, 2], [3, 4]])
tensor
```

```python
tensor + 2 # Lo mismo sucede con la multiplicacion

```

```
<tf.Tensor: id=30, shape=(2, 2), dtype=int32, numpy=
array([[3, 4],
       [5, 6]], dtype=int32)>
```

Nota: Todo lo que puedes hacer con Numpy lo puedes hacer con Tensores.

```python
np.sqrt(tensor) # Puedes aplicarles todas las operaciones de Numpy
```

```python
 np.dot(tensor, tensor_20) # Operaciones producto escalar entre tensores
```

```bash
# tensor_20
array([[23,  4],
       [32, 51]], dtype=int32) 
       
# tensor
array([[3, 4],
       [5, 6]], dtype=int32)
       
# Producto Escalar
array([[ 87, 106],
       [197, 216]], dtype=int32)
```

## Strings en TensorFlow 2.0

```python
tf_string = tf.constant("TensorFlow")
tf_string
```

```bash
<tf.Tensor: id=41, shape=(), dtype=string, numpy=b'TensorFlow'>
```

```python
tf.strings.length(tf_string) ## El 
tf.strings.unicode_decode(tf_string, "UTF8") ## Decodificar cada letra del string 

tf_string_array = tf.constant(["TensorFlow", "Deep Learning", "AI"])

# Iterar sobre un array de strings en TF
for string in tf_string_array:
  print(string)
```

