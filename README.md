# Sleep Arousal Detection with Convolutional Neural Networks

**Reproduction of the DeepSleep CNN for detecting sleep arousals from overnight sleep recordings.**

Stanford GENE 222 / CS 273C

## Highlights

- Reproduced Li and Guan's DeepSleep study, including arousal patterns across subjects (mean 30.3 events, range 1 to 91)
- Built a preprocessing pipeline that normalizes and windows 13 signal channels from PhysioNet sleep recordings
- Scaled a cloud pipeline on Google Cloud Batch with 98.7% weak scaling efficiency at about $0.044 per participant

## Built with

Python · NumPy · SciPy · Matplotlib · Google Cloud Batch · Jupyter

---

## What it does

- **Preprocessing pipeline:** loads `.mat`/`.hea`/`.arousal` files from PhysioNet, applies quantile normalization, excludes unlabeled regions, and extracts 30-second signal windows across 13 channels
- **Reproduced figures:** Figure 2 (arousal heterogeneity scatter across subjects, mean 30.3 events, range 1 to 91) and Figure 6b (30-second PSG visualization with arousal shading)
- **Scalability testing:** GATK HaplotypeCaller on Google Cloud Batch at N = 1, 2, 4, 8, 16 participants; 98.7% weak scaling efficiency; ~$0.044/participant
- **LLM-assisted analysis:** structured notebook using `sdo_llm_magic` for guided reasoning at each pipeline stage

## Architecture

| Layer | Stack |
|---|---|
| Signal processing | Python, SciPy, NumPy |
| Scalability pipeline | Google Cloud Batch, GATK |
| Analysis notebook | Jupyter, sdo_llm_magic |
| Visualization | Matplotlib |

## Data

Data comes from the [2018 PhysioNet Challenge](https://physionet.org/physiobank/database/challenge/2018/) and the [Sleep Heart Health Study](https://sleepdata.org/datasets/shhs). Both are publicly available and de-identified. Credentialed accounts on PhysioNet and NSRR are required for access.

## Paper

Li, H., Guan, Y. DeepSleep convolutional neural network allows accurate and fast detection of sleep arousal. *Commun Biol* 4, 18 (2021). https://doi.org/10.1038/s42003-020-01542-8
