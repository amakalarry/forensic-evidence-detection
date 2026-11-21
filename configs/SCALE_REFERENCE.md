# Official Ultralytics Scale Reference
# Keep this file alongside the YAMLs to prevent future misconfigurations.

## YOLOv8 Official Scales
| Variant | depth | width | max_channels |
|---------|-------|-------|--------------|
| n       | 0.33  | 0.25  | 1024         |
| s       | 0.33  | 0.50  | 1024         |
| m       | 0.67  | 0.75  | 768          |
| l       | 1.00  | 1.00  | 512          |
| x       | 1.00  | 1.25  | 512          |

## YOLO11 Official Scales
| Variant | depth | width | max_channels |
|---------|-------|-------|--------------|
| n       | 0.50  | 0.25  | 1024         |
| s       | 0.50  | 0.50  | 1024         |
| m       | 0.50  | 1.00  | 512          |
| l       | 1.00  | 1.00  | 512          |
| x       | 1.00  | 1.50  | 512          |

## Key Differences (m variants)
- YOLOv8-m: deeper (0.67) but narrower (0.75), higher max_ch (768)
- YOLO11-m: shallower (0.50) but full-width (1.00), lower max_ch (512)
- These are NOT interchangeable. Using YOLOv8-m scales on a YOLO11 architecture
  produces a model that is neither YOLOv8-m nor YOLO11-m.

## What Went Wrong in v1
The enhanced YAMLs used NANO-scale multipliers (depth=0.33, width=0.25)
instead of medium-scale, making the "baseline vs enhanced" comparison
invalid (medium baseline vs nano enhanced = apples to oranges).
