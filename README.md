# The COCO-Tasks Dataset

This repository contains the COCO-Tasks Dataset. For more information regarding the dataset please check our [paper](https://arxiv.org/abs/1904.03000).

If you use our dataset, please cite our paper.

```latex
@inproceedings{cocotasks2019,
    Author    = {Sawatzky, Johann and Souri, Yaser and Grund, Christian and Gall, Juergen},
    Title     = {{What Object Should I Use? - Task Driven Object Detection}},
    Booktitle = {{CVPR}},
    Year      = {2019}
}
```

Table of Contents
=================
 
 * [Downloading](#downloading)
     * [CVPR 2019 Release](#cvpr-2019-release)
 * [Usage](#usage)
     * [Annotations](#annotations)
     * [Image Lists](#image-lists)
     * [Detection Files](#detection-files)

## Downloading

**NOTE**: We use [Git-LFS](https://git-lfs.github.com/) to host the annotation files, so you need to first install it.

The you can clone our repository which will download all the files.

### CVPR 2019 Release

To download our dataset release used in our CVPR 2019 paper, use the following:

```bash
git clone -b cvpr2019 --depth 1 git@github.com:coco-tasks/dataset.git coco-tasks
```

## Usage

The dataset's annotation format is the same as the [COCO](http://cocodataset.org/) format with a small addition. This means that you can use the [COCO's API](https://github.com/cocodataset/cocoapi) to use our dataset.

You also have to download the images separately from [COCO dataset's website](http://cocodataset.org/#download).

If you want to reproduce our results, checkout the our code: [yassersouri/task-driven-object-detection](https://github.com/yassersouri/task-driven-object-detection)

### Annotations

Our annotations are located in the `annotations` folder. For example the file `task_1_train.json` is the training annotation file for task 1.

Each annotation, i.e. an object in an image is specified using the following dictionary structure in the JSON files.

```js
{
    'segmentation': [], // the segmentation mask of the object
    'area': 33356.1888,
    'iscrowd': 0,
    'image_id': 576993,  // COCO image id of the object
    'bbox': [57.6, 87.65, 266.4, 195.12],  // bounding box of the object
    'COCO_category_id': 58,  // the original category id from COCO
    'category_id': 0,  // whether or not it is preferred object in this image for the task. 0 means "not preferred" and 1 means "preferred"
    'id': 207 // COCO annotation id of the object
}
```

### Image Lists

The text files inside the `image_lists` directory specify which COCO image ids where used for the creation of our dataset.

There is no need to use these files, they are here for the sake of completeness.

### Detection Files

As described in our paper, at test time, we need to first perform object detection on an image. For reproducibility purposes, we have included the result of object detection from our custom trained Faster-RCNN and YOLOv2 object detectors in `detections_faster.json` and `detections_yolo.json` files respectively.

Each detection is specified using the following dictionary structed in the JSON file.

```js
{
    'image_id': 262148, //COCO image id
    'category_id': 1,  //COCO category id
    'bbox': [250.77206420898438,  // bounding box of the detection [x, y, width, height]
             50.91807556152344,
             154.542236328125,
             295.10801696777344],
    'score': 0.9993196725845337  // detection score in the range [1, 0]
}
```

