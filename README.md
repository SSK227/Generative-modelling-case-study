# Building and Understanding GANs: From Synthetic 2D Distributions to Real-World Applications

Coursework submission — Advanced Research Topics in Data Science, Unit 5 (GANs).

This repository contains all code for a two-part GAN assignment: foundational
experiments with synthetic 2D data (Part 1), and three real-world GAN
applications spanning medical imaging, network security, and creative sketch
generation (Part 2).

The full written report (`Report.docx` / PDF) is submitted separately via
the module platform as required by the assignment brief.

## Repository Contents

| File | Description |
|---|---|
| `Part_1_Building_and_Understanding_GANs_.ipynb` | Part 1: sine-wave GAN (tutorial reproduction), 2D spiral GAN, and architecture modification/comparison |
| `Part2_1_OCTMNIST_DCGAN.ipynb` | Part 2.1: DCGAN trained on OCTMNIST retinal scan images (MedMNIST) |
| `2_2_Cybersecurity___Synthetic_Traffic_with_CICIDS_2017.ipynb` | Part 2.2: tabular GAN trained on CICIDS 2017 network traffic data |
| `2_3_Creative_AI___QuickDraw__birthday_cake_.ipynb` | Part 2.3: DCGAN trained on QuickDraw "birthday cake" sketches |
| `Report.docx` | Full written report (7 pages) |
| `requirements.txt` | Python package dependencies |

## How to Run

All notebooks were developed and tested in **Google Colab**. To reproduce results:

1. Open the desired notebook in Google Colab (upload directly, or open from GitHub via Colab's "Open notebook → GitHub" option).
2. Run all cells sequentially from top to bottom (`Runtime → Run all`).
3. **Dataset-specific setup:**
   - **Part 1**: no external data required — synthetic data is generated in-notebook.
   - **Part 2.1 (OCTMNIST)**: dataset downloads automatically via the `medmnist` package on first run (requires internet access).
   - **Part 2.2 (CICIDS 2017)**: requires the CICIDS 2017 CSV files (`Wednesday-workingHours_pcap_ISCX.csv` at minimum for the core GAN; all 8 daily files for the full multi-day exploration section). Available from [Kaggle: Network Intrusion Dataset](https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset/data). Upload the CSV(s) to the Colab session's `/content/` directory before running.
   - **Part 2.3 (QuickDraw)**: dataset downloads automatically from Google's public QuickDraw bucket on first run (requires internet access).
4. A GPU runtime (`Runtime → Change runtime type → GPU`) is recommended for Parts 2.1–2.3 to reduce training time, though all notebooks also run on CPU.
5. Random seeds are fixed (`torch.manual_seed(42)`, and `np.random.seed(42)` where NumPy-based sampling is used) throughout for reproducibility.

## Summary of Results

| Task | Method | Key Result |
|---|---|---|
| Part 1, Task 1 | MLP GAN, sine wave | Reproduces sine curve shape; robust across seeds |
| Part 1, Task 2 | MLP GAN, 2D spiral | Captures outer windings; fails to resolve tightly-wound inner structure |
| Part 1, Task 3 | Deeper/LeakyReLU generator, spiral | Modest overall improvement (NN-distance 0.0107→0.0099); inner-loop failure not resolved |
| Part 2.1 | DCGAN, OCTMNIST | FID = 37.77; captures coarse anatomy and correct structural direction, not full contrast/texture |
| Part 2.2 | Tabular GAN, CICIDS 2017 | TV distance = 0.062, all 8 clusters proportionately represented; no mode collapse |
| Part 2.3 | DCGAN, QuickDraw sketches | FID = 44.71; no mode collapse; line-quality weaker than OCTMNIST texture |

Full methodology, evaluation, and discussion for each task are provided in the accompanying report.

## Reproducibility Note

All notebooks were executed sequentially from a clean runtime state prior to submission, with random seeds fixed, to confirm they run end-to-end without errors and produce results consistent with those reported.

## Author
Shiva krishna (24067206)
MSc Data Science
2026
