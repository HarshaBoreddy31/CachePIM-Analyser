# CachePIM: 4-to-7 Minute Demonstration Video Script

This script provides a structured, minute-by-minute guide for recording the 4 to 7-minute demonstration video required for project submission.

---

### Suggested Video Breakdown (Total: ~5 minutes 30 seconds)

#### **1. Introduction & Project Motivation (0:00 – 1:00)**
- **Screen:** Show the GitHub Repository / Title Slide / Dashboard Header (`http://localhost:8505`).
- **Narration:**
  > *"Hello everyone and Professor Bhuvaneswari. Today we are presenting **CachePIM**, an analytical research simulation framework designed to explore the performance crossover between host CPU cache hierarchies and Processing-in-Memory (PIM) architectures. 
  > While PIM addresses the memory bandwidth wall by moving computation directly into DRAM, it introduces offloading costs like host-to-device transfers, kernel launch overheads, and conservative clock speeds. In contrast, CPU cache hits can service operands in 1 to 2 nanoseconds. CachePIM provides a rapid, trace-driven analytical simulator capable of evaluating thousands of joint cache and interconnect configurations in seconds, calibrated against published physical UPMEM DPU hardware measurements with a 3.57% MAPE."*

#### **2. System Architecture & Workload Modes (1:00 – 2:00)**
- **Screen:** In the Streamlit sidebar, show the **Workload Configuration** dropdown and parameter controls.
- **Narration:**
  > *"CachePIM supports both parametric synthetic patterns—such as STREAM, REUSE, RANDOM, and MIXED_PHASE—and real 64-bit dynamic memory traces captured from standard PrIM benchmarks like Vector Addition, GEMV, Binary Search, and Select using Valgrind Lackey binary instrumentation.
  > In the sidebar, users can tune architectural parameters: CPU cache capacity from 8 to 256 KiB, set-associativity, host-to-PIM transfer bandwidth, and PIM bank counts."*

#### **3. Interactive 3D WebGL Volumetric Execution Arena (2:00 – 3:15)**
- **Screen:** Click **"Run Simulation"**, then scroll through the **KPI cards** and interact with the **3D / Isometric Execution Arena** in Tab 1 (rotate, zoom).
- **Narration:**
  > *"Here is the interactive 3D WebGL Execution Arena. On the left side, we visualize the host CPU cache hierarchy with animated memory access packets and hit/miss counters. On the right, we visualize the bank-parallel PIM memory array showing per-bank load distribution and bank skew factors.
  > Below the arena, our component-level cost breakdown shows how total execution latency decomposes into hit service, miss service, transfer time, and internal DRAM row-buffer access."*

#### **4. Multi-Policy Offloading Evaluation & Regret Analysis (3:15 – 4:15)**
- **Screen:** Navigate to **Tab 2: Policy Evaluation**. Show the policy comparison bar chart.
- **Narration:**
  > *"In Tab 2, CachePIM evaluates six distinct offloading policies: CPU-cache, CPU-no-cache, PIM-always, Cost-based, Reuse-aware, and an offline Oracle.
  > Across a balanced 500-instance evaluation grid, blind PIM offloading incurs a 34% bad-offload rate. In contrast, our analytical Cost-Based policy achieves 96% decision accuracy with zero missed offloads and near-zero regret."*

#### **5. 2D Crossover Heatmap & Architectural Sweeps (4:15 – 5:00)**
- **Screen:** Navigate to **Tab 3: Crossover Analysis**. Show the 2D Heatmap (Cache Capacity vs. Link Bandwidth) and Bank Scaling curve.
- **Narration:**
  > *"In Tab 3, we map the performance crossover boundary. The 2D heatmap clearly illustrates the regime where CPU cache residency outperforms PIM: when interconnect links are constrained to 1 to 4 GB/s and cache capacity accommodates working sets, host CPU execution is up to 2.78x faster than PIM."*

#### **6. Terminal Verification & Conclusion (5:00 – 5:45)**
- **Screen:** Switch to Terminal and run `pytest tests/` (showing 35 passed tests) and display `results/manifest.json`.
- **Narration:**
  > *"Finally, CachePIM is built for complete scientific reproducibility. Running our automated test suite executes 35 regression and invariant unit tests in under 30 seconds.
  > All simulation results, figures, and manuscripts are fully open-source and reproducible. Thank you!"*
