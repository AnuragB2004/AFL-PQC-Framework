# AFL-PQC Framework

**Scalable Quantum Circuit Architectures and Hybrid Variational Workflows for High-Impact Computational Intelligence Applications**

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/AnuragB2004/AFL-PQC-Framework.git
cd AFL-PQC-Framework

# Create environment
python -m venv afl_env
source afl_env/bin/activate  # Linux/Mac
# afl_env\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt

# Run complete experiment (15s execution)
python afl_pqc_framework.py

# View results
open afl_pqc_results_fixed.png
```

**Expected Output**:
```
✅ Converged at iteration 15
✅ Final cost: 0.1582
📈 66% faster than VQE baseline
```

***

## 🧬 Core Features

### **Implemented Algorithms** (from paper)
| Algorithm | Description | Status |
|-----------|-------------|--------|
| **Alg 1** | Parameter-shift gradients (Eq. 6) | ✅ |
| **Alg 2** | Readout error mitigation | ✅ |
| **Alg 3** | AFL optimizer (Eq. 8) | ✅ |

### **Circuit Architectures** (Figs 2-5)
```
1. Hardware-efficient (Eq. 1) ✓
2. Alternating layered (Eq. 4) ✓
3. Fully entangled (Eq. 7) ✓
4. Hierarchical 5-qubit ✓
```

### **Error Mitigation**
- Zero-noise extrapolation (ZNE) [Fig 9]
- Readout error mitigation [Alg 2]
- Multi-stage pipeline [Fig 10]

***

## 📊 Verified Results

**Exact reproduction** of paper results:

```
AFL-PQC: 4q, L=3, params=36
Iter  0: Cost=0.1777, LR=0.0077
...
Iter 15: Cost=0.1582, LR=0.0051 ✅ Converged!

Fidelity: 93.2% (vs VQE 72.3%) [+28.9%]
Convergence: 15 iter (vs VQE 45) [-66%]
CNOTs: 32 (vs VQE 45) [-29%]
```


*Figure 13: Exact convergence from code execution*

***

## 🛠️ Directory Structure

```
AFL-PQC-Framework/
├── afl_pqc_framework.py      # Main implementation
├── experiments/
│   ├── maxcut_4q.ipynb      # MaxCut benchmark
│   ├── portfolio.ipynb      # Portfolio optimization
│   └── h2_molecule.ipynb    # H₂ ground state
├── docs/
│   ├── afl_pqc_results_fixed.png  # Paper Fig 13
│   └── paper.pdf                   # Full manuscript
├── results/                   # Raw data
├── requirements.txt
└── README.md
```

***

## 🔬 Benchmark Problems

| Problem | Qubits | Hamiltonian | Accuracy |
|---------|--------|-------------|----------|
| **MaxCut** | 4 | `0.5(ZZII+IZZI+IIZZ+ZIZI)` | 100% |
| **Portfolio** | 4 | `∑QᵢⱼZᵢZⱼ - ∑μᵢZᵢ` | +12.3% |
| **H₂ Molecule** | 4 | Jordan-Wigner | 0.24% error |

***

## ☁️ IBM Quantum Hardware

**Tested backends**: `ibm_brisbane`, `ibm_kyoto`

```python
service = QiskitRuntimeService()
backend = service.least_busy(simulator=False)
job = sampler.run(compiled_circuit, shots=1024)
```

**Hardware specs** (Jan 2026):
```
Qubits: 127  |  T₁: 85-145μs  |  CNOT: 6-8×10⁻³
Fidelity: 93.2%  |  ZNE: +4.8% improvement
```

***

## 📈 Performance vs Baselines

| Method | Fidelity | Iterations | CNOTs |
|--------|----------|------------|-------|
| VQE (Kandala 2017) | 72.3% | 45 | 45 |
| QAOA (p=3) | 68.7% | 95 | 54 |
| **AFL-PQC** | **93.2%** | **15** | **32** |

**Improvements**: **+28.9% fidelity**, **-66% iterations**, **-29% CNOTs**

<img width="4170" height="2966" alt="afl_pqc_results_fixed" src="https://github.com/user-attachments/assets/fa30f7d8-d456-4d5d-a830-107500424e18" />


***

## 🔧 Installation

### **Minimal (Simulator)**
```bash
pip install qiskit qiskit-aer matplotlib numpy
```

### **Full (IBM Quantum)**
```bash
pip install -r requirements.txt
qiskit-ibm-runtime login  # IBM Quantum token
```

**requirements.txt**:
```
qiskit>=1.0.2
qiskit-aer>=0.13.0
qiskit-ibm-runtime>=0.21.0
numpy>=1.24.3
matplotlib>=3.7.1
scipy>=1.11.1
```

***

## 📚 Paper Reference

**Compares against**: Kandala et al. (2017) *Nature* ["Hardware-efficient VQE"](https://arxiv.org/abs/1704.05018)

**Key novelty**:
```
AFL-PQC = Hardware-efficient VQE + Adaptive LR + ZNE + Multi-ansatz
        = 93.2% fidelity vs 72.3% baseline
```

***

## 🤝 Contributing

1. Fork repository
2. Create feature branch (`git checkout -b feature/afl-enhancement`)
3. Commit changes (`git commit -m 'Add AFL momentum'`)
4. Push (`git push origin feature/afl-enhancement`)
5. Open Pull Request

***

## 📄 License

[MIT License](LICENSE) - Free for academic/industrial use

***

## 🛡️ Support

**Issues**: [Create New Issue](https://github.com/AnuragB2004/AFL-PQC-Framework/issues/new)  
**Discussions**: [Join Discussion](https://github.com/AnuragB2004/AFL-PQC-Framework/discussions)

**Contact**: anuragdgp@gmail.com
