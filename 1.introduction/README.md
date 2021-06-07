<h1>Chapter 1: Introduction</h1>

<h3>Installing Python</h3>
<p>To install python, redirect to: <a href="https://www.python.org/downloads/">python.org</a>.
  <br />
  <ul>
    <li>Depending on your operating systems, download the python version >= 3.7</li>
    <li>Run the setup wizard</li>
    <li>Add Python to your path, so that you can execute it through your terminal</li>
  </ul>
  Check, if Python installed, by running this in your terminal/cmd:
</p>

```sh
  python --version
```


<h3>Installing Anaconda</h3>
<p>
  To install Anaconda, redirect to: <a href="https://www.anaconda.com/products/individual#Downloads">anaconda.com</a>
  <br/>
  <ul>
    <li>Depending on your operating systems, download the Anaconda installer</li>
    <li>Follow the instructions in installation setup to successfully install Anaconda</li>
    <li>Now, open Anaconda Prompt</li>
    <li>Type the commands to setup your environment (where we will operate our Tensorflow codes)</li>
  </ul>
</p>

```sh
conda create -n tf tensorflow
Proceed ([y]/n)?  # Type 'Y' to proceed
conda activate tf
````

<p>Above code will create an anaconda environment for you, dedicated for tensorflow. It is a directory that contains a specific collection of conda as well pip packages which are isolated from rest of your workspace and the package you install in this environment, will not be downloaded in your complete system.
<br />
<br />
Understanding the code: 
<ul>
  <li>conda create : use to create new environment.</li>
  <li>tf: name of your new env. (It can be anything)</li>
  <li>conda activate: use to activate your environment. Basically it switched from default(base) -> your env(tensorflow-env).</li>
</ul>
<br />
Check the modules installed, (by default) in your newly created env:
</p>

```sh
pip freeze
```
<p>Above command will give you the list of modules, which comes pre-installed with your new environment.</p>

**Verify that, jupyter-lab, jupyter is installed and present in the list of installed modules.**
<p>If it is not installed, run the code: </p>

```sh
conda install -c conda-forge jupyterlab
Proceed ([y]/n)?  # Type 'Y' to proceed
```
<p>Now, We will run the Jupyter Notebook. Run the following code: </p>

```sh
jupyter-notebook
```

<h3>Working with the Jupyter Notebook</h3>
<p>1. You will see the following interface, opened in your browser: </p>
<img width="858" alt="jupter-gui" src="https://user-images.githubusercontent.com/63901956/120922977-cc2b4700-c6e9-11eb-8e2b-f13c2770973b.png">

<p>2. Click on new -> select Python 3 (from Notebook section). This will create a new notebook for you.</p>
<img width="858" alt="select-new-jupyter-notebook" src="https://user-images.githubusercontent.com/63901956/120923193-def24b80-c6ea-11eb-8491-a0bb51bbb562.png">

<p>3. Name your files as hello-world
<br />
4. Now, we will execute commands in our jupyter shell, and run it using the (run) button  
</p>

To run the cell either press `shift` + `enter` or click on the run button.

<br />
<img width="858" alt="Untitled" src="https://user-images.githubusercontent.com/63901956/120955602-58cc1880-c76f-11eb-9846-15fb2a33a236.png">
<p>To know more about Jupyter-Notebooks, visit: <a href="https://jupyter.readthedocs.io/en/latest/running.html">running-jupyter-notebooks</a></p>

---

<h3>Lab</h3>
<p>In this lab, we are going to create our first Neural Network using Tensorflow. The sample that I would like to use is that, we are going to find the relationship between two numbers. <br />
  So, for example, if we have a function such that: </p>
  
  `y = (2 * x) - 1` 
  then we will return y
Instead of using this function, we will see, how would neural network can do equivalent task? Using data! By feeding with a set of Xs and a set of Ys, it should be able to figure out the relationship between them.

<p>This is obviously a very different paradigm than what you might be used to, so let's step through it piece by piece.</p>

> Now write the codes below in each cell and run the each cell to observe the output
  
```sh
import tensorflow as tf
import numpy as np
from tensorflow import keras
```
1. Here, we have imported `Tensorflow` module and going to use it as tf(alias).
2. Then, we will use `Numpy`, numpy will help us to represent our data as lists easily.
3. Then we call for `Keras`, it is neural network framework library for defining the Sequential layers.

```sh
xs = np.array([-1.0,  0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
ys = np.array([-3.0, -1.0, 1.0, 3.0, 5.0, 7.0], dtype=float)
```
Here, we'll feed in some data. In this case, we took 6 Xs and 6 Ys. By the data, it is well known that the relationship between Xs and Ys is `Y = 2 * X - 1`
We use `Numpy` for storing our array. 
<br />
We declare the values in np.array[]

```sh
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])]
```

Now, we have created a simplest possible Neural Network. On compiling the above code. It has 1 layer `keras.layers.Dense` and this layer has 1 neuron `units=1` and the input shape is is `input_shape=[1]`


```sh
model.compile(optimizer='sgd', loss='mean_squared_error')
```

Now, we have compiled our Neural Network, we just created. Here we specify 2 functions. The LOSS function and the OPTIMIZER function.
<br />
We know that our function follows the relationship between numbers is y=2x-1.
<br />

But when the computer is trying to 'learn' that, it make guess.... maybe y=10x-10. The LOSS function measure the guessed answers against the known correct answers and measures how well or how badly it did.
<br />

It then uses the OPTIMIZER function to make another guess. Based on how the loss function went, it will try to minimize the loss. At that point maybe it will come up with somehting like y=5x+5, which, while still pretty bad, is closer to the correct result (i.e. the loss is lower)

1. The optimizer function we used here is, `optimizer='sgd'`. SGD is Stochastic Gradient Descent. It is a "classical" algorithm for optimization. We compute the gradient of the network LOSS function with respect to each individual weight in the network. Each forward pass through the network results in a certain parameterized loss function, and we use each of the gradients we've created for each of the weights, multiplied by a certain learning rate, to move our weights in whatever direction its gradient is pointing.
<br />

SGD's simplicity makes it a good choice for shallow networks. However, it also means that SGD converges significantly more slowly than other, more advanced algorithms that are also available in `Keras`

2. We are using LOSS function `loss='mean-squared-error'` because this is a **Regression Problem**.

<br />
Regression Predictive Models involve predicting real-valued quantity. Mean Square error or MSE is a default loss to use for regression problems. It is the loss function to be evaluated first and only changed if you have a good reason. Mean squared error is calculated as the average of the squared differences between the predicted and actual values. The squaring means that larger mistakes result in more error than smaller mistakes, meaning that the model is punished for making larger mistakes.
<p>Know more about loss functions in Keras: <a href="https://keras.io/api/losses/">Keras-Loss-Functions</a></p>

<p>Know more about types of Machine Learning Problems: <a href="https://machinelearningmastery.com/classification-versus-regression-in-machine-learning/">(Regression, Binary Classification and Multiple Classification)</a></p>

```sh
model.fit(xs, ys, epochs=500)
```

So, far we have created a layer and compiled it using the respective loss functions and optimizers. Now, we will call for `model.fit()` where it learns the relationship between Xs and Ys. Here, the code will go into loop, making guess on how 'good' or 'bad' it is, and uses optimizer to make another guess. `epochs` indicates the number of passes of the entire array and train the data with the neural network on each pass.

```sh
print(model.predict([10.0]))
```

Finally, we'll predict using `model.predict()` to figure out the Y for a previously unknown X. For example above, if `X=10`, what do you think Y will be?

<br />

Well, theoretically `Y=2X-1`, so the answer should be 19, right?
But, it ended up being a little under. Why do you think that it?
<br />

Remember that neural networks deal with probabilities, so given the data that we fed the NN with, it calculated that there is a very high probability that the relationship between X and Y is Y=2X-1, but with only 6 data points we can't know for sure. As a result, the result for 10 is very close to 19, but not necessarily 19.
