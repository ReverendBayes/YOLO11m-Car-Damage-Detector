
# YOLO11m Model for Car Body Damage Detection

This custom-trained YOLO11m model (`trained.pt`) was fine-tuned on a custom dataset to detect and classify common vehicle body damage: cracks, dents, flat tires, scratches, broke headlights and tailights, and broken windshields. It’s high-capacity, fast-enough, and built to plug into real-world inspection workflows.

---


## Model Overview

- **Architecture:** YOLO11m (231 layers, ~20M parameters)
- **Dataset:** CarDD_COCO (custom fine-tuned version)
- **Training:** Google Colab (NVIDIA L4 GPU, 22GB VRAM)
- **Classes:** dent, scratch, crack, shattered_glass, broken_lamp, flat_tire
- **Training Framework:** Ultralytics 8.3.117, PyTorch 2.6.0+cu124, Python 3.11.12

---

## Performance Snapshot

Class-by-class tactical breakdown:

| Class            | Box Precision (P) | Recall (R) | mAP50 | mAP50-95 |
|:-----------------|:------------------|:-----------|:------|:---------|
| shattered_glass  | 0.979              | 0.978      | 0.994 | 0.963    |
| flat_tire        | 0.943              | 0.919      | 0.959 | 0.932    |
| broken_lamp      | 0.826              | 0.821      | 0.895 | 0.796    |
| dent             | 0.699              | 0.520      | 0.581 | 0.330    |
| scratch          | 0.610              | 0.561      | 0.573 | 0.341    |
| crack            | 0.559              | 0.426      | 0.409 | 0.223    |

---

## Tactical Highlights

- **Shattered Glass:** Elite — nearly flawless across all metrics.  
- **Flat Tire:** Excellent — reliable, highly precise detections.  
- **Broken Lamp:** Very strong — high precision and consistency.  
- **Dent/Scratch/Crack:** Weakest — fair performance, but prone to missed detections and slight localization drift (especially cracks).

---

## Use Cases

This model is fully usable for visual inspection support. It is intended as an assistive tool—not a replacement—for human service advisors. It aims to accelerate visual inspections, flag overlooked damage, and ensure consistency across high-throughput intake workflows. Use for inspection workflows, damage logging, or visual diagnostics.

This model saves time, adds consistency, and helps document condition clearly before keys are handed over. It’s assistive—not autonomous. It gives advisors a head start.

- Pre-loaner vehicle inspections
- Service center damage logging
- Fleet condition audits
- Insurance pre-claim imaging
- Rental return documentation

---

## Real-World Use: BMW Pre-Loaner Inspections

An enhanced version of this model is running in BMW service environments to support pre-loaner vehicle inspections.

Here’s how it works:
- Technicians capture images of the vehicle exterior.
- The model runs inference and flags visible body damage.
- Detections are mapped to a standard car diagram automatically.
- Human service advisors review and finalize the report.

This setup saves time, adds consistency, and helps document condition clearly before keys are handed over. It’s assistive—not autonomous. It gives advisors a head start.

“Good enough” here means:  
- Fewer missed issues  
- Fewer false alarms  
- Faster workflows  
- Repeatable results across locations

---
## Example Outputs

Below are sample detection results from the model:

![Example 1](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/1.png)
![Example 2](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/2.png)
![Example 3](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/3.png)
![Example 4](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/4.png)
![Example 5](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/5.png)
![Example 6](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/6.png)
![Example 7](https://raw.githubusercontent.com/ReverendBayes/vehicle_body_damage_detector/main/public/7.png)


---

## Model Files

- `trained.pt` — trained YOLO11m checkpoint 

---

## Quickstart

### 1. Install Ultralytics
```bash
pip install ultralytics
```

### 2. Load and Inference
```python
from ultralytics import YOLO

model = YOLO("trained.pt")
results = model("your_image.jpg", save=True)
results[0].show()  # Visualize output
```

---

## References

- [Ultralytics GitHub](https://github.com/ultralytics/ultralytics)

---
