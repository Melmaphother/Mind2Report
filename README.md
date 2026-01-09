<div align="center">
  <h1>
        📊 Mind2Report: A Cognitive Deep Research Agent <br> for Expert-Level Commercial Report Synthesis <br>
  </h1>
</div>

<div align="center">
  <a href="https://arxiv.org/abs/2601.04879">
    📖 <strong>Paper</strong>
  </a> |
  <a href="https://huggingface.co/datasets/xxx/Mind2Report-Data">
    📊 <strong>Datasets</strong>
  </a> |
  <a href="https://github.com/Melmaphother/Mind2Report">
    👀 <strong>Code</strong>
  </a>
  <br><br>
  <img src="https://img.shields.io/github/last-commit/Melmaphother/Mind2Report?color=green" alt="Last Commit">
  <img src="https://img.shields.io/github/stars/Melmaphother/Mind2Report?color=yellow" alt="Stars">
  <img src="https://img.shields.io/github/forks/Melmaphother/Mind2Report?color=lightblue" alt="Forks">
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue" alt="License">
</div>

---

## 📖 Abstract

Synthesizing informative commercial reports from massive and noisy web sources is critical for high-stakes business decisions. Although current deep research agents achieve notable progress, their reports still remain limited in terms of quality, reliability, and coverage. In this work, we propose Mind2Report, a cognitive deep research agent that emulates the commercial analyst to synthesize expert-level reports. Specifically, it first probes fine-grained intent, then searches web sources and records distilled information on the fly, and subsequently iteratively synthesizes the report. To rigorously evaluate Mind2Report, we further construct QRC-Eval comprising 200 real-world commercial tasks and establish a holistic evaluation strategy to assess report quality, reliability, and coverage.

