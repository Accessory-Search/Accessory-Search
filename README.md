# Accessory Search

This repo has the source code for the paper "JEDI: Joint accEssory Discovery and re-Identification (JEDI) for Accessory Search". Including:

* the annotation of Accessory-Market

* the annotation of Accessory-MSMT17

* the evaluation code of Accessory-Search task

## Annotation

### Data Sources and Annotation Format
* Please download original images from [Market1501](http://zheng-lab.cecs.anu.edu.au/Project/project_reid.html) and MSMT17-V1. The image name and person id of each accessory is consistance with original reid data. 
* We provide txt files for annotation in folder annotation. The annotation is formatted as [ImageName, [left, top, right, bottom], AccessoryId, IsQuery].     
  * The Accessory-Market dataset has 40104 object bounding boxes which is classified to 1448 object ids.
  * The Accessory-MSMT17 dataset has 74528 object bounding boxes which is classified to 2713 object ids.
  More statics of Accessory-Market and Accessory-MSMT17 is listed below.

### Accessory Cases Visualization
Sample images of Accessory-Market and Accessory-MSMT17. Each image has multiple accessories in red boxes. Some accessories labeled as the same ID are enlarged for visualization.  
![cases_visualization](https://github.com/Accessory-Search/Accessory-Search/blob/main/Images/20210420144758.jpg)


### Data Statics

| Name             | IDs  | Images | Bboxes | Qeuries | QuerySize           |
| :--:             | :--: | :--:   | :--:   | :--:    | :--:                |
| Accessory-Market | 1448 | 15321  | 40104  | 4848    | $[33\pm18,34\pm15]$   | 
| Accessory-MSMT17 | 2713 | 32033  | 74528  | 10020   | $[108\pm104,77\pm65]$ |

### Data Distribution
Statistical analysis of the Accessory-Market and Accessory-MSMT17. (a) and (b): the distribution of accessory IDs. (c): correspondence between accessories and human parsing categories. (e,f,g): the relation ship between accessory IDs and person IDs. (d) and (h): the heatmaps of the bounding box locations.
![dataset_distribution](https://github.com/Accessory-Search/Accessory-Search/blob/main/Images/datacurve1.jpg)

================================================================

## Evaluation

We evaluate the accessory search performance of different methods using metrics listed blow:

* Metrics   
    * mAP: We use mean average precision(mAP) to evaluate the overall performance. For each query, we calculate the area under the Precision-Recall curve, which is known as average precision(AP)[1](#refer-anchor-1). Then the mean value of APs of all queries is obtained with equation blow: $$ mAP =  \frac {\sum_{i=1}^{N_q} AP_i}{N_q}  $$. 
    * CMC: 
    * ReCall(IoU>0.6): We propose ReCall(IoU>0.6) to measure how well the accessories have been exploited, i.e. recall at IoU>0.6. The box is regarded as a true match if its IoU to a ground truth accessory box is larger than 0.6. This metric is computed across all query and gallery boxes.


================================================================

## Leardboard

Comming soon......


* For more information, feel free to contack us at accessory_search@163.com. 


## Refenrence
<div id="refer-anchor-1"></div>
- [1] [Scalable Person Re-identification: A Benchmark](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Zheng_Scalable_Person_Re-Identification_ICCV_2015_paper.pdf) 
