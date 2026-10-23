# ICAIC 2026 Learning Plan

7 weeks, 19 Oct to 6 Dec 2026. Chapter numbers refer to the PDFs in `ICAIC Textbooks/`.

## What the contest rewards
- **Dates:** Individual contest **Tue 8 Dec** (3 tasks). Team contest **Thu 10 Dec** (2–3 tasks). Practice session 7 Dec.
- **Length unclear:** the rules say 6 hours, the programme says 9am–12pm. Confirm with sc@icaic.sg.
- **All coding.** Python in JupyterLab, scored by a metric on a hidden test set.
- **10 minutes per evaluation run** on one L4 GPU, training included. Fast models and fine-tuning small pretrained models beat building big models from scratch.
- **No internet, no LLM help, no books or notes.** Training loops, CV splits and agents have to come from memory.

So the plan is about **30% reading, 70% coding from memory.**

## Weekly plan

| Week                | Focus                                 | Read only these                                                                                                                                                                                                             | Drill (no LLM, no copy-paste)                                                                                                                                                                                                                                                                       |
| ------------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **W1** Oct 19–25    | Tabular ML and validation             | **ESL 7.3, 7.10–7.11** (bias-variance, cross-validation, bootstrap) · **Murphy PML1 Ch 18** (trees, forests, boosting) · **PML1 5.1** (decision theory: ROC/PR, thresholds)                                                 | LightGBM/XGBoost/CatBoost with K-fold CV, early stopping, leak-free target encoding, class imbalance, tuning thresholds to the metric                                                                                                                                                               |
| **W2** Oct 26–Nov 1 | Deep learning core                    | **Goodfellow Ch 11** (all) · **Goodfellow 7.1, 7.4, 7.8, 7.12** (regularisation, augmentation, early stopping, dropout) · **Goodfellow 8.3–8.5, 8.7.1** (SGD, Adam, batch norm)                                             | PyTorch training loop from a blank page: Dataset/DataLoader, AMP, learning-rate schedule, checkpointing, a timer to stay under 10 min                                                                                                                                                               |
| **W3** Nov 2–8      | Computer vision and transfer learning | **Bishop Ch 10** (CNNs, detection, segmentation) · **PML1 19.1–19.3, 19.7** (augmentation, transfer, semi-supervised, weak supervision)                                                                                     | Fine-tune a torchvision ResNet or ViT in under 10 min: freeze then unfreeze, albumentations, test-time augmentation, pseudo-labelling · adversarial examples (FGSM, PGD) against a pretrained model                                                                                                 |
| **W4** Nov 9–15     | Transformers, NLP and LLMs            | **Bishop Ch 12** (attention, transformer LMs, multimodal)                                                                                                                                                                   | HF `transformers` fine-tuning, LoRA with `peft`, `sentence-transformers` embeddings with logistic regression or kNN, cosine retrieval, generation settings, parsing structured output                                                                                                               |
| **W5** Nov 16–22    | RL and search agents                  | **Sutton & Barto (2015 draft): Ch 2.1–2.7, Ch 3, 4.3–4.4, 6.1–6.5, 9.1–9.4** · **Sutton & Barto 2020 edition Ch 13** (policy gradients, see below) · **AIMA Ch 3.1–3.6** (BFS, A*) and **Ch 5.1–5.4** (minimax, alpha-beta) | A*, alpha-beta, MCTS (UCT), tabular Q-learning, DQN, REINFORCE, all from scratch                                                                                                                                                                                                                    |
| **W6** Nov 23–29    | Time series, unsupervised, gaps       | **PML1 20.1** (PCA), **21.3** (k-means)                                                                                                                                                                                     | Lag/rolling features with GBDT, time-ordered CV, FFT features, windowed sensor/IMU data, IsolationForest, autoencoder anomaly scores · audio: load `.wav` with `torchaudio`, mel-spectrograms, a small CNN on spectrograms. **Mock 1:** IOAI 2026 Individual tasks 1–3, full-length, timed, offline |
| **W7** Nov 30–Dec 6 | Taper                                 | Nothing new                                                                                                                                                                                                                 | **Mock 2:** IOAI 2026 Individual tasks 4–6, then rewrite every template from memory until it's quick                                                                                                                                                                                                |

## Skip entirely
- **AIMA** Ch 7–12 (logic, planning, knowledge representation), Ch 13–17 (probabilistic reasoning), Ch 18–25
- **ESL** everything except Ch 7
- **Goodfellow** Part III (Ch 13–20)
- **Bishop** Ch 14–20 (generative models)
- **Murphy PML1** Part I (Ch 2–8): look things up only when stuck

