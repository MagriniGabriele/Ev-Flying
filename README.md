# EV-Flying: an Event-based Dataset for In-The-Wild Recognition of Flying Objects


[![arXiv](https://img.shields.io/badge/arXiv-2506.05163-b31b1b.svg)](https://arxiv.org/abs/2506.04048)
[![paper](https://img.shields.io/badge/paper-ACMMM2025-blue.svg)](https://openaccess.thecvf.com/content/CVPR2025W/EventVision/papers/Magrini_EV-Flying_an_Event-based_Dataset_for_In-The-Wild_Recognition_of_Flying_Objects_CVPRW_2025_paper.pdf)
[![huggingface](https://img.shields.io/badge/dataset-Huggingface-yellow.svg)](https://huggingface.co/datasets/GabrieleMagrini/Ev-Flying/)
[![survey](https://img.shields.io/badge/DroneDetectionSurvey-CVPRw2025-brightgreen.svg)](https://openaccess.thecvf.com/content/ICCV2025W/NeVi/papers/Magrini_Drone_Detection_with_Event_Cameras_ICCVW_2025_paper.pdf)

<div align="center">
  <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/images/evflying.png?raw=true" 
    alt="Spash image"
    width=720/>
</div>


Official repository for "EV-Flying: an Event-based Dataset for In-The-Wild Recognition of Flying Objects".
It includes **train** and **test** splits with zipped subfolders for each sequence.

The full dataset it available for download on the official [HuggingFace page](https://huggingface.co/datasets/GabrieleMagrini/Ev-Flying)🤗.


**Demos and examples** can be found in the official [website](https://magrinigabriele.github.io/Ev-Flying/).


---

## 📂 Dataset Structure

```
Ev-Flying/
 ├── Train/
 │    ├── 0/
 │    │   ├── 0.npy
 │    │   ├── coordinates.txt
 │    │   └── tracks.txt
 │    ├── 1/
 │    └── ...
 ├── Test/
 │    ├── 24/
 │    ├── 26/
 │    └── ...
```

Each folder corresponds to one sequence (event data and annotations).


---

## 📝 Annotation Format

Each sequence includes two **`.txt` annotation file** with bounding box and identity information for every frame.
Annotations comprise both bounding box coordinates with id and class of the flying object, while tracks represent the single annotated events, meaning each event has been assigned to one of the 4 possible classes (Bird, Insect, Drone, Background).

The format of the annotations is:

```
time: x1, y1, x2, y2, id, class
```
- **time**  → time relative to the start of the recording in 'seconds.microseconds' for the annotation
- **x1, y1** → top-left corner of the bounding box  
- **x2, y2** → bottom-right corner of the bounding box  
- **id** → unique identifier for the flying object, consistent across frames (for tracking)  
- **class** → object class  

📌 Example:
```
1.33332: 490.0, 413.0, 539.0, 448.0, 1, 3
6.33327: 609.0, 280.0, 651.0, 308.0, 2, 2
```

This structure is compatible with standard detection and tracking pipelines, while maintaining instance-level identity across time.

---

## 📥 Download


### Clone the entire dataset
```bash
git lfs install
git clone https://huggingface.co/datasets/GabrieleMagrini/Ev-Flying
```


### Use with 🤗 Datasets
```python
from datasets import load_dataset

# Load full dataset
ds = load_dataset("GabrieleMagrini/Ev-Flying")

# Load specific split
train_set = load_dataset("GabrieleMagrini/Ev-Flying", split="train")
test_set  = load_dataset("GabrieleMagrini/Ev-Flying", split="test")
```

The files on HuggingFace contains only insects and birds, to also incorporate drone you can do so by downloading and adding [this](https://drive.google.com/file/d/1FV2XcBMb_AlAFptK0OPDCFJ1eWh0zd7F/view?usp=sharing) extract from the FRED dataset containing 2 additional 2 minutes long drone labeled videos as used in the paper.
Simply download the zip folder and extract it in the same position of the already donwloaded EvFlying folder. 

Demos and examples can be found in the official [website](https://magrinigabriele.github.io/Ev-Flying/)


---

## 🖼️ Examples



<div align="center">
  <h1 style="font-size: 2rem; margin-bottom: 1rem; color: #fff;">Insect</h1>
  <p>
    <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/videos/video_10_id_31_class_2.webp?raw=true" width="45%" />
    <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/videos/video_26_id_72_class_2.webp?raw=true" width="45%" />
  </p>
</div>

<div align="center">
  <h1 style="font-size: 2rem; margin-bottom: 1rem; color: #fff;">Bird</h1>
  <p>
    <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/videos/video_27_id_45_class_1.webp?raw=true" width="45%" />
    <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/videos/video_27_id_70_class_1.webp?raw=true" width="45%" />
  </p>
</div>

<div align="center">
  <h1 style="font-size: 2rem; margin-bottom: 1rem; color: #fff;">Drone</h1>
  <p>
    <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/videos/video_drone_id_3_class_3.webp?raw=true" width="45%" />
    <img src="https://github.com/MagriniGabriele/Ev-Flying/blob/main/static/videos/video_drone_id_0_class_3.webp?raw=true" width="45%" />
  </p>
</div>

---

## Star History

<a href="https://www.star-history.com/?repos=MagriniGabriele%2FEv-Flying&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=MagriniGabriele/Ev-Flying&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=MagriniGabriele/Ev-Flying&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=MagriniGabriele/Ev-Flying&type=date&legend=top-left" />
 </picture>
</a>

## ✨ Citation

If you use **Ev-Flying** in your research, please cite:

```
@inproceedings{magrini2025ev,
  title={EV-flying: An event-based dataset for in-the-wild recognition of flying objects},
  author={Magrini, Gabriele and Becattini, Federico and Colombo, Giovanni and Pala, Pietro},
  booktitle={Proceedings of the Computer Vision and Pattern Recognition Conference},
  pages={4947--4955},
  year={2025}
}
```


