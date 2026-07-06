# Awesome Streaming Agents [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of **streaming agents**, covering AI systems (VLM/VLA/video) that are **time-sensitive**, **real-time responsive**, **proactive** (continuously activated without explicit user prompts), and capable of processing **unbounded streaming inputs**.


## Contents

- [A. Streaming Multimodal Model](#a-streaming-multimodal-model)
- [B. Proactive Interaction & Continuous Activation](#b-proactive-interaction--continuous-activation)
- [C. Streaming VLA & Real-Time Embodied Control](#c-streaming-vla--real-time-embodied-control)
- [D. Time-Sensitive Serving & Streaming Backends](#d-time-sensitive-serving--streaming-backends)
- [Benchmarks](#benchmarks)
- [Contributing](#contributing)

---

## A. Streaming Multimodal Model

*Models that accept continuous, unbounded video/audio streams with constant-memory KV-cache or low-latency constraints, maintaining long-term understanding. Includes full-duplex audio-visual interaction models.*

> Papers listed in reverse chronological order.

- **Wan-Streamer**: *Wan-Streamer v0.1: End-to-end Real-time Interactive Foundation Models*. *arXiv, Jun 2026*.
  - **Authors/Institution**: Lianghua Huang, Zhifan Wu, Wei Wang et al. (Alibaba Wan Team)
  - **Core Contribution**: First native streaming end-to-end real-time full-duplex audio-visual interaction foundation model. Causal streaming of language, audio, and video within a single Transformer (~200ms model latency, ~550ms total). No external VAD/ASR/LLM/TTS/avatar modules.
  - **Links**: [[Paper](https://arxiv.org/abs/2606.25041)] | [[Project](https://wan-streamer.com/)]

- **Stream3D-VLM**: *Stream3D-VLM: Online 3D Spatial Understanding with Incremental Geometry Priors*. *arXiv, Jun 2026*.
  - **Authors/Institution**: Hanxun Yu, Xuan Qu, Lei Ke et al. (Zhejiang University; Tencent Hunyuan)
  - **Core Contribution**: First streaming online 3D VLM — autoregressive streaming control via next-token prediction for response timing, Visual-Spatial Feature Integration (VSFI) for incremental geometry priors, and Geometry-Adaptive Voxel Compression (GAVC) for efficient token compression. 1M+ online 3D QA pairs across 29 tasks.
  - **Links**: [[Paper](https://arxiv.org/abs/2606.06891)] | [[Project](https://stream3d-vlm.github.io/)]

- **DuplexOmni**: *DuplexOmni: Real-Time Listening, Seeing, Thinking, and Speaking for Full-Duplex Interaction*. *arXiv, Jun 2026*.
  - **Authors/Institution**: Muye Huang, Lingling Zhang, Xingyu Yu et al. (Xi'an Jiaotong University, Peking University; Meituan)
  - **Core Contribution**: Decouples real-time multimodal full-duplex interaction into asynchronous parallel dual-layer architecture — interaction layer (end-to-end streaming audio/video → text/speech, low latency) + thinking layer (pluggable reasoning and tool-use, background execution). Full-duplex supports in-speech interruption and continuous perception-expression.
  - **Links**: [[Paper](https://arxiv.org/abs/2606.09186)]

- **JoyAI-VL-Interaction**: *JoyAI-VL-Interaction: Real-Time Vision-Language Interaction Intelligence*. *JD.com Tech Report, Jun 2026*.
  - **Authors/Institution**: Dingyu Yao, Junhao Zhou, Chenxu Yang et al. (JD.com)
  - **Core Contribution**: Real-time streaming VLM with AdaCodec long-horizon memory compression and GRPO-trained proactive response mechanism. Supports interactive AI companion scenarios: commentating, guidance, multi-speaker coordination.
  - **Links**: [[Project](https://joyai-vl-video-future-academy-jd.github.io/JoyAI-VL-Interaction/)] | [[Code](https://github.com/jd-opensource/JoyAI-VL-Interaction)]

- **StreamReady**: *StreamReady: Learning What to Answer and When in Long Streaming Videos*. *CVPR, 2026*.
  - **Authors/Institution**: Shehreen Azad, Vibhav Vineet, Yogesh Singh Rawat (UCF CRCV, Microsoft Research)
  - **Core Contribution**: First work treating "when to answer" as a first-class metric. Introduces Answer Readiness Score (asymmetric early/late penalties), three-tier visual memory tree (FIFO → K-Means → EMA prototypes), and `<RDY>` token with readiness head. ProReady-QA benchmark (32 videos, 5000 proactive QA with evidence-window annotations).
  - **Links**: [[Paper](https://arxiv.org/abs/2603.08620)] | [[Project](https://sacrcv.github.io/StreamReady-website/)]

- **VST (Video Streaming Thinking)**: *Video Streaming Thinking: VideoLLMs Can Watch and Think Simultaneously*. *arXiv, Mar 2026*.
  - **Authors/Institution**: Yiran Guan, Liang Yin, Dingkang Liang et al. (HUST, Xiaomi MiLM)
  - **Core Contribution**: Introduces "thinking while watching" paradigm — interleaves proactive pre-query reasoning with video consumption, amortizing LLM reasoning latency over playback. VST-SFT + VST-RL post-training pipeline with video knowledge-graph data synthesis. VST-7B: 79.5% StreamingBench, 15.7× faster than Video-R1.
  - **Links**: [[Paper](https://arxiv.org/abs/2603.12262)] | [[Code](https://github.com/1ranGuan/VST)]

- **OmniStream**: *OmniStream: Mastering Perception, Reconstruction and Action in Continuous Streams*. *arXiv, Mar 2026*.
  - **Authors/Institution**: SJTU, Shanghai Innovation Institute, VGG Oxford
  - **Core Contribution**: Unified causal streaming ViT backbone — extends DINOv3 with causal spatiotemporal attention, 3D-RoPE, and KV-cache inference. Frozen backbone generalizes across semantic, 3D reconstruction, VLM, and VLA tasks. Streaming inference reduces complexity from O(T²) to O(T); 15× faster at T=64.
  - **Links**: [[Paper](https://arxiv.org/abs/2603.12265)]

- **FluxMem**: *FluxMem: Adaptive Hierarchical Memory for Streaming Video Understanding*. *CVPR, 2026*.
  - **Authors/Institution**: Yiweng Xie, Bo He, Junke Wang et al. (Fudan University)
  - **Core Contribution**: Adaptive hierarchical memory bank with dynamic retention/eviction policy for training-free token compression in streaming video. Maintains long-term context under constant memory budget via query-guided memory refresh.
  - **Links**: [[Paper](https://arxiv.org/abs/2603.02096)]

- **HERMES**: *HERMES: KV Cache as Hierarchical Memory for Efficient Streaming Video Understanding*. *ACL, 2026*.
  - **Authors/Institution**: Haowei Zhang, Shudong Yang, Jinlan Fu et al. (Fudan University)
  - **Core Contribution**: Training-free hierarchical KV-cache organization for streaming video — short-term, mid-term, and long-term memory tiers with query-aware retrieval. Enables efficient streaming without retraining or architectural changes.
  - **Links**: [[Paper](https://arxiv.org/abs/2601.14724)]

- **VideoScaffold**: *VideoScaffold: Elastic-Scale Visual Hierarchies for Streaming Video Understanding in MLLMs*. *arXiv, Dec 2025*.
  - **Authors/Institution**: Naishan Zheng, Jie Huang, Qingpei Guo, Feng Zhao et al.
  - **Core Contribution**: Dynamic representation framework with Elastic-scale Event Segmentation (EES) and Hierarchical Event Consolidation (HEC). Adaptively adjusts event granularity based on video duration, enabling smooth transition from fine-grained frame understanding to abstract event reasoning in streaming. Plug-and-play for image-based MLLMs.
  - **Links**: [[Paper](https://arxiv.org/abs/2512.22226)] | [[Code](https://github.com/zheng980629/VideoScaffold)]

- **StreamingVLM**: *StreamingVLM: Real-Time Understanding for Infinite Video Streams*. *ICLR, 2026*.
  - **Authors/Institution**: Ruyi Xu, Guangxuan Xiao, Yukang Chen et al. (MIT Han Lab)
  - **Core Contribution**: Unified framework aligning training (overlapped-chunk SFT) with streaming inference (compact KV-cache: attention sinks + rolling vision buffer + rolling text buffer + contiguous RoPE). 8 FPS on H100 for 2h+ videos. 66.18% win rate vs GPT-4o mini on Inf-Streams-Eval; also boosts offline VQA (+4.30 LongVideoBench).
  - **Links**: [[Paper](https://arxiv.org/abs/2510.09608)] | [[Code](https://github.com/mit-han-lab/streaming-vlm)] | [[Demo](https://streamingvlm.hanlab.ai)]

- **InfiniPot-V**: *InfiniPot-V: Memory-Constrained KV Cache Compression for Streaming Video Understanding*. *NeurIPS, 2025*.
  - **Authors/Institution**: Minsoo Kim, Kyuhong Shim, Jungwook Choi, Simyung Chang et al.
  - **Core Contribution**: First training-free, query-agnostic KV-cache compression with hard length-independent memory cap. Temporal-axis Redundancy (TaR) removal + Value-Norm (VaN) ranking. Cuts peak GPU memory by up to 94% across four MLLMs; sustains real-time generation in multi-turn dialogues.
  - **Links**: [[Paper](https://arxiv.org/abs/2506.15745)]

- **StreamBridge**: *StreamBridge: Turning Your Offline Video Large Language Model into a Proactive Streaming Assistant*. *NeurIPS, 2025*.
  - **Authors/Institution**: Haibo Wang, Bo Feng, Zhengfeng Lai et al. (Apple)
  - **Core Contribution**: Transforms offline Video-LLMs into proactive streaming assistants via round-decayed compression memory buffer for long-context multi-turn interaction + lightweight decoupled activation model for continuous proactive responses. Stream-IT dataset. Outperforms GPT-4o and Gemini 1.5 Pro.
  - **Links**: [[Paper](https://arxiv.org/abs/2505.05467)]

- **Flash-VStream**: *Flash-VStream: Efficient Real-Time Understanding for Long Video Streams*. *ICCV, 2025*.
  - **Authors/Institution**: Haoji Zhang, Yiqin Wang, Yansong Tang et al.
  - **Core Contribution**: Flash Memory module with dual-tier design: low-capacity context memory aggregating temporal information + high-capacity augmentation memory retrieving spatial details. SOTA on EgoSchema, MLVU, LVBench, MVBench, Video-MME with significant latency reduction.
  - **Links**: [[Paper](https://arxiv.org/abs/2506.23825)] | [[Code](https://github.com/IVGSZ/Flash-VStream)]

- **Dispider**: *Dispider: Enabling Video LLMs with Active Real-Time Interaction via Disentangled Perception, Decision, and Reaction*. *arXiv, Jan 2025*.
  - **Authors/Institution**: Rui Qian, Shuangrui Ding, Xiaoyi Dong et al. (Show Lab, CUHK)
  - **Core Contribution**: Disentangles streaming video LLM into three async modules — Perception (continuous video monitoring), Decision (optimal interaction moment identification), Reaction (detailed response generation while perception continues). Lightweight proactive streaming module with event-triggered activation.
  - **Links**: [[Paper](https://arxiv.org/abs/2501.03218)] | [[Code](https://github.com/Mark12Ding/Dispider)]

- **VideoLLM-online**: *VideoLLM-online: Online Video Large Language Model for Streaming Video*. *CVPR, 2024*.
  - **Authors/Institution**: Joya Chen, Zhaoyang Lv, Shiwei Wu et al. (Show Lab, NUS; Meta Reality Labs)
  - **Core Contribution**: Pioneering streaming Video LLM with LIVE (Learning-In-Video-Stream) framework: temporally-aligned training objective, offline-to-streaming data synthesis via LLM prompting, and parallelized async inference pipeline. 10+ FPS on A100 for 5-min clips; SOTA on offline benchmarks.
  - **Links**: [[Paper](https://arxiv.org/abs/2406.11816)] | [[Code](https://github.com/showlab/videollm-online)] | [[Project](https://showlab.github.io/videollm-online)]




## B. Proactive Interaction & Continuous Activation

*Agents that monitor streaming environments (e.g., egocentric video) and spontaneously initiate dialogue or actions without explicit user prompts.*

> Papers listed in reverse chronological order.

- **EgoPro-Bench**: *EgoPro-Bench: Benchmarking Personalized Proactive Interaction in Egocentric Video Streams*. *arXiv, May 2026*.
  - **Authors/Institution**: Dongchuan Ran, Linyu Ou, Xueheng Li et al.
  - **Core Contribution**: Large-scale benchmark (2400 eval + 12000 train videos, 12 interaction types) for proactive interaction with simulated user profiles. Introduces "short thinking, better interaction" principle — limited token budget before intent recognition for low-latency HMI.
  - **Links**: [[Paper](https://arxiv.org/abs/2605.07299)]

- **Pro²Assist**: *Pro²Assist: Continuous Step-Aware Proactive Assistance with Multimodal Egocentric Perception for Long-Horizon Procedural Tasks*. *arXiv, May 2026*.
  - **Authors/Institution**: Lilin Xu, Bufang Yang, Siyang Jiang et al. (Columbia University)
  - **Core Contribution**: Step-aware proactive assistant tracking fine-grained task progress via multimodal AR glasses data. Continuous reasoning over multi-scale temporal dynamics and task knowledge. 21% procedural understanding improvement, 2.29× proactive timing accuracy; 90% user-rated useful.
  - **Links**: [[Paper](https://arxiv.org/abs/2605.04227)]

- **Proact-VL**: *Proact-VL: A Proactive VideoLLM for Real-Time AI Companions*. *ICML, 2026*.
  - **Authors/Institution**: Weicai Yan, Yuhong Dai, Qi Ran et al. (Zhejiang University, Shenzhen University, Microsoft Research Asia)
  - **Core Contribution**: General framework shaping multimodal LLMs into proactive real-time AI companions. Jointly models continuous perception, autonomous response triggering, and controllable commentary generation under latency constraints. Built on Qwen2-VL/2.5-VL/3-VL backbones with three interaction modes (solo/co-commentary/guidance).
  - **Links**: [[Paper](https://arxiv.org/abs/2603.03447)] | [[Project](https://proact-vl.github.io/)]

- **ProAgent**: *ProAgent: Harnessing On-Demand Sensory Contexts for Proactive LLM Agent Systems*. *arXiv, Dec 2025*.
  - **Authors/Institution**: (Multiple institutions)
  - **Core Contribution**: Proactive LLM agent with on-demand tiered perception — always-on low-cost sensors (location, motion, audio) trigger high-cost vision capture on demand. Temporal constraint mechanism avoids repeated disturbances via semantic similarity gating.
  - **Links**: [[Paper](https://arxiv.org/abs/2512.06721)]

- **AgileThinker**: *Real-Time Reasoning Agents in Evolving Environments*. *arXiv, Nov 2025*.
  - **Authors/Institution**: Yule Wen, Yixin Ye, Yanzhe Zhang, Diyi Yang, Hao Zhu
  - **Core Contribution**: Formalizes "real-time reasoning" as a new problem class for agents in dynamic environments. Dual-thread architecture: reactive agent (bounded reasoning for fast response) + planning agent (extended reasoning for complex problems). Real-Time Reasoning Gym benchmark.
  - **Links**: [[Paper](https://arxiv.org/abs/2511.04898)]



## C. Streaming VLA & Real-Time Embodied Control

*Models that output continuous action trajectories (VLA) or jointly predict future video and actions with actions as the primary control target (WAM). Emphasizes high-frequency action stream smoothing for robotics, autonomous driving, and game agents.*

> Papers listed in reverse chronological order.

- **The Latent Bridge**: *The Latent Bridge: A Continuous Slow–Fast Channel for Real-Time Game Agents*. *arXiv, Jun 2026*.
  - **Authors/Institution**: Bojie Li, Noah Shi (Pine AI, University of Washington)
  - **Core Contribution**: Couples frozen reasoning VLM (Qwen3-VL-8B-Thinking) with reactive VLM (MiniCPM-o 4.5) via a learned continuous latent bridge that projects slow model residuals into fast model's embedding space — no text round-trip. On 7 Atari games + MetaDrive; Latent Bridge significantly beats Text Bridge (+57% MsPacman, +28% RoadRunner). Code and replay recordings released.
  - **Links**: [[Paper](https://arxiv.org/abs/2606.24470)] | [[Code](https://github.com/19PINE-AI/latent-bridge-games)] | [[Project](https://01.me/research/latent-bridge-games)]

- **CausalDrive**: *CausalDrive: Real-time Causal World Models for Autonomous Driving*. *arXiv, Jun 2026*.
  - **Authors/Institution**: Tianyi Yan, Huan Zheng, Dubing Chen et al.
  - **Core Contribution**: Real-time causal driving WAM at 12 FPS — Context-Forced DMD over causal AR Flow-Matching, strictly avoids future-layout leakage. Enables closed-loop RL post-training via Video2Reward and human-in-the-loop simulation. SocioDrive-Bench for causal driving sociology.
  - **Links**: [[Paper](https://arxiv.org/abs/2606.15341)]

- **GigaWorld-Policy**: *GigaWorld-Policy: An Efficient Action-Centered World–Action Model*. *arXiv, Mar 2026*.
  - **Authors/Institution**: Angen Ye, Boyuan Wang, Chaojun Ni et al. (GigaAI)
  - **Core Contribution**: Action-centered WAM — causal mask prevents future video tokens from influencing action tokens, so inference skips entire video branch (360ms vs Motus 3231ms, 9× faster). Training uses future video as dense physics supervision but deploys action-only. 7% task success gain, 95% improvement over π0.5 on RoboTwin 2.0.
  - **Links**: [[Paper](https://arxiv.org/abs/2603.17240)] | [[Code](https://github.com/open-gigaai/giga-world-policy)] | [[Project](https://gigaai-research.github.io/GigaWorld-Policy/)]

- **StreamingVLA**: *StreamingVLA: Streaming Vision-Language-Action Model with Action Flow Matching and Adaptive Early Observation*. *arXiv, Mar 2026*.
  - **Authors/Institution**: Yiran Shi, Dongqi Guo, Tianchen Zhao et al. (Tsinghua University, Lenovo Research)
  - **Core Contribution**: First systematic asynchronous streaming VLA — eliminates action chunking, adopts action flow matching to overlap generation with execution, and uses saliency-aware adaptive early observation to overlap execution with observation. 2.4× latency speedup, 6.5× reduction in execution halting; maintains LIBERO success rate (94.9% vs 95.1%).
  - **Links**: [[Paper](https://arxiv.org/abs/2603.28565)]

- **DreamZero**: *World Action Models are Zero-shot Policies*. *arXiv, Feb 2026*.
  - **Authors/Institution**: Seonghyeon Ye, Yunhao Ge, Kaiyuan Zheng et al. (NVIDIA)
  - **Core Contribution**: 14B WAM built on Wan2.1-I2V-14B video diffusion backbone — jointly predicts future video and robot actions, enabling real-time closed-loop control at 7Hz (38× acceleration via system/model optimizations). 2×+ improvement in zero-shot generalization vs SOTA VLAs; cross-embodiment transfer with 10–20 min video demos.
  - **Links**: [[Paper](https://arxiv.org/abs/2602.15922)] | [[Project](https://dreamzero0.github.io/)]

- **DynamicVLA**: *DynamicVLA: A Vision-Language-Action Model for Dynamic Object Manipulation*. *arXiv, Jan 2026*.
  - **Authors/Institution**: Haozhe Xie, Beichen Wen, Jiarui Zheng et al. (S-Lab, Nanyang Technological University)
  - **Core Contribution**: 0.4B compact VLA with Continuous Inference (overlaps reasoning and execution to eliminate inter-chunk waiting) and Latent-aware Action Streaming (discards outdated actions, prioritizes most recent predictions for temporal alignment). DOM benchmark: 200K synthetic + 2K real-world dynamic manipulation episodes.
  - **Links**: [[Paper](https://arxiv.org/abs/2601.22153)] | [[Code](https://github.com/hzxie/DynamicVLA)] | [[Project](https://haozhexie.com/project/dynamic-vla)]

- **VLASH**: *VLASH: Real-Time VLAs via Future-State-Aware Asynchronous Inference*. *arXiv, Nov 2025*.
  - **Authors/Institution**: Jiaming Tang, Yufei Sun, Yilong Zhao et al. (MIT; NVIDIA; Tsinghua; UC Berkeley; UCSD; Caltech)
  - **Core Contribution**: General async inference framework for VLAs — estimates future execution-time state by rolling robot state forward with previously generated action chunk, bridging prediction-execution gap. Up to 2.03× speedup, 17.4× reaction latency reduction. First to enable VLA playing ping-pong and whack-a-mole. Works with existing VLAs (π0.5) without architectural changes.
  - **Links**: [[Paper](https://arxiv.org/abs/2512.01031)] | [[Code](https://github.com/mit-han-lab/vlash)]

- **FiS-VLA**: *Fast-in-Slow: A Dual-System Foundation Model Unifying Fast Manipulation within Slow Reasoning*. *arXiv, Jun 2025*.
  - **Authors/Institution**: Hao Chen, Jiaming Liu, Chenyang Gu et al. (CUHK, PKU, OPPO)
  - **Core Contribution**: Dual-system VLA with shared Qwen2-VL backbone — fast path injects into slow path's last K=2 layers for streaming manipulation while maintaining slow reasoning capacity. Diffusion policy action head. Ablation shows K>2 provides diminishing returns.
  - **Links**: [[Paper](https://arxiv.org/abs/2506.01953)] | [[Code](https://github.com/CHEN-H01/Fast-in-Slow)] | [[Project](https://fast-in-slow.github.io/)]



## D. Time-Sensitive Serving & Streaming Backends

*Systems designed for streaming agents: preemptive scheduling, segmented generation, dynamic prioritization, and speculative decoding — supporting time-sensitive LLM/VLA inference.*

> Papers listed in reverse chronological order.

- **Stream2LLM**: *Stream2LLM: Overlap Context Streaming and Prefill for Reduced Time-to-First-Token (TTFT)*. *MLSys, 2026*.
  - **Authors/Institution**: Rajveer Bachkaniwala, Chengqi Luo, Richard So et al. (Divya Mahajan, Kexin Rong — Georgia Tech)
  - **Core Contribution**: Streaming-aware LLM serving for concurrent prefill-decode disaggregated deployments. Adaptive scheduling for append-mode (progressive context accumulation) and update-mode (iterative refinement with cache invalidation). Longest common prefix matching minimizes redundant recomputation. Up to 11× TTFT improvement.
  - **Links**: [[Paper](https://arxiv.org/abs/2604.16395)] | [[Code](https://github.com/rajveerb/stream2llm/tree/mlsys_artifact)]

- **PASCAL**: *PASCAL: A Phase-Aware Scheduling Algorithm for Serving Reasoning-based Large Language Models*. *HPCA, 2026*.
  - **Authors/Institution**: Eunyeong Cho, Jehyeon Bang, Ranggi Hwang, Minsoo Rhu (KAIST)
  - **Core Contribution**: Phase-aware scheduling distinguishing reasoning vs. answering phases. Prioritizes reasoning to reduce TTFT; controlled preemption and token pacing during answering. Dynamic migration at phase boundaries. Up to 72% tail TTFT reduction for DeepSeek-R1 models.
  - **Links**: [[Paper](https://arxiv.org/abs/2602.11530)]

- **TokenFlow**: *TokenFlow: Responsive LLM Text Streaming Serving under Request Burst via Preemptive Scheduling*. *EuroSys, 2026*.
  - **Authors/Institution**: Junyi Chen, Chuheng Du, Renyuan Liu et al.
  - **Core Contribution**: Preemptive request scheduling + proactive KV-cache management for LLM text streaming. Dynamic prioritization based on real-time token buffer occupancy and consumption rate. Background GPU↔CPU KV-cache transfer overlapping I/O with computation. 82.5% effective throughput improvement, 80.2% P99 TTFT reduction.
  - **Links**: [[Paper](https://arxiv.org/abs/2510.02758)]

- **TimelyLLM**: *TimelyLLM: Segmented LLM Serving System for Time-sensitive Robotic Applications*. *arXiv, Dec 2024*.
  - **Authors/Institution**: Neiwen Ling, Guojun Chen, Lin Zhong (Yale University)
  - **Core Contribution**: First time-sensitive LLM serving system for robotic agents. Content-aware segmented generation (detects executable robot skills and pauses/resumes at semantic boundaries). Time Utility Function (TUF)-based scheduling with potential utility density prioritization. 1.97× time utility, 84% waiting time reduction; integrated with vLLM.
  - **Links**: [[Paper](https://arxiv.org/abs/2412.18695)]

- **EAGLE / EAGLE-2**: *EAGLE: Speculative Sampling Requires Rethinking Feature Uncertainty* (+ *EAGLE-2: Faster and Better Speculative Sampling*). *ICML, 2024 / ACL, 2024*.
  - **Authors/Institution**: Yuhui Li, Fangyun Wei, Chao Zhang, Hongyang Zhang (PKU, Microsoft)
  - **Core Contribution**: Self-speculative decoding at feature level — trains draft head on target LLM's second-to-last hidden state for 2–3× acceleration. EAGLE-2 discovers draft softmax confidence ≈ acceptance rate (strong calibration), enabling adaptive draft length without extra training. Foundational infrastructure for VLA streaming acceleration.
  - **Links**: [[Paper (EAGLE)](https://arxiv.org/abs/2401.15077)] | [[Paper (EAGLE-2)](https://arxiv.org/abs/2406.16858)] | [[Code](https://github.com/SafeAILab/EAGLE)]

- **LayerSkip**: *LayerSkip: Enabling Early Exit Inference and Self-Speculative Decoding*. *ACL, 2024*.
  - **Authors/Institution**: Mostafa Elhoushi, Akshat Shrivastava et al. (Meta AI / FAIR)
  - **Core Contribution**: Early exit inference with shared LM head across layers and layer dropout self-distillation. Optimal early exit at ~L/4. Demonstrates self-distillation for efficient inference with ground-truth label supervision. Adaptable to on-policy VLA streaming with distribution-level KL upgrade.
  - **Links**: [[Paper](https://arxiv.org/abs/2404.16710)] | [[Code](https://github.com/facebookresearch/LayerSkip)]


## Benchmarks

Key benchmarks for evaluating streaming agent capabilities:

| Benchmark | Focus | Source |
|:---|:---|:---|
| **Inf-Streams-Eval** | 2h+ video, dense per-second frame-text alignment | [StreamingVLM](https://arxiv.org/abs/2510.09608) (ICLR 2026) |
| **ProReady-QA** | 30–60min video, evidence-window proactive QA (5000 QA, 5 task types) | [StreamReady](https://arxiv.org/abs/2603.08620) (CVPR 2026) |
| **StreamingBench** | Online streaming video QA with continuity / forward splits | [StreamingBench](https://github.com/thunlp-mt/streamingbench) |
| **OVO-Bench** | Online video open-ended QA with Real / Back temporal splits | [OVO-Bench](https://github.com/joeleelyf/ovo-bench) (CVPR 2025) |
| [**VStream-QA**](https://huggingface.co/datasets/IVGSZ/VStream-QA) | Online streaming video question answering | [Flash-VStream](https://arxiv.org/abs/2506.23825) |
| **EgoPro-Bench** | Egocentric proactive interaction (2400 eval + 12000 train, 12 types) | [EgoPro-Bench](https://arxiv.org/abs/2605.07299) (2026) |
| **Stream-IT** | Streaming video understanding with interleaved video-text sequences | [StreamBridge](https://arxiv.org/abs/2505.05467) (2025) |
| **Live Gaming Benchmark** | Real-time game commentary, co-commentary, and guidance | [Proact-VL](https://arxiv.org/abs/2603.03447) (2026) |
| **Real-Time Reasoning Gym** | Dynamic environment agent reasoning under temporal constraints | [AgileThinker](https://arxiv.org/abs/2511.04898) (2025) |
| **DOM (Dynamic Object Manipulation)** | Dynamic object manipulation (200K synthetic + 2K real, multi-embodiment) | [DynamicVLA](https://arxiv.org/abs/2601.22153) (2026) |
| **SocioDrive-Bench** | Causal driving sociology for interactive autonomous driving simulation | [CausalDrive](https://arxiv.org/abs/2606.15341) (2026) |

---

## Contributing

Contributions welcome! Please follow the format and create a pull request:

```markdown
- **ShortName**: *Full Paper Title*. *Venue, Year*.
  - **Authors/Institution**: First Author, Second Author et al. (Institution1, Institution2)
  - **Core Contribution**: 1–2 sentences on how it addresses streaming / time-sensitivity / proactivity / unbounded input, and the underlying model type (LLM / VLM / VLA / WAM).
  - **Links**: [[Paper](url)] | [[Code](url)] | [[Project](url)]
```

**Criteria for inclusion**: The work must explicitly address at least one of: (1) time-sensitive processing, (2) real-time/low-latency response, (3) proactive/continuous activation without explicit prompts, (4) unbounded streaming input processing.