## Gaps the books don't cover
1. **Policy gradients.** Our Sutton & Barto PDF is a 2015 draft with no REINFORCE chapter. The final 2nd edition is free from the author: `incompleteideas.net/book/RLbook2020.pdf`. Read **Ch 13**.
2. **LLM, RAG and agents.** Learn hands-on with `transformers`, `peft`, `trl`, `sentence-transformers`.
3. **Time-series forecasting.** Covered by the Week 6 drills.
4. **Audio.** IOAI 2026 had an audio task (reordering dialogue clips). Covered by the Week 6 drill.
5. **Adversarial examples.** IOAI 2026 had a task making two image models disagree. Covered by the Week 3 drill.

## Practice tasks (IOAI past papers)
ICAIC 2026 has no past papers. The organisers point to IOAI tasks instead ([their list](https://github.com/icaic-official/Documents-and-experience-from-other-events-like-IOAI-)), and IOAI uses the same setup: short time limit per run, one GPU, no internet, scored against a baseline and a Scientific Committee reference.

The tasks are cloned locally into `Practice Tasks/` (not pushed to this repo). To get them yourself: `git clone --depth 1 https://github.com/IOAI-official/IOAI-2025.git` (same for `IOAI-2024`, `IOAI-2026`). You need `git-lfs` installed for the datasets.

Do one or two each weekend, offline and without LLM help, then compare against the official solution (2025 has solution notebooks).

| Week | Task | Path in `Practice Tasks/` | Skill |
|---|---|---|---|
| W1 | Lost in Hyperspace | `IOAI-2024/On-Site-Round/Lost_in_Hyperspace` | Feature engineering for a fixed linear-regression model |
| W1 | Antique | `IOAI-2025/Individual-Contest/Antique` | Semi-supervised tabular classification |
| W2 | Chicken Counting | `IOAI-2025/Individual-Contest/Chicken_Counting` | Training a density-estimation decoder on a pretrained feature extractor |
| W3 | Restroom | `IOAI-2025/Individual-Contest/Restroom` | Image matching / metric learning |
| W3 | Pixel | `IOAI-2025/Individual-Contest/Pixel` | Finding the most important pixels for a classifier |
| W3 (optional) | Madarian Cow | `IOAI-2024/On-Site-Round/Madarian_Cow` | Adapting an image-generation model |
| W4 | Help BOBAI | `IOAI-2024/On-Site-Round/Help_BOBAI` | Text classification in an unknown language |
| W4 | Concepts | `IOAI-2025/Individual-Contest/Concepts` | Word-guessing game with a provided LLM |
| W5 | (none fit) | | No past IOAI task is pure RL. Stick to the Week 5 drills. |
| W6 | Radar | `IOAI-2025/Individual-Contest/Radar` | Semantic segmentation on radar signals |
| W6 | Weather | `IOAI-2025/At-Home-Round/Weather` | Satellite weather forecasting |
| W6 Mock 1 | Find the Order, Robot Chasing, Potato | `IOAI-2026/Individual-Contest/1_…`, `2_…`, `3_…` | Audio ordering, imitating agent behaviour, embedding-guided search |
| W7 Mock 2 | Double Agent Dilemma, Ghost of the Machine, IOAI Field | `IOAI-2026/Individual-Contest/4_…`, `5_…`, `6_…` | Adversarial examples, detecting where LLM text starts, fitting a function from scratch |

Spare tasks if you run out: `IOAI-2025/At-Home-Round/Chameleon`, `IOAI-2025/At-Home-Round/Radar`, and the APOAI 2026 / NOAI 2026 sets linked in the organisers' list.

## Templates to have memorised by Week 7
1. Tabular: GBDT with K-fold CV, out-of-fold predictions, submission file
2. PyTorch training loop with AMP, learning-rate schedule and a time limit
3. Fine-tuning a pretrained image model
4. Fine-tuning an HF text classifier, plus an embedding baseline
5. MCTS / alpha-beta agent
6. DQN or REINFORCE
7. Time-series feature builder with time-ordered CV
8. FGSM / PGD adversarial attack
9. Audio to mel-spectrogram to classifier

## Team contest split
- **Person A:** tabular and time series
- **Person B:** CV, NLP and LLMs
- **Person C:** RL and search

Each goes deep on one area and stays competent on the rest.

## Sources
[Contest](https://icaic.sg/contest.php) · [Syllabus](https://icaic-official.github.io/docs/syllabus.html) · [Rules](https://icaic-official.github.io/docs/contest-rules.html) · [Technical appendix](https://icaic-official.github.io/docs/technical-appendix.html) · [Programme](https://icaic.sg/programme.php)
