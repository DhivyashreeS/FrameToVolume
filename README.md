# FrameToVolume: 2D-to-3D Image-to-GIF Conversion

A lightweight Python pipeline that transforms a single 2D photograph into rich 3D representations—depth maps, point clouds, meshes—and generates parallax-view GIF animations. Powered by state‑of‑the‑art monocular depth estimation models (MiDaS, Depth Anything V2, ZoeDepth) and Open3D for geometric reconstruction.

<img width="161" height="138" alt="image" src="https://github.com/user-attachments/assets/db1cafe4-8bdb-47d1-bc31-14f7b930d82b" />


---

## Requirements

* **Python**: 3.10+
* **Libraries**:

  ```bash
  pip install \
    numpy \
    opencv-python \
    torch \
    torchvision \
    torchaudio \
    matplotlib \
    imageio \
    open3d \
    pillow \
    transformers \
    tqdm \
    timm
  ```

---

## Project Structure

```
├── depth_estimator.py       # Generate depth maps, point clouds, meshes
├── gif_generator.py        # Create parallax-view GIFs from depth data
├── input/                  # Place your custom images here
│   └── bull.png            # Example input image
└── output/                 # All generated outputs are saved here
    └── bull/               # Subfolder for each run
```

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/FrameToVolume.git
   cd FrameToVolume
   ```

2. **Create a virtual environment (optional but recommended)**

   ```bash
   python3.10 -m venv venv
   source venv/bin/activate  # Linux/macOS
   venv\\Scripts\\activate # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

> *Note:* You can also install directly with the `pip install ...` command listed in **Requirements**.

---

## Usage

1. **Prepare your input**

   * Save the image you want to process into the `input/` folder.

2. **Depth Estimation & 3D Reconstruction**

   ```bash
   python depth_estimator.py
   ```

   * When prompted:

     * Enter the image file name (e.g., `bull.png`).
     * Enter an output folder name (e.g., `bull`).
   * This will generate:

     * Normalized depth maps (`.png`).
     * Colored point clouds (`.ply`).
     * Reconstructed meshes (`.ply`).
   * All files available in `output/<your_folder>/`

3. **Parallax GIF Generation**

   ```bash
   python gif_generator.py
   ```

   * When prompted:

     * Enter the same output folder name you used above (e.g., `bull`).
   * A parallax-view GIF will be created and saved in `output/<your_folder>/`.

---

## Model Details

* **MiDaS DPT-Hybrid** via Hugging Face (`Intel/dpt-hybrid-midas`)
* **Depth Anything V2 (Small)** via official API
* **ZoeDepth N** (fine-tuned on NYU-Depth indoor data)

Each model yields a raw depth estimate which is normalized and aligned to the original image resolution before geometric processing.

---

## Acknowledgements

* Ranftl et al. (2021) – *Vision Transformers for Dense Prediction* (ICCV)
* Bhat et al. (2023) – *ZoeDepth: Zero-shot Transfer by Combining Relative and Metric Depth* (CVPR)
* Yang et al. (2024) – *Depth Anything V2* (NeurIPS)
* Zhou et al. (2018) – *Open3D: A Modern Library for 3D Data Processing*

---

> Feel free to contribute—issues and pull requests are welcome!")}

