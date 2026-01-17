
# CUDA-Based Monte Carlo Option Pricing

High-performance Monte Carlo simulation framework in C++ and CUDA for pricing **European, Asian, American, and Basket options**. Benchmarks CPU vs GPU implementations.

## Features

- European Call/Put
- Asian (Arithmetic Average)  
- American (Early Exercise - CPU only)
- Basket (Multiple Assets)
- CPU & GPU (CUDA) implementations
- Template-based payoff abstraction
- CLI support (`cxxopts`)
- RAII Timer for benchmarking
- Fixed-seed RNG for reproducibility

## Prerequisites

- C++17 compiler
- NVIDIA GPU + CUDA Toolkit
- CMake or Make
- `cxxopts` (included)

## Project Structure

```
.
├── include/
│   ├── benchmark.hpp
│   ├── european.cuh
│   ├── asian.cuh
│   ├── basket.cuh
│   └── american.cuh
├── src/
│   ├── main.cu
│   ├── european.cu
│   ├── asian.cu
│   ├── basket.cu
│   └── american.cu
├── benchmarking/
│   └── *.cu
├── third_party/cxxopts/
├── Results.ipynb
└── README.md
```

## Build

```bash
mkdir build && cd build
cmake .. -DCUDA_ARCHITECTURES=80
make -j
```

## Usage

```bash
# European Call (GPU)
./option_pricer --type european --payoff call --method gpu \
  --paths 1e6 --S0 100 --K 100 --r 0.05 --sigma 0.2 --T 1.0

# Help
./option_pricer --help
```

## Results

See `Results.ipynb` for CPU/GPU benchmarks.
