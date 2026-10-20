# Social Media Analytics and Sentiment Analysis

Course materials for **Social Media Analytics and Sentiment Analysis** — Prof. Dr. Mehrdad Jalali, SRH University of Applied Sciences Heidelberg.

A six-chapter path from social media posts to trustworthy insight: text and sentiment, transformers and LLMs, social networks, information diffusion, network visualisation with Gephi, and a responsible end-to-end group project.

## Interactive study guides

Open these in your browser. Each page explains the chapter's concepts with examples, interactive exercises (live VADER, TF-IDF calculator, network and diffusion simulators, a mini-Gephi playground, proposal canvas …), links to real tools and a self-check quiz.

| Chapter | Topic | Open |
|---|---|---|
| 1 | Foundations & Introduction | [Open page](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter1_Foundations.html) |
| 2 | Preprocessing & Classical Sentiment | [Open page](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter2_Preprocessing_Classical_Sentiment.html) |
| 3 | Transformers & LLMs: Sentiment, Emotion & Stance | [Open page](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter3_Transformers_LLMs.html) |
| 4 | Social Network Analytics I — Influence, Communities & Homophily | [Open page](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter4_Networks_Influence_Communities.html) |
| 5 | Social Network Analytics II — Information Diffusion | [Open page](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter5_Information_Diffusion.html) |
| 6 | Gephi Workshop & Project Kick-off | [Open page](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter6_Gephi_Project.html) |

All six: <https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/>

Offline: download the `.html` files from the [`interactive/`](interactive/) folder and open them in any browser — every page is self-contained.

## Labs (Jupyter notebooks)

| Lab | Notebook | What you do |
|---|---|---|
| 1.1 | [`Lab1.1_Profile.ipynb`](notebooks/Lab1.1_Profile.ipynb) | Profile `ev_posts.csv` before any modelling: missing values, duplicates, time range, labels, engagement |
| 2.1 | [`Lab2.1_Baseline.ipynb`](notebooks/Lab2.1_Baseline.ipynb) | Auditable preprocessing, VADER vs. TF-IDF + Logistic Regression, leakage-safe split, error analysis |
| 3.1 | [`Lab3.1_Transformers.ipynb`](notebooks/Lab3.1_Transformers.ipynb) | Pretrained sentiment/emotion models, zero-shot stance, fine-tuning (Colab GPU), failure audit |
| 4.1 | [`Lab4.1_Networks.ipynb`](notebooks/Lab4.1_Networks.ipynb) | Centralities, Louvain communities, assortativity — karate club, then the EV mention network |
| 5.1 | [`Lab5.1_Diffusion.ipynb`](notebooks/Lab5.1_Diffusion.ipynb) | Cascade metrics from parent IDs, Independent Cascade / Linear Threshold, seed strategies |
| 6.1 | [`Lab6.1_Gephi.ipynb`](notebooks/Lab6.1_Gephi.ipynb) | Prepare GEXF files, then in **Gephi**: statistics vs. Chapter 4, colour/size/filters, Timeline replay of two cascades, one captioned SVG figure |

Each lab has a walkthrough, **three challenges** and a reflection. Labs build on each other: Lab 2.1 writes `outputs/posts_ch2.parquet`, which Lab 3.1 reads; Lab 4.1 exports the networks as GEXF; Lab 6.1 prepares the Gephi files from the Lab 4.1 and 5.1 data. Labs 1, 2, 4, 5 and 6 are stored with their outputs; Lab 3.1 downloads models from Hugging Face on first run and is stored without outputs.

## Data

All files are **synthetic teaching data** (seed 42) — no real users.

| File | Content |
|---|---|
| `data/ev_posts.csv` | 2,400 posts about electric vehicles (1–14 March 2026): text, language, sentiment label, likes, replies, `reply_to`, `user_location` |
| `data/ev_mentions.csv` | directed, weighted mention network (260 pseudonymised users, 1,208 edges) with the sentiment of the mentions |
| `data/ev_users.csv` | user attributes for homophily: language and group |
| `data/ev_cascades.csv` | 8 repost/reply cascades with `parent_id`, UTC timestamps, type and sentiment |
| `data/gephi/*.gexf` | ready-to-open Gephi files from Lab 6.1: `karate_ch6`, `karate_cascade` (dynamic), `ev_mentions_ch6`, `ev_cascade_c01` and `ev_cascade_c05` (dynamic) |

`ev_posts.csv` is template-generated, so classifiers can score unrealistically high on it — Lab 2.1 discusses why that is a warning sign.

## Gephi (Chapter 6)

Download the desktop version from [gephi.org](https://gephi.org/users/download/) (0.10.1; Java is included in the installer). No installation possible: [Gephi Lite](https://gephi.org/lite/) runs in the browser, but has no Timeline and no SVG/PDF export. Open the files in `data/gephi/` with **File → Open**.

## Installation

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter lab
```

Windows PowerShell activation: `.venv\Scripts\Activate.ps1`. Open the labs in numerical order from the `notebooks/` folder.

## Group project

The examination project (50% of the grade) answers one real question about public social media data — end to end, responsibly, as a group of 3–5. It must contain a data profile and GDPR check, documented preprocessing and a classical baseline, and at least one network or diffusion analysis; projects with a network include a Gephi figure with legend, caption and matching numbers; a transformer/LLM model is optional. Use the proposal canvas and storyboard tools in the [Chapter 6 guide](https://mehrdadjalali-ai.github.io/SocialMediaAnayltics/interactive/Chapter6_Gephi_Project.html). Deadlines and assessment criteria are on Moodle; submit only via Moodle.

## Troubleshooting

- **Data not found:** start Jupyter from the repository root or from `notebooks/`.
- **`posts_ch2.parquet` missing:** run Lab 2.1 before Lab 3.1.
- **Model download fails:** check internet access; use Colab if the lab machine blocks Hugging Face.
- **Different results:** confirm seed 42 and the package versions in `requirements.txt`.
- **Gephi numbers differ from Python:** check the settings — Normalize (betweenness), Use edge weight (PageRank), Use weights (Modularity); see the switchboard in the Chapter 6 guide.
