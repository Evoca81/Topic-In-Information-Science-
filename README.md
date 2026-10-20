# Video resolution vs. pose-tracking accuracy in bouldering

**Question:** How much does MediaPipe pose-tracking accuracy drop as video resolution falls? Is the drop larger for
distal joints (wrists, ankles) than for proximal joints (shoulders, hips)?

**Design:** For six bouldering clips (the first 300 frames of each), MediaPipe PoseLandmarker (full model, VIDEO mode,
the same pipeline as `notebooks/day1.ipynb`) is run at native resolution (the reference) and at 1280, 854, 640, 426 and
320 px on the long side. Error is the distance from the reference landmark divided by torso length. Accuracy is PCK@0.1.

## Files
| File | Purpose |
|---|---|
| `resolution_study.ipynb` | Whole pipeline: pose estimation at every resolution level (`results/resolution_results.csv`), Friedman and Page trend tests, the mixed model, and the figure (`results/stats.txt`, `results/resolution.png`) |
| `pose_landmarker_full.task` | MediaPipe pose model used by the notebook |
| `results/drop_test.txt` | Wilcoxon test: distal vs. proximal PCK drop |
| `report.pdf` / `report.tex` | Report |

## Run
```bash
pip install mediapipe opencv-python numpy pandas scipy statsmodels matplotlib jupyter
# clips in data/ named like 4Q_Square_D_2026A.MOV
jupyter notebook resolution_study.ipynb   # then Run All
```
## Regarding Data/Videos
Because Github limits the maximum capacity for videos so i will upload it to a google drive
