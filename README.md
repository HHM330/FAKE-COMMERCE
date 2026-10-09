# FAKE‑COMMERCE Dataset
> FAKE-COMMERCE: A Challenge Dataset for Deepfake Detection in Commercial Endorsement Videos

![FAKE-COMMERCE](https://github.com/HHM330/FAKE-COMMERCE/blob/main/FAKE-COMMERCE.png?raw=true)

## Dataset Description
Although widely used, existing benchmarks such as FaceForensics++ , Celeb-DF, and Wilddeepfake are not designed for commercial endorsement scenarios. They predominantly feature frontal, unoccluded faces from cinematic or interview sources, and lack challenges caused by product interaction from Key Opinion Leader (KOL) advertisements. To fill this gap, we constructed a deepfake dataset specifically tailored to commercial advertising video scenarios (FAKE-COMMERCE, FCD), thereby addressing a critical data gap in the current deepfake detection research focused on digital marketing content.

## 📌 Introduction
FAKE‑COMMERCE is a real‑world advertising deepfake benchmark built for KOL short‑video advertisement scenarios.

- Covers 23 real‑world product categories from short‑video advertising
- Contains manually annotated naturally‑occurring purpose‑driven occlusions: 312 annotated natural‑occlusion clips (31.2% of total samples)
- Occlusion annotations: occlusion type (limb / product / static_sticker / dynamic_sticker), occlusion severity (light / moderate / severe), and real‑world occlusion screenshot. See Sheet2 of map.xlsx
- Forgery types: full‑face and audio forgery, partial‑face and audio forgery, audio‑only forgery
- Total clips: 1000 real advertisement videos, 3000 manipulated deepfake clips (average 10‑second cropped version)
![occlusion_show](https://github.com/HHM330/FAKE-COMMERCE/blob/main/occlusion_show.png?raw=true)

## 📊 Dataset Statistics
- Total original real advertisement clips: 1000
- Manipulated deepfake clips: 3000
- Annotated natural‑occlusion clips: 312 (31.2% of original real samples)
  - Occlusion‑type distribution of natural‑occlusion samples:
    - limb_occlusion: 46%
    - product_occlusion: 35%
    - dynamic_sticker:13%
    - static_sticker:6%
  - Occlusion‑severity distribution:
    - light:35%
    - moderate:50%
    - severe:15%
- Number of product categories: 23

## 🔧 Data Collection & Processing
### Data Collection
- Source: Public short-video advertisements from bilibili (Chinese platform)
- Collection period: July 2024 – January 2025
- Raw corpus: 4,510 videos containing product recommendation links (crawled under fair-use academic policy)
- After manual screening: 1,000 videos with clear advertising content and front-facing faces during promotional segments
- Product categories: 23 categories (e.g., Electronics & Digital 25.3%, Cosmetics & Personal Care 18.4%, Household Appliances 14.1%, etc.)
- Face-swap source: **SCUT-FBP5500 v2 dataset** — diverse faces selected for identity transfer
- Ethics & Copyright: All videos publicly accessible; used strictly for non-commercial academic research; copyright retained by original creators; content removal requests accepted (see Contact). Data use complies with academic fair-use principles.

### Forgery Generation
- Audio-only manipulation: 1,000 clips via voice conversion
- Audio-visual joint forgery: 2,000 clips with synchronized audio + facial forgery
- Audio Deepfake Generation: Unlike prior datasets (e.g., ASVspoof, WaveFake) that rely on open-source TTS/VC systems, our audio forgery set simulates democratized deepfake creation​ by using Jianying (CapCut)—a consumer-grade application with millions of users. Its voice cloning and AI dubbing features are powered by proprietary lightweight voice conversion and neural vocoder pipelines, conceptually similar to SV2TTS​ or VITS​ but optimized for mobile deployment. By including such samples, FAKE-COMMERCE bridges the gap between controlled lab-generated fakes and real-world manipulated audio encountered in social media, where attackers often exploit accessible tools rather than building custom models.
- Face Deepfake Generation: Face forgeries are produced with the Roop pipeline backed by InsightFace (Buffalo L) for detection/alignment. Three identity-transfer backends are used: inswapper-128 (real-time), SimSwap-512 (high-fidelity GAN), and GhostFace-v14 (diffusion-based). A binary mask mechanism switches between full-face and partial-face replacement, while GFPGAN-v1.4 is applied afterward to enhance facial details and reduce visible manipulation artifacts.


### Preprocessing
- Synthetic occlusion augmentation (training only):
  - Limb occlusion: hand texture images from **11k hands dataset**, diverse poses/genders
  - Product/sticker occlusion: BGR color range sampling
  - Temporal consistency: same texture + fixed scale/rotation + minor pixel offsets within each clip
  - **Disabled** for validation and test sets

### Occlusion Overview
We define two forms of occlusion in this dataset:
1. Natural purpose‑driven occlusion: Real occlusions naturally appearing in original advertising footage, manually labelled by three annotators with senior‑reviewer consistency calibration. We select 202 moderate‑to‑severe natural‑occlusion clips to construct a dedicated natural‑occlusion test set.
2. Synthetic purpose‑driven occlusion: Offline augmentation used for model training only. Occlusion assets (limb / product / static_sticker / dynamic_sticker) are applied according to product‑category dominant‑occlusion mapping rules. Synthetic occlusion augmentation is disabled for validation & test partitions.

## 📂 Dataset Structure

```text

data/
├── all/
│   ├── train/
│   │   ├── real/
│   │   └── fake/
│   ├── val/
│   │   ├── real/
│   │   └── fake/
│   └── test/
│       ├── real/
│       └── fake/
├── part/
│   └── ...
├── audio/
│   └── ...
├── map.xlsx
└── README.md

```

## 📥 How to obtain raw video files
> ⚠️ Important: The original advertising videos are collected from public short‑video platform under academic fair‑use. 
To obtain raw video clips for non‑commercial academic research:
1. Ensure your purpose is non‑commercial academic research only.
2. Send an email to corresponding author: 202410192491@mail.scut.eud.cn
    - Subject: Request FAKE‑COMMERCE Dataset — [Your Name / Institute / Project]
    - Body content:
      - Your full name, affiliation, research group
      - Brief research project description (≤150 words)
      - Confirm you will only use for academic non‑commercial research, will not redistribute, repost, or reshare raw dataset to third parties.
3. After verification, we will send download link / access instructions.

## 📄 Privacy Statement
To ensure the privacy of individuals featured in the dataset, we have implemented the following measures:
Applicant Verification: Access is granted only after verifying the applicant's academic email address, personal electronic signature, and other necessary credentials.
Usage Agreement: Applicants are required to sign a comprehensive agreement to ensure the dataset is used exclusively for research purposes.
Right to Removal: If any part of the dataset impacts you, please contact us to request its removal.

## 📝 Citation
If you use FAKE‑COMMERCE dataset in your work, please cite our paper:
```bibtex
@article{2026fakecommerce,
  title={Are the Advertisements You Watch Authentic? Deepfake Detection in Key Opinion Leader Short‑Video Advertisements with Purpose‑Driven Occlusion},
  author={Heyong Wang, Hongman He, Ming Hong, Haotian Sheng, Junqiu Liu},
  journal={###},
  year={2026}
}

We are committed to safeguarding privacy while enabling research advancements.


