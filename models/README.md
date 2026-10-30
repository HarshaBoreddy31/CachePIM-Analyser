# CachePIM Model Architecture Specification

## Note on Machine Learning / Deep Learning Models
**CachePIM is an analytical microarchitectural and memory hierarchy simulator**, not a machine-learning / deep-learning predictive model. 

- **No Pretrained Neural Weights:** Unlike neural network-based surrogate models, CachePIM evaluates exact, inspectable, closed-form architectural equations founded upon physical hardware principles (exact LRU cache hit/miss counting, $N$-way set-associativity mapping, interconnect transfer bandwidth, and DRAM row-buffer locality).
- **Deterministic Mathematical Formulations:**
  - CPU latency: $T_{\text{CPU}} = N_{\text{hit}} \cdot t_{\text{hit}} + N_{\text{miss}} \cdot t_{\text{miss}} + N_{\text{op}} \cdot t_{\text{compute}} + T_{\text{writeback}}$
  - PIM latency: $T_{\text{PIM}} = T_{\text{H2P}} + T_{\text{internal\_mem}} + T_{\text{compute}} + T_{\text{imbalance}} + T_{\text{P2H}} + T_{\text{launch}} + T_{\text{sync}}$
  - Pipelined overlap: $T_{\text{pipelined}} = \max(T_{\text{H2P}}, T_{\text{exec}}) + (1 - \alpha) \cdot \min(T_{\text{H2P}}, T_{\text{exec}})$
- **Policy Decision Engine:** The offloading policies (`Cost-based`, `Reuse-aware`, `Oracle`, `PIM-always`, `CPU-cache`) perform deterministic analytical cost evaluation.

Therefore, no external binary model weights (e.g., `.pt`, `.onnx`, `.bin`, `.h5`) are required. All model logic is self-contained in the `cachepim/` package.
