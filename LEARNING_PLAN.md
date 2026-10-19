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

| Week | Focus | Read only these | Drill (no LLM, no copy-paste) |
|---|---|---|---|
| **W1** Oct 19–25 | Tabular ML and validation | **ESL 7.3, 7.10–7.11** (bias-variance, cross-validation, bootstrap) · **Murphy PML1 Ch 18** (trees, forests, boosting) · **PML1 5.1** (decision theory: ROC/PR, thresholds) | LightGBM/XGBoost/CatBoost with K-fold CV, early stopping, leak-free target encoding, class imbalance, tuning thresholds to the metric |
| **W2** Oct 26–Nov 1 | Deep learning core | **Goodfellow Ch 11** (all) · **Goodfellow 7.1, 7.4, 7.8, 7.12** (regularisation, augmentation, early stopping, dropout) · **Goodfellow 8.3–8.5, 8.7.1** (SGD, Adam, batch norm) | PyTorch training loop from a blank page: Dataset/DataLoader, AMP, learning-rate schedule, checkpointing, a timer to stay under 10 min |
| **W3** Nov 2–8 | Computer vision and transfer learning | **Bishop Ch 10** (CNNs, detection, segmentation) · **PML1 19.1–19.3, 19.7** (augmentation, transfer, semi-supervised, weak supervision) | Fine-tune a torchvision ResNet or ViT in under 10 min: freeze then unfreeze, albumentations, test-time augmentation, pseudo-labelling |
| **W4** Nov 9–15 | Transformers, NLP and LLMs | **Bishop Ch 12** (attention, transformer LMs, multimodal) | HF `transformers` fine-tuning, LoRA with `peft`, `sentence-transformers` embeddings with logistic regression or kNN, cosine retrieval, generation settings, parsing structured output |
| **W5** Nov 16–22 | RL and search agents | **Sutton & Barto (2015 draft): Ch 2.1–2.7, Ch 3, 4.3–4.4, 6.1–6.5, 9.1–9.4** · **Sutton & Barto 2020 edition Ch 13** (policy gradients, see below) · **AIMA Ch 3.1–3.6** (BFS, A*) and **Ch 5.1–5.4** (minimax, alpha-beta) | A*, alpha-beta, MCTS (UCT), tabular Q-learning, DQN, REINFORCE, all from scratch |
| **W6** Nov 23–29 | Time series, unsupervised, gaps | **PML1 20.1** (PCA), **21.3** (k-means) | Lag/rolling features with GBDT, time-ordered CV, FFT features, windowed sensor/IMU data, IsolationForest, autoencoder anomaly scores. **Mock 1:** full-length, timed, offline |
| **W7** Nov 30–Dec 6 | Taper | Nothing new | **Mock 2**, then rewrite every template from memory until it's quick |

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

## Templates to have memorised by Week 7
1. Tabular: GBDT with K-fold CV, out-of-fold predictions, submission file
2. PyTorch training loop with AMP, learning-rate schedule and a time limit
3. Fine-tuning a pretrained image model
4. Fine-tuning an HF text classifier, plus an embedding baseline
5. MCTS / alpha-beta agent
6. DQN or REINFORCE
7. Time-series feature builder with time-ordered CV

## Team contest split
- **Person A:** tabular and time series
- **Person B:** CV, NLP and LLMs
- **Person C:** RL and search

Each goes deep on one area and stays competent on the rest.

## Sources
[Contest](https://icaic.sg/contest.php) · [Syllabus](https://icaic-official.github.io/docs/syllabus.html) · [Rules](https://icaic-official.github.io/docs/contest-rules.html) · [Technical appendix](https://icaic-official.github.io/docs/technical-appendix.html) · [Programme](https://icaic.sg/programme.php)
