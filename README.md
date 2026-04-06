
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
from qiskit.visualization import plot_bloch_multivector
from qiskit.quantum_info import Statevector 

qc = QuantumCircuit(1)
qc.h(0)

state = Statevector.from_instruction(qc)
plot_bloch_multivector(state)
<img width="585" height="216" alt="image" src="https://github.com/user-attachments/assets/4c5f5a72-69a2-4f58-a445-0d047b3b6708" />
