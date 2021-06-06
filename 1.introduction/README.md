<h1>Fullfilling the requirements</h1>
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
conda create -n tensorflow-env
Proceed ([y]/n)?  # Type 'Y' to proceed
conda activate tensorflow-env
````

<p>Above code will create an anaconda environment for you. It is a directory that contains a specific collection of conda as well pip packages which are isolated from rest of your workspace and the package you install in this environment, will not be downloaded in your complete system.
<br />
<br />
Understanding the code: 
<ul>
  <li>conda create : use to create new environment.</li>
  <li>tensorflow-env: name of your new env. (It can be anything)</li>
  <li>conda activate: use to activate your environment. Basically it switched from default(base) -> your env(tensorflow-env).</li>
</ul>
<br />
Check the modules installed, (by default) in your newly created env:
</p>

```sh
pip freeze
```
<p>Above command will give you the list of modules, which comes pre-installed with your new environment.</p>

