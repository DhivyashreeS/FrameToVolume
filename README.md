# FrameToVolume: 2D-to-3D Image-to-GIF Conversion

A lightweight Python pipeline that transforms a single 2D photograph into rich 3D representations—depth maps, point clouds, meshes—and generates GIF animations. Powered by state‑of‑the‑art monocular depth estimation models (Depth Anything V2, MiDaS, ZoeDepth) and Open3D for geometric reconstruction.

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/2704f4a7-b903-4a0c-b607-5cfa10f7ab8e" />

<img width="200" height="200" alt="map_depth_anything" src="https://github.com/user-attachments/assets/0777f683-937b-4658-880b-976c3353dead" />

<img width="200" height="200" alt="map_midas" src="https://github.com/user-attachments/assets/52565db0-4969-4344-9222-0c3354eac8b5" />

<img width="200" height="200" alt="map_zoe_depth" src="https://github.com/user-attachments/assets/4d128865-b82f-4571-b85b-f914a72f6ef4" />
<br>
<img src="https://github.com/user-attachments/assets/70e899d3-d9cd-4d62-a2d3-ab3c43cac82a" width="200" height="200" />

<img src="https://github.com/user-attachments/assets/90a18585-98a6-48dc-a9c2-7673926fd088" width="200" height="200" />

<img src="https://github.com/user-attachments/assets/12376fcd-1110-4d24-b87f-3567b9f31ec7" width="200" height="200" />

---

## Requirements

* **Python**: 3.10+
* **Libraries**:

  ```bash
  pip install numpy opencv-python torch torchvision torchaudio matplotlib imageio open3d pillow transformers tqdm timm
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

