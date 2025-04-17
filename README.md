
# Vehicle Body Damage Detection — YOLOv8

This custom-trained YOLOv8 model (`crystal_best.pt`) detects and localizes common vehicle body damage: cracks, dents, rust, scratches, and paint issues. It’s fast, lightweight, and built to plug into real-world inspection workflows.

---

## Model Overview

- **Architecture:** YOLOv8 (72 layers, ~3M parameters)  
- **Dataset:** Polygon-annotated custom set  
- **Training Environment:** Google Colab (Tesla T4)  
- **Classes:** Crack, Dent, PDR-Dent, Paint-Crack, Paint-fading, Rust, Scratch  
- **Inference Speed:** ~8.6ms/image (Tesla T4)  
- **Versions:** Ultralytics 8.3.110, Torch 2.6.0+cu124, Python 3.11.12

---

## Performance Snapshot

| Model              | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
|-------------------|-----------|--------|--------|--------------|
| **crystal_best.pt**   | 0.765     | 0.518  | 0.585  | 0.353        |
| **pre-trainedYOLOv8.pt** | 0.0115    | 0.0497 | 0.0079 | 0.0040       |

The pretrained checkpoint was practically unusable—low recall, poor localization, and unreliable predictions. The trained model hits usable precision and recall levels, with strong bounding box consistency. It's not perfect, but it’s fast, dependable, and human-reviewable.

---

## Use Cases

- Vehicle intake inspections  
- Repair cost estimation  
- Fleet maintenance logs  
- Insurance claim support  

---

## Damage Detected
- Crack
- Dent
- PDR-Dent
- Paint-Crack
- Paint-fading
- Rust
- Scratch

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


## Quickstart

### 1. Install Ultralytics
```bash
pip install ultralytics
```

### 2. Run Inference
```python
from ultralytics import YOLO

model = YOLO("crystal_best.pt")
results = model("your_image.jpg", save=True)
results[0].show()  # Optional: visualize in notebook
```

---

## Files

- `crystal_best.pt` — YOLOv8 model trained on custom vehicle damage dataset

---

## References

- [Ultralytics YOLOv8 Documentation](https://docs.ultralytics.com/)  
- [Ultralytics GitHub](https://github.com/ultralytics/ultralytics)

---
