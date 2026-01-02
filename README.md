# DeepResearch

**A lightweight deep research framework based on progressive search and cross-evaluation.**

# Introduction

DeepResearch focuses on solving complex information analysis problems and supports local deployment for individual developers. Through modular context assembly (covering knowledge bases, tool descriptions, and interaction history) and progressive search optimization, it builds an intelligent research workflow of "Task Planning → Tool Calling → Evaluation & Iteration". This workflow effectively alleviates the issues of attention dispersion and information loss when large models process long contexts. Meanwhile, it allows users to introduce custom research workflows, ensuring the output content has thematic focus, comprehensive argumentation, and logical hierarchy.

**Features:**
- Delivers high-quality results without requiring model customization.
- Enables collaboration between small and large models to boost research efficiency and control usage costs.
- Reduces large model hallucinations through knowledge extraction and cross-evaluation verification.
- Supports lightweight deployment and flexible configuration.

## Quick Start
This section will explain how to configure the local runtime environment for DeepResearch.
### 1. Environment Setup
- Recommended Python version: **3.10.0** (using other versions may cause dependency issues).
- Clone the repository.
   ```bash
   git clone <repository-url> 
   ```
- Ensure you have Poetry installed(Recommended version:2.2.1).
   ```bash
   poetry --version
   # If Poetry is not installed yet, you can try installing it via the following methods
   # Install Poetry on Bash
   curl -sSL https://install.python-poetry.org | python3 -
   # Install Poetry on PowerShell
   (Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -
   ```
- Set up your runtime environment
   ```bash
   cd DeepResearch
   poetry install
   poetry env activate
   ```

### 2. Environment Configuration
 According to DeepResearch's workflow, you need to fill in LLM configuration parameters for each module (for the `Planner`, it is recommended to use a reasoning LLM, such as `DeepSeek-R1`). 

Edit `config/llms.toml` and `config/search.toml` files provide your actual API keys and configuration values: 

- **api_base/api_key/model**: OpenAI-compatible API from various platforms.

- **jina_api_key** or **tavily_api_key**: Get your key from [Jina](https://jina.ai/) or [Tavily](https://www.tavily.com/) for web page reading.

### 3. Running DeepResearch
Enjoy the moment.
   ```bash
   poetry run python -m src.run
   ```
## Support

- Community Discussion: GitHub Discussions
- Bug Reports: GitHub Issues

## License

This project is licensed under the [Apache 2.0 License](LICENSE).
