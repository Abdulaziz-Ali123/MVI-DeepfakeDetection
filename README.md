# DeepFake Detection in Real-World Communication

A study of DeepFake audio detection using Convolutional Neural Networks (CNNs) trained on MFCC features, evaluated on ASVspoof, Fake or Real (FoR), and a new complementary dataset we built, **DDRCD**.

**Authors:** Abdulaziz Ali, Kemar Wilson, Farrell Joswara
**Affiliation:** Department of Electrical Engineering and Computer Science, University of Kansas
**Support:** KU Institute for Information Science (I2S), Midwest Viceroy Institute (MVI)

📄 **[Read the full paper (PDF)](DeepFake_Detection_in_Real_World_Communication.pdf)**

---

## Overview

DeepFake audio can produce highly realistic but fabricated voice recordings, creating risks for misinformation, fraud, and identity theft. This project reviews current detection approaches and reports our own experiments on detecting fake audio in a real-world setting.

The paper covers:

- Key challenges in DeepFake audio detection
- Current detection techniques (machine learning, signal processing and spectral analysis, cross-modal detection)
- Our experimental methodology and results
- Future directions, including real-time detection systems and cross-industry collaboration

## Challenges

- **Rapid evolution of forgery techniques:** generation methods are advancing faster than detection.
- **Data availability and quality:** high-quality, diverse DeepFake audio datasets remain limited.
- **Ethical implications:** detection tools raise privacy concerns and can be misused for surveillance.

## Datasets

| Dataset | Description |
|---|---|
| **ASVspoof** | Widely used speaker verification spoofing benchmark with genuine and spoofed samples (voice conversion and text-to-speech). |
| **Fake or Real (FoR)** | Recordings from real people alongside synthetic voices, designed to reflect more diverse and challenging real-world conditions. |
| **DDRCD** (DeepFake Detection in Real-World Compliment Dataset) | A dataset created by this team to complement larger datasets. It focuses on more believable DeepFakes and is meant to build on, not replace, ASVspoof and FoR. It also serves as a test of a detection model's efficacy. |

## Methodology

1. **Feature extraction:** Mel-frequency cepstral coefficients (MFCCs) are extracted from each audio sample to represent short-term spectral characteristics.
2. **Normalization:** All audio is normalized to uniform amplitude levels to reduce bias from differing recording conditions across datasets.
3. **Model:** A CNN takes the MFCCs as input and classifies each sample as real or fake. Time constraints limited experiments to CNNs only.
4. **Class imbalance handling:** ASVspoof contains far more spoofed than genuine samples, so we trained two models, one with **under-sampling** (reducing the majority class) and one with **over-sampling** (increasing the minority class).

## Results

Models were evaluated on accuracy, precision, and recall.

### Table I: Model evaluations

| Model | Accuracy | Precision | Recall |
|---|---|---|---|
| Under-sampled | 84.4% | 91.5% | 75.6% |
| Over-sampled | 99.6% | 99.9% | 99.4% |
| FoR | 63.8% | ~94.3% | 29.36% |

### Table II: Model performance on the FoR dataset

| Model | Accuracy | Precision | Recall |
|---|---|---|---|
| Under-sampled | 45.1% | 36% | 9.2% |
| Over-sampled | 59.84% | 63.1% | 51.7% |

### Table III: Model performance on DDRCD

| Model | Accuracy | Precision | Recall |
|---|---|---|---|
| Under-sampled | 27.27% | 15.99% | 12.9% |
| Over-sampled | 18.18% | 18.9% | 22.58% |

**Takeaway:** The over-sampled model performs very well on ASVspoof, but performance drops sharply on FoR and DDRCD. This points to a generalization gap between benchmark data and more realistic, believable DeepFakes.

## Future Work

- Experiment with different model architectures, input sizes, and over/under-sampling techniques
- Build real-time detection systems for high-stakes scenarios such as live broadcasts
- Pursue collaboration across industry, government, and academia through shared standards, research, and open-source tools

## References

1. Y. Patel et al., "Deepfake Generation and Detection: Case Study and Challenges," *IEEE Access*, vol. 11, pp. 143296-143323, 2023. doi: 10.1109/ACCESS.2023.3342107
2. Y. Xie, Y. Lu et al., "CodecFake: Enhancing Anti-Spoofing Models Against Deepfake Audios from Codec-Based Speech Synthesis Systems," 2024.
3. J. Frank and L. Schonherr, "WaveFake: A Data Set to Facilitate Audio Deepfake Detection," *NeurIPS Datasets and Benchmarks Track*, 2021.
4. Y. Li, M. Zhang et al., "Cross-Domain Audio Deepfake Detection: Dataset and Analysis," 2024.
5. Z. Ba, Q. Wen et al., "DEepfake CROss-lingual Evaluation Dataset (DECRO)," 2023.
6. ASVspoof Consortium, "ASVspoof 2019: Automatic Speaker Verification Spoofing and Countermeasures Challenge." https://www.asvspoof.org
7. J. Clement et al., "Fake or Real (FoR) Audio Dataset for Deepfake Detection," 2021.

## Acknowledgments

We thank the KU Institute for Information Science (I2S) and the Midwest Viceroy Institute (MVI) for their support and sponsorship, along with the faculty and staff of the University of Kansas Department of Electrical Engineering and Computer Science, the TRIO McNair Scholars Program, and the Watson Library for their guidance and mentorship.
