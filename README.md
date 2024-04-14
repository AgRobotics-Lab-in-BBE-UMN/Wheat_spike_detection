# Wheat Spike Detection
Detect wheat spikes by using [open-MMLab mmdection](https://github.com/open-mmlab/mmdetection). The publication is [Wheat-Net: An Automatic Dense Wheat Spike Segmentation Method Based on an Optimized Hybrid Task Cascade Model](https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2022.834938/full).
We use [Labelme](https://github.com/labelmeai/labelme) to annotate wheat spikes. The annotations are saved into JSON files.

Here we prepare **create_json_file v2.ipynb** to convert Labelme JSON files into one COCO format JSON file.

Usage like:
```
#'D:\train_data\json*.json' to get all JSON files of the training dataset
labelme_json=glob.glob(r'D:\train_data\json*.json')

#create one JSON file whose name is coco_train.json
labelme2coco(labelme_json,'./coco_train.json') 
```

We use the Hybrid Task Cascade (HTC) model for the best mAP value. the HTC mode needs to create semantic PNG files for the training dataset.
we prepare **generate_segm_mask.ipynb** for this purpose.
Note, for wheat spike detection, the classes are set as {spike:0, background:1}

The main function is 'create_mask_fromjson_forxxx()', please carefully set class values. 
Use glob.glob() to get all JSON files and create corresponding semantic files by calling 'create_mask_fromjson_forxxx()' function.
