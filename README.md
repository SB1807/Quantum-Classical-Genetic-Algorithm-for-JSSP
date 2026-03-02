# Entangled Genetic Quantum Alrgotithm (EQGA) for JSSP

A Hybrid Quantum-Classical Optimization Engine for solving NP-Hard Job Shop Scheduling  Problems.

## The Job Shop Scheduling Problem (JSSP) is a classical NP-Hard optimization challenge. This Project implements a *Quantum Genetic Algorithm (QGA)* to find  near optimal schedules.


By Mapping opperations directly to qubits, the algorithm leverages quantum superposition and entanglement to explore a search space of over *$2^{20}$ states for a 5x4 matrix*. (> 1 million states).

This project uses a **shot-based execution** on a custom **Noisy Backend** proving that the  evolutionary nature of the algorithm  can self correct and converge when running on quantum hardware.

## Key features 

* Succesfully maps and simulates a 5-Job, 4-Machine JSSP instance requiring a **20-qubit** circuit
* Utilizes a **CNOT Staircase** to create a multi-qubit entanglement, physically linking the decision probabilities od dependent operations.
* **Algorithmic Error Correction**: Implements a quantum mutation operator using stohstic **Pauli-X** bit flips to prevent premature convergence to local optima.
*  Simulates decoherence using `qiskit-aer`'s Depolarizing Error Channel. Features physically accurate asymmetric error rates (1% for single-qubit gates, 5% for two-qubit CNOT gates).
* Uses $R_y$ rotation gaets to incrementlly shoft probability amplitudes toward the global best solution over generations.


## Tehnical Architecture 

1. **State initialization** Uniform superposition via Hadamard ($H$) gates, followed by a CNOT ($CX$) chain for baseline entanglement.
2. **Measurement phase** Destructive, single-shot measurment on a noisy backend to simulate real hardwaee constraints and eliminate memory bottlenecks.
3. **Classical Decoder** Translates quantum binary strings into strict JSSP sequences, using Max-Plus algebra to resolve machine availibility and job percedence constraints.
4. **Evolution Phase** Applies variational rotation to reward succesful qubit states and controlled mutation ti maintain genetic diversity. 


## Instalation and Setup

To run this project, you need python 3.10+ and the following libraries:

``` pip install numpy, matplotlib, qiksit, qiskit-aer```

# Usage 

The project is optimized for Jupyter Notebooks. It is divided into modullar cells: 
1. Define the *Job_Data* dictionary. (max. 5x4 with 16 gb of RAM).
2. Configure the simulated Noisy backend *get_nnoisy_backend*.
3. Run the primary evolutionary loop *run_noisy_qga*.
4. Generate Visualizations. 



## Future Work (for now)

Finding a optimized solution for reducing the gate cost and number of Qubits 






