# Incentivizing Truthful Language Models via Peer Elicitation
Games
Official repository for our NeurIPS 2025 paper: “Incentivizing Truthful Language Models via Peer Elicitation
Games”.

## 🧠 Overview
We introduce Peer Elicitation Games (PEG), a training-free, game-theoretic framework for eliciting truthfull behavior from LLMs.

## 📁 Repository Structure
.
├── initial_policy/ # Notebooks for generating initial LLM policies from various datasets
│ ├── initial_policy_diffModel_ARC.ipynb
│ ├── initial_policy_diffModel_GPQA.ipynb
│ └── initial_policy_diffModel_MMLU.ipynb
│
├── data/ # Includes pre-generated 12 initial policy datasets (3 models × 4 datasets = 12 files)
│ └── arc_policy_df_deepseek_llm_7b.csv
│ └── ...
├── peg_application/ # Notebook implementing the core PEG mechanism
│ └── PEG_mechanism.ipynb


---

## ⚙️ Setup

1. **Clone the repo**
```bash
git clone https://github.com/llm-anon-user/neurips2025-repo.git
cd neurips2025-repo
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```
3. Set your Hugging Face token (for data and model loading)

```bash
export HF_TOKEN=your_huggingface_token
```
 
## 🚀 Usage

### Option A: Use pre-generated initial policy 
If you'd like to skip LLM inference and use the initial policy from our paper:

1. Open and run:
```bash
peg_application/PEG_mechanism.ipynb
```
2. This uses initial policy from Data/ folder and outputs updated policies and evaluation metrics

### Option B: Generate your own initial policy
1. Ensure you have set your HF_TOKEN environment variable.
The notebooks require access to the Hugging Face allenai/ai2_arc and similar datasets.
In the code, we use a placeholder string for the token:
```python
os.environ["HF_TOKEN"] = "hf_***REDACTED***"
```
Before running, replace this with your actual token or set it in your environment:
```python
export HF_TOKEN=your_actual_token
```
Or, in a notebook cell:

```python
from huggingface_hub import login
login("your_actual_token")
```
   
3. Run the following notebooks to generate your own policies:
```bash
initial_policy/initial_policy_diffModel_ARC.ipynb
initial_policy/initial_policy_diffModel_GPQA.ipynb
initial_policy/initial_policy_diffModel_MMLU.ipynb
```
2. This will produce 12 new initial policy datasets, which you can then feed into PEG_mechanism.ipynb.


