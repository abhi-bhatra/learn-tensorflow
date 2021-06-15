<h1>Computer Vision Neural Networks on TensorFlow</h1>


### What is Computer Vision?
It is a field of Artificial Intelligence in which you train your Computer to recognize and understand the visual world.
Computer Vision is now widely used in almost every sector, from security-surveiliance to education.

### What is Computer Vision Neural Networks?
Embedding the power of Artificial Neural Nets in Computer Vision could help in understanding and solving problems more deeply.

### TensorFlow in Computer Vision
TensorFlow practices are giving next level hikes in learning and implementing Computer Vision. We can train Computer Vision Neural Nets very rapidly, with higher rates of accuracy.

---
#### About Module
In this module, we will take our knowledge of TensorFlow to next level by begining to solve problems of Computer Vision with just few lines of codes.

#### We are going to use MNIST-Fashion Dataset. It consist of 70,000 images of fashion products. To know more about this Dataset: 

<a href="https://github.com/zalandoresearch/fashion-mnist">Fashion MNIST dataset</a>

We are going to design the Neural Network and train it on this Large MNIST dataset. Then, our model can recognize different items of clothing, trained from a dataset containing 10 different types.
For our ease, and unbiased approach, clothings are given a number. Like: 

<img width="133" alt="MNIST-Labels" src="https://user-images.githubusercontent.com/63901956/122094315-aa3c6d80-ce29-11eb-97b6-d9f4263c0ce7.png">

<p>Here, you can see the different labels, for example: 0 -> T-shirt, 1 -> Trouser, ....so on.</p>


So, let's start coding.

```sh
import tensorflow as tf
```

Text on this import

```sh
mnist = tf.keras.datasets.fashion_mnist
```

Text on this import

```sh
(training_images, training_labels), (test_images, test_labels) = mnist.load_data()
```

Text on this import

```sh
import numpy as np
np.set_printoptions(linewidth=200)
import matplotlib.pyplot as plt
plt.imshow(training_images[0])
print(training_labels[0])
print(training_images[0])
```

Text on this import

```sh
training_images  = training_images / 255.0
test_images = test_images / 255.0
```

Text on this import

```sh
model = tf.keras.models.Sequential([tf.keras.layers.Flatten(), 
                                    tf.keras.layers.Dense(128, activation=tf.nn.relu), 
                                    tf.keras.layers.Dense(10, activation=tf.nn.softmax)])
```

Text on this import

```sh
model.compile(optimizer = tf.optimizers.Adam(),
              loss = 'sparse_categorical_crossentropy',
              metrics=['accuracy'])

model.fit(training_images, training_labels, epochs=5)
```

Text on this import

```sh
model.evaluate(test_images, test_labels)
```

Text on this import
