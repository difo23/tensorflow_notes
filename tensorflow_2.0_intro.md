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
tf2_variable[0, 2].assign(100) # Fi
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

