# FlapVis Dataset

* # Flapping-wing Visual (FlapVis): A Small-Target Detection Dataset Captured by a Flapping-Wing Flying Robot

This repository hosts a **representative subset** of the **FlapVis** dataset, a self-collected aerial small-target detection dataset acquired by a flapping-wing flying robot (FWFR). Unlike conventional aerial datasets collected by relatively stable rotary-wing UAVs, FlapVis is captured during actual flapping-wing flight, where the onboard camera is affected by image jitter and unstable imaging conditions. As a result, the dataset naturally contains typical visual degradation characteristics of FWFRs, such as motion blur and weak target textures. The complete FlapVis dataset will be made publicly available upon publication of the associated paper.

## Highlights

### Captured by a real flapping-wing platform

All images are acquired by a self-developed FWFR named **USTB-Hawk** during real flight, rather than by rotary-wing UAVs or simulation. The data therefore reflects the genuine imaging conditions of onboard flapping-wing perception.

![fig_flapvis_samples](C:\Users\ZeweiZhao\Downloads\fig_flapvis_samples.png)

### Motion-degraded, small-target, diverse scenes

The onboard camera records multiple low-altitude ground scenes under diverse conditions, including playgrounds, grasslands, campus roads, urban intersections, and open outdoor environments. Most targets are small-scale (bounding boxes smaller than 20 × 20 pixels), posing challenges for accurate detection.

### Manually annotated and quality-checked

All selected frames are manually annotated with bounding boxes, and the annotations are carefully checked to ensure labeling consistency.

## Subset Overview

| Property             | Value                                  |
| -------------------- | -------------------------------------- |
| Platform             | USTB-Hawk (flapping-wing flying robot) |
| Images (this subset) | 150                                    |
| Annotated instances  | 570                                    |
| Resolution           | 640 × 320                              |
| Categories           | 2 (`car`, `people`)                    |
| Annotation format    | YOLO (`.txt`) and COCO (`.json`)       |

> **Note:** This repository provides only a representative subset of FlapVis for verification purposes. The complete dataset (3052 images, split 2441 / 305 / 306 for train / val / test) will be made publicly available upon publication of the associated paper.

## Categories

| id   | name   |
| ---- | ------ |
| 0    | car    |
| 1    | people |

## Data Collection and Preprocessing

The raw footage is recorded by the on board camera of USTB-Hawk during actual flapping-wing flight. To reduce temporal redundancy while preserving scene diversity, one frame is extracted every 30 frames from the recorded videos. Only frames containing at least one target are retained, and all retained frames are manually annotated. The samples in this subset are selected by stratified sampling across scene groups to cover the diversity of the full dataset.

## Data Structure

The subset is organized as follows:

   ```
${FlapVis_ROOT}
 -- images
     |-- <frame_name>.jpg
     |-- <frame_name>.jpg
     ...
 -- labels
     |-- <frame_name>.txt
     |-- <frame_name>.txt
     ...
 -- annotations.json     # COCO-format annotations
   ```

Each label file shares the same base name as its corresponding image.

## Annotation Format

Each image has a corresponding YOLO-format label file (`labels/<name>.txt`). Each line describes one object as:

   ```
<class_id> <x_center> <y_center> <width> <height>
   ```

where all coordinates are normalized to `[0, 1]` with respect to the image size. A COCO-format file (`annotations.json`) containing the `images`, `annotations`, and `categories` fields is also provided for convenience.

## Data Availability

A representative subset of the FlapVis dataset is provided in this repository for verification purposes. The complete dataset will be made publicly available upon publication of the associated paper.
