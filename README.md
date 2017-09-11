# Quantum Information Software Kit (QISKit)

[![Build Status](https://travis-ci.org/QISKit/qiskit-sdk-py.svg?branch=master)](https://travis-ci.org/QISKit/qiskit-sdk-py)

The Quantum Information Software Kit, or **QISKit** for short, is a software development kit (SDK) for working with [OpenQASM](https://github.com/QISKit/qiskit-openqasm) and the [IBM Quantum Experience (QX)](https://quantumexperience.ng.bluemix.net/). 

Use **QISKit** to create quantum computing programs, compile them, and execute them on one of several backends (online Real Quantum Processors, online Simulators, and local Simulators). For the online backends, QISKit uses our [python API client](https://github.com/QISKit/qiskit-api-py) to connect to the IBM Quantum Experience. 

**We use GitHub issues for tracking requests and bugs. Please see the** [IBM Q Experience community](https://quantumexperience.ng.bluemix.net/qx/community) **for questions and discussion.** **If you'd like to contribute to QISKit, please take a look at our** [contribution guidelines](CONTRIBUTING.rst).

Links to Sections:

* [Installation](#installation)
* [Create your first Quantum Program](#create-your-first-quantum-program)
* [More Information](#more-information)
* [Authors](#authors-(alphabetical))
* [License](#license)

# Installation

## Dependencies

[Python 3.5 or later](https://www.python.org/downloads/) is needed to use QISKit. In addition, [Jupyter Notebooks](https://jupyter.readthedocs.io/en/latest/install.html) is recommended for interacting with the tutorials.
For this reason we recomend installing [Anaconda 3](https://www.continuum.io/downloads) python distribution, as it comes with all of these dependencies pre-installed.

In addition, a basic understanding of quantum information is very helpful when interacting with QISKit. If you're new to quantum, start with our [User Guides](https://github.com/QISKit/ibmqx-user-guides)!

## Install QISKit

For those who are familiar with python, use the following install procedure:

### PIP Installation

The fastest way to install QISKit is by using the PIP tool (a python package manager):

```
    pip install qiskit
```

### Source Installation 

An alternative method is to clone the QISKit SDK repository in your local machine, and navigate to the cloned directory via terminal:

#### Download the code 

Select the "clone or download" button at the top of this webpage (or from the URL shown in the git clone command), unzip the file if needed, and then navigate to the **qiskit-sdk-py folder** in a terminal window.

#### Clone the repository 

Alternatively, if you have Git installed, run the following commands: 
```
    git clone https://github.com/QISKit/qiskit-sdk-py
    cd qiskit-sdk-py
```

### Setup you enviroment

We recomend using python virtual environments to improve your experience. [Setup the environment](doc/install.rst#3.1-Setup-the-environment)

## Create your first Quantum Program

Now that the SDK is installed, it's time to begin working with QISKit. First, get your API token:

-  Create an [IBM Quantum Experience (QX)](https://quantumexperience.ng.bluemix.net/) account if you haven't already done so
-  Get an API token from the Quantum Experience website under “My Account” > “Personal Access Token”

This API token allows you to execute your programs on the IBM Quantum Experience backends.

We are now ready to try out some QASM examples, which runs via the local simulator.

This is a simple superpesition example.

```
from qiskit import QuantumProgram

# Creating Programs create your first QuantumProgram object instance.
Q_program = QuantumProgram()

# Creating Registers create your first Quantum Register called "qr" with 2 qubits
qr = Q_program.create_quantum_register("qr", 2)
# create your first Classical Register called "cr" with 2 bits
cr = Q_program.create_classical_register("cr", 2)
# Creating Circuits create your first Quantum Circuit called "qc" involving your Quantum Register "qr" # and your Classical Register "cr"
qc = Q_program.create_circuit("superposition", [qr], [cr])

# add the H gate in the Qubit 0, we put this Qubit in superposition
qc.h(qr[0])

# add measure to see the state
qc.measure(qr, cr)

# Compiled  and execute in the local_qasm_simulator

result = Q_program.execute(["superposition"], backend='local_qasm_simulator', shots=1024)

# Show the results
print(result)
print(result.get_data("superposition"))
```

in this case the output will be:

```
COMPLETED
{'00': 509, '11': 515} 
```


You can execute your code on a [real Quantum Chip](https://github.com/QISKit/ibmqx-backend-information). More details on this and more so in [our QISKit documentation](doc/qiskit.rst).

### Next Steps

Now you're set up and ready to check out some of the other examples from our [Tutorials](https://github.com/QISKit/qiskit-tutorial) repository! Start with the [index tutorial](https://github.com/QISKit/qiskit-tutorial/blob/master/index.ipynb) and then go to the [‘Getting Started’ example](https://github.com/QISKit/qiskit-tutorial/blob/002d054c72fc59fc5009bb9fa0ee393e15a69d07/1_introduction/getting_started.ipynb). If you already have [Jupyter Notebooks installed](https://jupyter.readthedocs.io/en/latest/install.html), you can copy and modify the notebooks to create your own experiments.

These tutorials are developed using [Jupyter Notebooks](https://jupyter.org/), but can be accessed as read-only from their own github web page. To install the tutorials as part of the QISKit SDK, see the following installation details [installation details](doc/install.rst#Install-Jupyter-based-tutorials). Complete SDK documentation can be found in the [*doc* directory](doc/qiskit.rst).

## More Information

For more information on how to use QISKit, tutorial examples, and other helpful links, check this out:

* **[User Guides](https://github.com/QISKit/ibmqx-user-guides)**,
  a good starting place for learning about quantum information and computing
* **[Tutorials](https://github.com/QISKit/qiskit-tutorial)**,
  for example notebooks, start with the [index](https://github.com/QISKit/qiskit-tutorial/blob/master/index.ipynb) and [‘Getting Started’ Jupyter notebook](https://github.com/QISKit/qiskit-tutorial/blob/002d054c72fc59fc5009bb9fa0ee393e15a69d07/1_introduction/getting_started.ipynb)
* **[OpenQASM](https://github.com/QISKit/openqasm)**,
  for additional information and examples of QASM code
* **[IBM Quantum Experience Composer](https://quantumexperience.ng.bluemix.net/qx/editor)**,
  a GUI for interacting with real and simulated quantum computers
* **[QISkit Python API](https://github.com/QISKit/qiskit-api-py)**, an API to use the IBM Quantum Experience in Python


QISKit was originally developed by researchers and developers of the [IBM-Q](http://www.research.ibm.com/ibm-q/) Team within [IBM Research](http://www.research.ibm.com/), with the aim of offering a high level development kit to work with quantum computers.

Visit the [IBM Q Experience community](https://quantumexperience.ng.bluemix.net/qx/community) for questions and discussions on QISKit and quantum computing more broadly. If you'd like to contribute to QISKit, please take a look at our [contribution guidelines](CONTRIBUTING.rst).


## Authors (alphabetical)

Jim Challenger, Andrew Cross, Ismael Faro, Jay Gambetta, Juan Gomez, Paco Martin, Antonio Mezzacapo, Jesus Perez, and John Smolin, Erick Winston, Chris Wood.

In future releases, anyone who contributes with code to this project is welcome to include their name here.


## License

This project uses the [Apache License Version 2.0 software license](https://www.apache.org/licenses/LICENSE-2.0).


