# AutoHFormer: Efficient Hierarchical Autoregressive Transformer for Time Series Prediction

Time series forecasting requires architectures that simultaneously achieve three competing objectives: (1) strict temporal causality for reliable predictions, (2) sub-quadratic complexity for practical scalability, and (3) multi-scale pattern recognition for accurate long-horizon forecasting. We introduce AutoHFormer, a hierarchical autoregressive transformer that addresses these challenges through three key innovations: (1) Hierarchical Temporal Modeling: Our architecture decomposes predictions into segment-level blocks processed in parallel, followed by intra-segment sequential refinement. This dual-scale approach maintains temporal coherence while enabling efficient computation. (2) Dynamic Windowed Attention: The attention mechanism employs learnable causal windows with exponential decay, reducing complexity while preserving precise temporal relationships. This design avoids both the anti-causal violations of standard transformers and the sequential bottlenecks of RNN hybrids. (3) Adaptive Temporal Encoding: a novel position encoding system is adopted to capture time patterns at multiple scales. It combines fixed oscillating patterns for short-term variations with learnable decay rates for long-term trends. Comprehensive experiments demonstrate that AutoHFormer 10.76× faster training and 6.06× memory reduction compared to PatchTST on PEMS08, while maintaining consistent accuracy across 96-720 step horizons in most of cases.

## Overall Architecture

AutoHFormer adopts a hierarchical autoregressive framework. The prediction horizon is divided into segments, enabling the model to first generate coarse global predictions and then refine them step by step, effectively capturing both global and local dependencies.

<p align="center">
  <img src="AutoHFormer.png" alt="AutoHFormer Architecture" width="1000"/>
</p>

## Pseudo-code

The following pseudo-code illustrates the core workflow of AutoHFormer, including segment-level generation, windowed attention, and adaptive decay.

<p align="center">
  <img src="pseudo-code.png" alt="AutoHFormer Algorithm" width="450"/>
</p>

## Experiments
### Comparison to Benchmark
AutoHFormer achieves state-of-the-art results on several standard time series forecasting benchmarks, significantly outperforming existing methods.

<p align="center">
  <img src="experiments.png" alt="AutoHFormer Main Results" width="1000"/>
</p>

## How to run
1. Install requirements. ```python3 -m pip install -r requirements.txt```

2. Dataset Preparation. All the datasets are in ```./datasets```.

3. Training. To run experiments on other datasets, just execute the corresponding script:
```bash
bash scripts/Electricity/AutoHFormer.sh
bash scripts/Weather/AutoHFormer.sh
bash scripts/PEMS04/AutoHFormer.sh
```

4. Results.
All experiment logs are saved under `logs/LongForecasting/`

`@article{zhang2025autohformer,
  title={AutoHFormer: Efficient Hierarchical Autoregressive Transformer for Time Series Prediction},
  author={Zhang, Qianru and Wen, Honggang and Li, Ming and Huang, Dong and Yiu, Siu-Ming and Jensen, Christian S and Li{\`o}, Pietro},
  journal={arXiv preprint arXiv:2506.16001},
  year={2025}
}`
