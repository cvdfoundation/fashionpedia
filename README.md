# Fashionpedia Dataset

Fashionpedia is a new dataset which consists of two parts: (1) an ontology built by fashion experts containing 27 main apparel categories, 19 apparel parts, 294 fine-grained attributes and their relationships; (2) a dataset with everyday and celebrity event fashion images annotated with segmentation masks and their associated per-mask fine-grained attributes, built upon the Fashionpedia ontology.

## Download

CVDF hosts the images and annotations in the Fashionpedia dataset.  

### Images

- [Training images](https://s3.amazonaws.com/ifashionist-dataset/images/train2020.zip)
- [Validation and test images](https://s3.amazonaws.com/ifashionist-dataset/images/val_test2020.zip)

### Annotations

- [instances_attributes_train2020](https://s3.amazonaws.com/ifashionist-dataset/instances_attributes_train2020.json)
- [instances_attributes_val2020](https://s3.amazonaws.com/ifashionist-dataset/instances_attributes_val2020.json)
- [test_image_info2020](https://s3.amazonaws.com/ifashionist-dataset/info_test2020.json)



## Annotation format

We follow the annotation format of the [COCO dataset](http://mscoco.org/dataset/#download) with additonal fields, such as attributes. The annotations are stored in the [JSON format](http://www.json.org/) and are organized as follows:

```
{
 "info": info,
 "categories": [category],
 "attributes": [attribute],
 "images": [image],
 "annotations": [annotation],
 "licenses": [license]
}

info{
  "year" : int,
  "version" : str,
  "description" : str,
  "contributor" : str,
  "url" : str,
  "date_created" : datetime,
}

category{
  "id" : int,
  "name" : str,
  "supercategory" : str,  # parent of this label
  "level": int,           # levels in the taxonomy
  "taxonomy_id": string,
}

attribute{
  "id" : int,
  "name" : str,
  "supercategory" : str,  # parent of this label
  "level": int,           # levels in the taxonomy
  "taxonomy_id": string,
}

image{
  "id" : int,
  "width" : int,
  "height" : int,
  "file_name" : str,
  "license" : int,
  "time_captured": string,
  "original_url": string,
  "isstatic": int, 0: the original_url is not a static url,
  "kaggle_id": str,
}

annotation{
  "id" : int,
  "image_id" : int,
  "category_id" : int,
  "attribute_ids": [int],
  "segmentation" : [polygon] or [rle]
  "bbox" : [x,y,width,height], # int
  "area" : int
  "iscrowd": int (1 or 0)
}
polygon: [x1, y1, x2, y2, ...], where x, y are the coordinates of vertices, int
rle: {"size", (height, widht), "counts": str}

license{
  "id" : int,
  "name" : str,
  "url" : str
}
```



## More information

Check out more information about Fashionpedia below:

- [Fashionpedia python API](<https://github.com/KMnP/fashionpedia-api>)  for reading, visualizing annotations, and result evaluation
- [Fashionpedia project page](<https://fashionpedia.github.io/home/index.html>)

