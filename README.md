# Quantum-Anonymous-Transmission
Quantum Anonymous Transmission Using Qiskit

# Quantum Teleportation with GHZ States

## Overview

This repository contains an implementation of quantum teleportation using GHZ (Greenberger-Horne-Zeilinger) states with Qiskit. The code demonstrates how to create entangled quantum states across multiple qubits and use them to transmit quantum information.

## Theory

### GHZ States

GHZ states are maximally entangled quantum states involving three or more qubits. For an n-qubit system, the GHZ state is represented as:

|GHZ⟩ = (|00...0⟩ + |11...1⟩)/√2

These states exhibit perfect correlations: when measuring all qubits in the same basis, we either get all 0s or all 1s.

### Quantum Communication Protocol

This implementation focuses on a quantum communication protocol using GHZ states where:

1. A GHZ state is created across N qubits
2. A sender encodes a classical bit (0 or 1) into the quantum state
3. All participants apply Hadamard gates to decode the message
4. Measurement results reveal which participant was the sender and what message was sent

The key quantum phenomena utilized:

- **Quantum Entanglement**: The non-local correlations between entangled qubits
- **Quantum Superposition**: The ability of quantum systems to exist in multiple states simultaneously
- **Phase Kickback**: How operations on one qubit can affect the global phase of an entangled system

### Mathematical Explanation

Starting with an N-qubit system in state |00...0⟩, applying a Hadamard gate to the first qubit and CNOT gates to the rest creates the GHZ state:

(|00...0⟩ + |11...1⟩)/√2

When the sender applies a Z gate to encode a "1":
- If the sender applies Z to their qubit: (|00...0⟩ - |11...1⟩)/√2
- If the sender doesn't apply any gate (to encode "0"): (|00...0⟩ + |11...1⟩)/√2

After all participants apply Hadamard gates:
- For data=0: All participants measure the same value (all 0s or all 1s)
- For data=1: The sender's measurement will be the opposite of all other participants

## Code Structure

The code is organized into several functions:

- `create_ghz()`: Creates an N-qubit GHZ state
- `encode_data()`: Encodes a classical bit into the quantum state
- `decoding()`: Applies Hadamard gates to decode the message
- `measurement()`: Measures all qubits in the computational basis
- `create_circuit()`: Combines all steps into a complete circuit
- `execute()`: Runs the quantum circuit on a simulator

## Usage

```python
# Set parameters
number_of_clients = 5  # Number of qubits in the GHZ state
sender = 2             # Index of the sender (0 to number_of_clients-1)
data = 1               # Data bit to encode (0 or 1)
shots = 1024           # Number of times to run the circuit

# Create and run the circuit
qc = create_circuit(number_of_clients, sender, data)
qc.draw("mpl")         # Visualize the circuit
results = execute(qc, shots)
counts = results.get_counts()
plot_histogram(counts) # Visualize the results
