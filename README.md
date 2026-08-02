# Social Media Analytics and Sentiment Analysis

An MSc-level, notebook-first course combining text, sentiment, networks, diffusion, and responsible research practice. The four CSV files are **synthetic teaching data** generated with seed 42 and contain no real private users.

## Seven chapters

| # | Notebook | Focus |
|---|---|---|
| 1 | `01_Foundations_and_Introduction.ipynb` | Concepts, ethics, orientation |
| 2 | `02_Text_Preprocessing_in_Social_Media.ipynb` | Transparent text cleaning |
| 3 | `03_Lexicon_and_Classical_ML_Sentiment_Analysis.ipynb` | VADER, TF–IDF, classifiers |
| 4 | `04_Transformer_Based_Sentiment_Emotion_and_Stance.ipynb` | Transformer inference and stance |
| 5 | `05_Social_Network_Analytics_Influence_Communities_and_Homophily.ipynb` | Networks and communities |
| 6 | `06_Information_Diffusion.ipynb` | Cascades and simulations |
| 7 | `07_Advanced_Topics_and_Applications.ipynb` | Integrated mini-project |

Each chapter moves from plain-language concepts through small executable steps, interpretation, exactly three challenges, a summary, and a group-project connection.

## Structure

- `notebooks/`: the seven executed course notebooks
- `data/`: synthetic posts, users, edges, and diffusion events
- `requirements.txt`: compatible Python dependencies

## Installation

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter lab
```

Windows PowerShell activation: `.venv\Scripts\Activate.ps1`. Windows Command Prompt: `.venv\Scripts\activate.bat`. Open notebooks in numerical order. Chapter 4 may download a small public Hugging Face model on first execution; no API key is needed, and an offline teaching fallback is included.

Execute all notebooks from the repository root:

```bash
for notebook in notebooks/*.ipynb; do python -m nbconvert --to notebook --execute --inplace "$notebook" --ExecutePreprocessor.timeout=600; done
```

## Challenges and group project

Complete the three challenges after each walkthrough without looking for a ready-made solution. Record assumptions, outputs, interpretation, and limitations. The sequence builds toward a group project that combines a measurable question, transparent methods, evaluation, visualization, and ethical risk assessment.

## Troubleshooting

- **Data not found:** launch Jupyter from the repository root or `notebooks/`.
- **Kernel missing:** run `python -m ipykernel install --user --name social-media-analytics`.
- **Model download fails:** check internet access; Chapter 4 prints a fallback notice and still demonstrates output structure.
- **Slow execution:** use CPU and the included small samples; do not enlarge transformer batches initially.
- **Different results:** confirm seed 42 and package versions from `requirements.txt`.
