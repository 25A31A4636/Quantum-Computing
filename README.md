# Quantum-Computing
This project demonstrates a simple quantum circuit using Qiskit. A Hadamard gate is applied to a single qubit to create superposition. The qubit is measured into a classical bit using AerSimulator. Results show an approximately 50/50 distribution of 0s and 1s.
from qiskit import QuantumCircuit, transpile
from qiskit_aer import AerSimulator

# Create a quantum circuit with 1 qubit and 1 classical bit
qc = QuantumCircuit(1, 1)
qc.h(0)          # Apply Hadamard gate
qc.measure(0, 0) # Measure qubit into classical bit

# Initialize simulator
simulator = AerSimulator()

# Transpile circuit for simulator
compiled_circuit = transpile(qc, simulator)

# Run simulation
result = simulator.run(compiled_circuit, shots=1000).result()

# Get counts
counts = result.get_counts()
