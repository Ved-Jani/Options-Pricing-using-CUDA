# Monte Carlo Option Pricing with C++ & CUDA 🚀

A high-performance Monte Carlo simulation framework for pricing financial derivatives using **C++17** and **CUDA**. This project supports multiple option types and provides both **CPU and GPU implementations** for benchmarking and performance comparison.

---

## 📌 Features

### Supported Option Types
- European Options (Call / Put)
- Asian Options (Arithmetic Average)
- American Options (Early Exercise – CPU only)
- Basket Options (Multiple Assets)

### Technical Highlights
- CPU & GPU (CUDA) implementations
- Template-based payoff abstraction (`CallPayoff`, `PutPayoff`)
- Fixed-seed RNG for reproducible simulations
- RAII-based benchmarking timer
- Command-line interface using **cxxopts**
- Modular architecture with clean host/device separation

---

## 📁 Project Structure
├── include/
│ ├── benchmark.hpp
│ ├── european.cuh
│ ├── asian.cuh
│ ├── basket.cuh
│ └── american.cuh
├── src/
│ ├── main.cu
│ ├── european.cu
│ ├── asian.cu
│ ├── basket.cu
│ └── american.cu
├── benchmarking/
│ ├── european.cu
│ ├── asian.cu
│ ├── basket.cu
│ └── american.cu
├── third_party/
│ └── cxxopts/
│ └── cxxopts.hpp
├── Results.ipynb
└── README.md


---

## 🛠 Prerequisites

- C++17 compatible compiler
- NVIDIA GPU with CUDA support
- CUDA Toolkit installed
- `nvcc` compiler
- cxxopts library (included)

---

## ⚙️ Build Instructions

Compile using `nvcc`:

```bash
nvcc -std=c++17 -arch=<gpu_architecture> \
  -Iinclude -Ithird_party/cxxopts \
  src/main.cu src/european.cu src/asian.cu src/basket.cu src/american.cu \
  -o option_pricer