This repository contains the official code for our [paper](https://arxiv.org/abs/2601.04879):
> Mind2Report: A Cognitive Deep Research Agent for Expert-Level Commercial Report Synthesis

<details>
<summary><b>Full Abstract</b></summary>

Synthesizing informative commercial reports from massive and noisy web sources is critical for high-stakes business decisions. Although current deep research agents achieve notable progress, their reports still remain limited in terms of quality, reliability, and coverage. In this work, we propose Mind2Report, a cognitive deep research agent that emulates the commercial analyst to synthesize expert-level reports. Specifically, it first probes fine-grained intent, then searches web sources and records distilled information on the fly, and subsequently iteratively synthesizes the report. We design Mind2Report as a training-free agentic workflow that augments general large language models (LLMs) with dynamic memory to support these long-form cognitive processes. To rigorously evaluate Mind2Report, we further construct QRC-Eval comprising 200 real-world commercial tasks and establish a holistic evaluation strategy to assess report quality, reliability, and coverage. Experiments demonstrate that Mind2Report outperforms leading baselines, including OpenAI and Gemini deep research agents. Although this is a preliminary study, we expect it to serve as a foundation for advancing the future design of commercial deep research agents. 

</details>

## 🎁 Updates/News:

🚩 **News** (Jan. 2026): Mind2Report initialized and open-sourced.


## ✨ Motivation

<img src="assets/motivation.png" align="left" width="55%"/>

**Mind2Report** simulates how a **Commercial Analyst** performs cognitive deep research—both follow similar patterns:
- 🎯 Intent clarification & fine-grained probing
- 📝 Note-taking & memory recording  
- 🔄 Iterative report synthesis

The challenge lies in navigating the **Massive and Noisy Web** filled with AI-generated content, advertisements, fake news, and scattered information.

Mind2Report transforms this chaotic landscape into **Expert-level Commercial Reports** that are ⭐ High-quality, ✅ Reliable, 🔍 Comprehensive, and 🎯 Decision-ready.

<br clear="left"/>


## 🌟 Framework

<div align="center">
<img src="assets/framework.png" width="95%"/>
<p><em>Figure 2: the proposed Mind2Report.</em></p>
</div>

The figure illustrates the comprehensive pipeline of the **Mind2Report** framework, consisting of three core modules:

- **Intent-Driven Outline Formulation** — On the left, the system begins with intent clarification to understand user queries, followed by outline search to gather domain knowledge. It then generates a structured chapter tree with both broad summaries (e.g., "H100 market, AI infra. 2025") and concrete thinking directions (e.g., "Llama training, BF16 TFLOPs").

- **Memory-Augmented Adaptive Search** — In the center, the core research loop operates recursively. The system performs information distilling from web sources, with a fail-retry mechanism for query expanding when needed. Successfully extracted knowledge is recorded into a knowledge-enriched chapter tree with dynamic memory. The coherent-preserved iterative synthesis phase includes knowledge merging, iterative synthesis, and reference matching.

- **Multi-dimensional Reflection** — The system evaluates research quality across four dimensions: search steps efficiency, integrity of information, freshness of sources, and plurality of perspectives. This reflection mechanism ensures the final commercial report meets expert-level standards with proper citations and structured content.


## 🚀 Quick Start

This guide provides step-by-step instructions to set up the environment, configure APIs, and run Mind2Report.

### 1. Environment Setup

We recommend using Conda to manage dependencies. Ensure you have Python 3.10+ installed.

```bash
# Clone the Mind2Report repository from GitHub.
git clone https://github.com/Melmaphother/Mind2Report.git

# Navigate into the cloned repository directory.
cd Mind2Report

# Create a new conda environment.
conda create -n mind2report python=3.10

# Activate the environment.
conda activate mind2report

# Install all dependencies.
pip install -r requirements.txt
```

### 2. Configuration

Mind2Report requires configuration for LLM APIs and search tools. Edit the configuration files in `src/config/`:

**LLM Configuration** (`src/config/llms.toml`):
```toml
[planner]
api_base = "your-api-base"
api_key = "your-api-key"
model = "Deepseek-R1"  # Recommended: reasoning LLM

[basic]
api_base = "your-api-base"
api_key = "your-api-key"
model = "DeepSeek-V3.1"
```

**Search Configuration** (`src/config/search.toml`):
```toml
[search]
jina_api_key = "your-jina-api-key"  # Get from https://jina.ai/
# or
tavily_api_key = "your-tavily-api-key"  # Get from https://tavily.com/
```

### 3. Run Mind2Report

Start the interactive deep research agent:

```bash
python -m src.run
```

The system will guide you through:
1. Enter your research query
2. (Optional) Answer clarifying questions for better results
3. Wait for the agent to perform deep research
4. Receive your comprehensive report in Markdown and HTML formats


## 💪 Performance

<div align="center">
<img src="assets/performance.png" width="100%"/>
<p><em>Table 1: Performance Comparison on FirmBench Benchmark</em></p>
</div>

We evaluate Mind2Report against baselines across three dimensions: **Quality** (relevance and structure), **Reliability** (hallucination, temporality, consistency), and **Coverage** (breadth and depth). The table compares Mind2Report with:

- **Proprietary DRAs**: o3 Deep Research, o4-mini Deep Research, Gemini Deep Research, Grok Deep Search, Perplexity Deep Research
- **Open-source Training-based DRAs**: WebThinker, MiroThinker, Tongyi-DeepResearch  
- **Open-source Workflow-based DRAs**: MiroFlow, OpenManus, OWL

Mind2Report achieves **Rank 1.00** (best average rank), with **75.42%** relevance, **85.24%** structure score, and only **6.12%** hallucination rate—significantly outperforming all baselines including commercial systems like o3 and Gemini Deep Research.


## 📋 Example Output

<div align="center">
<img src="assets/example.png" width="100%"/>
<p><em>Figure 3: Example of Generated Commercial Report</em></p>
</div>

The figure shows a sample commercial report generated by Mind2Report on the topic **"NVIDIA H100 vs. AMD MI300X: Comparative Analysis for Large-Scale Foundational Model Training in 2025"**. The report features:

- 📋 **Structured Sections**: Organized chapters including Industry Overview, Market Landscape, Leading Players Analysis, and Strategic Implementation Guidance
- 📊 **Data Tables**: SWOT analysis comparing strengths, weaknesses, opportunities, and threats of both platforms
- 📈 **Visualizations**: Charts comparing real-world computational efficiency (FP8/BF16 TFLOPs) and memory architecture
- 🔗 **Proper Citations**: All claims are backed by numbered references with source URLs
- 📄 **Decision-Ready Content**: Actionable insights for infrastructure decision-makers


## 🙏 Acknowledgement

This repo is built on pioneer works. We appreciate the following GitHub repos and resources:

- [LangGraph](https://github.com/langchain-ai/langgraph) - State machine framework for LLM applications

- [Jina AI](https://jina.ai/) - Web reading and search APIs

- [Tavily](https://tavily.com/) - AI-powered search API


## 🔖 Citation

>🙋 Please let us know if you find out a mistake or have any suggestions!
>
>🌟 If you find our work helpful, please consider to star this repository and cite our research.

```bibtex
@misc{cheng2026mind2report,
      title={Mind2Report: A Cognitive Deep Research Agent for Expert-Level Commercial Report Synthesis}, 
      author={Mingyue Cheng and Daoyu Wang and Qi Liu and Shuo Yu and Xiaoyu Tao and Yuqian Wang and Chengzhong Chu and Yu Duan and Mingkang Long and Enhong Chen},
      year={2026},
      eprint={2601.04879},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2601.04879}, 
}
```
