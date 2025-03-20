# Quantum Anonymous Transmission Using GHZ States in Qiskit

## Introduction

Quantum anonymous transmission (QAT) is a communication protocol where a sender can transmit information anonymously using quantum entanglement. The key concept is that no single participant can determine who sent the message, ensuring **privacy** and **security** through quantum mechanics. GHZ (Greenberger–Horne–Zeilinger) states play a crucial role in enabling this protocol.

This document explains the theory behind QAT using GHZ states, how the sender remains anonymous, and how to interpret the output.

## Theoretical Background

### 1. GHZ States and Their Role
A **GHZ state** is a maximally entangled quantum state shared among multiple participants. For `N` qubits, the GHZ state is:

$$ |GHZ\rangle = \frac{1}{\sqrt{2}} ( |00...0\rangle + |11...1\rangle ) $$

These states exhibit **nonlocal correlations**, meaning measurement of one qubit influences all others, even at a distance. This property is essential for secure and anonymous quantum communication.

GHZ states enable **quantum superposition of all participants**, meaning that from an external perspective, no single participant can be distinguished as the sender. The entanglement ensures that only when all participants collaborate can they extract useful information.

### 2. Quantum Anonymous Transmission (QAT)
In QAT, a sender encodes a classical bit (`0` or `1`) into a GHZ state without revealing their identity. This is achieved by leveraging entanglement and the symmetry of GHZ states. Any participant in the network could have sent the message, but no one can determine the exact sender.

#### How Anonymity is Preserved
- The GHZ state is **symmetrically shared** among all participants.
- The sender encodes a message by applying a **Pauli-Z operation** without altering the entanglement structure.
- Since **all participants share the same entangled state**, no single measurement reveals the sender’s identity.
- Only collective analysis of measurement outcomes determines the message while maintaining sender anonymity.

### 3. Encoding and Decoding in QAT
- **Encoding:** If the sender wants to transmit `0`, they do nothing. If they want to send `1`, they apply a **Pauli-Z gate** to their qubit. This introduces a phase shift, but does not break the entanglement.
- **Decoding:** All participants apply a **Hadamard gate (H)** before measurement. The collective measurement reveals whether the message is `0` or `1` but does not expose the sender.

The Hadamard transformation ensures that measurement results remain probabilistically distributed across participants while preserving the encoded information.

## Interpreting the Output
When the circuit is executed and measured, the output bitstrings must be analyzed as follows:

- **If the data bit is `0`** → The number of `1`s in the measurement results will be **even**.
- **If the data bit is `1`** → The number of `1`s in the measurement results will be **odd**.

### Why This Works
The even-odd pattern results from quantum interference and the entanglement properties of the GHZ state. Applying the **Hadamard transformation** redistributes the phase shifts introduced during encoding, leading to a measurable parity-based distinction without revealing individual actions.

## Implementation in Qiskit
To implement QAT in **Qiskit**, follow these steps:

1. **Create a GHZ state** by applying a Hadamard gate to the first qubit and a chain of CNOT gates.
2. **Encode the data bit** by applying a Pauli-Z gate if the bit is `1`.
3. **Decode the state** using Hadamard gates on all qubits.
4. **Measure all qubits** and analyze the results.

## Conclusion
Quantum anonymous transmission allows secure, sender-anonymous communication using the entanglement properties of GHZ states. By leveraging quantum superposition and measurement correlations, participants can detect messages without revealing the sender's identity. The use of GHZ states ensures that the system remains secure against interception and sender identification, contributing to the development of quantum-secure communication networks.

---

## 🤝 Contributing
Feel free to submit issues or pull requests if you find improvements!

## 📜 References
- Qiskit Documentation: [https://qiskit.org/documentation/](https://qiskit.org/documentation/)
- Nielsen & Chuang, "Quantum Computation and Quantum Information"
- M. A. Nielsen, I. L. Chuang, "Quantum Information Theory"
- Research papers on GHZ states and quantum anonymous transmission
- Bennett, Brassard, Crepeau, Skubiszewska, "Generalized Quantum Cryptography"
- Hillery, Bužek, Berthiaume, "Quantum Secret Sharing"

## 📜 License
This project is open-source under the MIT License.

---
Happy coding with **Qiskit!** 🚀
