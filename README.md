# Custom MOTS tools
> Tools for evaluating and visualizing results for the Multi Object Tracking and Segmentation (MOTS) task on custom dataset.

This repository is a modified fork from the original source code [mots_tools](https://github.com/VisualComputingInstitute/mots_tools)

## Installation

1. Clone this repository

```sh
git clone https://github.com/hoanW/Custom_MOTS_tools.git
cd Custom_MOTS_tools
```

2. Install dependencies

```sh
pip3 install -r requirements.txt
```
[FFmpeg](https://ffmpeg.org/download.html) is also required for visualization.

To install FFmpeg in Debian os:
```sh
sudo apt install ffmpeg
```

## Usage
### Customization
Edit the custom LABELS in mots_common/io.py file. LABELS should contain backgroud as the first element as class id 0. For example:
```
LABELS = ['__background__', 'car', 'pedestrian']
```

Data for evaluation and visualization are:
1. img_folder: contains video images.
2. gt_folder: contains gt data in text file.
3. result_folder: contains tracking results in text file.
4. sepmap: a text file contains list of videos to evaluate/visualize.

Annotation format for gt and tracking result data following https://www.vision.rwth-aachen.de/page/mots.

To get coco-form encoded masks from numpy array as a string, use:
```sh
import pycocotools.mask as rletools

encoded_mask_string = rletools.encode(np.asfortranarray(numpy_masks))["counts"].decode("utf-8")
```

### Evaluation
```sh
python3 mots_eval/eval.py data/results_folder data/gt_folder data/all.seqmap
```

### Visualization
```sh
python3 mots_vis/visualize.py data/results_folder data/img_folder data/output_folder data/all.seqmap
```
## References
```
@inproceedings{Voigtlaender19CVPR_MOTS,
 author = {Paul Voigtlaender and Michael Krause and Aljo\u{s}a O\u{s}ep and Jonathon Luiten and Berin Balachandar Gnana Sekar and Andreas Geiger and Bastian Leibe},
 title = {{MOTS}: Multi-Object Tracking and Segmentation},
 booktitle = {CVPR},
 year = {2019},
}
```
## Meta

Hoan Vu – hoanviet.vu@gmail.com

