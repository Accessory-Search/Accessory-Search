# Accessory Search

This repo has the accessory annotation and accessory search leaderboard proposed by "JEDI: Joint accEssory Discovery and re-Identification (JEDI) for Accessory Search". Including:

* the annotation of Accessory-Market.

* the annotation of Accessory-MSMT17.

## Annotation

### 1.Data Sources and Annotation Format
* Please download original images from [Market1501](http://zheng-lab.cecs.anu.edu.au/Project/project_reid.html)[[1](#refer-anchor-1)] and [MSMT17-V1](https://arxiv.org/pdf/1711.08565v2.pdf). The image name and person id is consistance with original reid data. 
* We provide txt files for annotation in folder annotation. The annotation is formatted as **[ImageName, [left, top, right, bottom], AccessoryId, IsQuery]**. Query images are marked by IsQuery==1, and gallery images are marked by IsQuery==0.     
  * The Accessory-Market dataset has 40104 object bounding boxes which is classified to 1448 object ids, and is divided into 4848 queries and 35256 galleries.  
  * The Accessory-MSMT17 dataset has 74528 object bounding boxes which is classified to 2713 object ids, and is divided into 10020 queries and 64508 galleries.
  More statics of Accessory-Market and Accessory-MSMT17 is listed below.

### 2.Accessory Cases Visualization
* Sample images of Accessory-Market and Accessory-MSMT17 are shown below. Each image has multiple accessories in red boxes. Some accessories labeled as the same ID are enlarged for visualization.  
![cases_visualization](https://github.com/Accessory-Search/Accessory-Search/blob/main/Images/cases.jpg)

### 3.Data Statics

* The statics of Accessory-Market and Accessory-MSMT17 are shown below. 

| Name             | IDs  | Images | Bboxes | Qeuries | Galleries |QuerySize           |
| :--:             | :--: | :--:   | :--:   | :--:    | :--:      |:--:                |
| Accessory-Market | 1448 | 15321  | 40104  | 4848    |   35256   |[33&plusmn;18,34&plusmn;15]   | 
| Accessory-MSMT17 | 2713 | 32033  | 74528  | 10020   |   64508   |[108&plusmn;104,77&plusmn;65] |

* Statistical analysis of the Accessory-Market and Accessory-MSMT17 are shown below. (a) and (b): the distribution of accessory IDs. (c): correspondence between accessories and human parsing categories. (e,f,g): the relation ship between accessory IDs and person IDs. (d) and (h): the heatmaps of the bounding box locations.
![dataset_distribution](https://github.com/Accessory-Search/Accessory-Search/blob/main/Images/datacurve1.jpg)


## Evaluation Metrics
We evaluate the accessory search performance of different methods using metrics listed blow:

* **mAP**: We use mean average precision(mAP) to evaluate the overall performance. For each query, we calculate the area under the Precision-Recall curve, which is known as average precision(AP)[[1](#refer-anchor-1)]. Then the mean value of APs of all queries, i.e. mAP is obtained.
* **CMC**: Cumulative Matching Characteristic, which shows the probability that a query object appears in deifferent-sized candidate lists. The calculation process is described in [[1](#refer-anchor-1)]. We choose Rank-1, Rank-5 and Rank-10 of CMC curve for a brief comparision in following leardborad.   
* **ReCall(IoU>0.6)**: We propose ReCall(IoU>0.6) to measure how well the accessories have been exploited, i.e. recall at IoU>0.6. The box is regarded as a true match if its IoU to a ground truth accessory box is larger than 0.6. This metric is computed across all query and gallery boxes.

    Note: The calculation of mAP and CMC in proposed accessory search task is very similar with ReID. However, an image is considered as true positive only if it contains the same accessory as the query, no matter if the person is the same or not.
 

## Leardboard

We evaluated following methods in proposed Accessory-Market and Accessory-MSMT17 datasets, the results are shown below.

* Accessory-Market

| Method | Recall | mAP | R-1 | R-5 | R-10 |
| :--:   | :--:   | :--:| :--:| :--:| :--: |
| ISP [[3](#refer-anchor-3)]    |    _    |   0.4  |  0.2   |   0.8  |   1.4   |
| DELG[[2](#refer-anchor-2)]   |    -   | 0.5    |  1.9   |   5.3  |   7.1   |
| GlobalTrack [[4](#refer-anchor-4)] | -   |   1.9  |   12.3  |   40.4  |  49.0    |
| JEDI   |    18.8   |  **20.8**  |   **24.4**  |  **77.4**   |   **90.4**   |

* Accessory-MSMT17

| Method | Recall | mAP | R-1 | R-5 | R-10 |
| :--:   | :--:   | :--:| :--:| :--:| :--: |
| ISP [[3](#refer-anchor-3)]    |   -     |  0.2   |   0.2  |  0.7   |  1.2    |
| DELG[[2](#refer-anchor-2)]   |    -    |  0.1   |   0.3  |  1.1   |  1.1    |
| GlobalTrack [[4](#refer-anchor-4)] | -  |   1.6  |  4.3   |  30.4   |  39.1    |
| JEDI   |    7.7    |  **16.2**   |  **20.6**   |  **74.2**   |  **87.4**    |


* Speed (Inference time on [V100](https://www.nvidia.com/en-us/data-center/v100/) of one matching)

| Method | Time(ms) | 
| :--:   | :--:   |
| ISP [[3](#refer-anchor-3)]    |   33     |  
| DELG[[2](#refer-anchor-2)]   |   298    |  
| GlobalTrack [[4](#refer-anchor-4)] | 113  |   
| JEDI   |    40    |


* For more information, feel free to contact us at accessory_search@163.com. 


## Refenrence
<div id="refer-anchor-1"></div>

- [1] [Scalable Person Re-identification: A Benchmark](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Zheng_Scalable_Person_Re-Identification_ICCV_2015_paper.pdf) 

<div id="refer-anchor-2"></div>

- [2] [Unifying deep local and global features for image search](https://arxiv.org/pdf/2001.05027.pdf)

<div id="refer-anchor-3"></div>

- [3] [Identity-Guided Human Semantic Parsing for Person Re-Identification](https://arxiv.org/pdf/2007.13467.pdf)

<div id="refer-anchor-4"></div>

- [4] [GlobalTrack: A Simple and Strong Baseline for Long-term Tracking](https://arxiv.org/pdf/1912.08531.pdf)

<div id="refer-anchor-5"></div>

- [5] [Person Transfer GAN to Bridge Domain Gap for Person Re-Identification](https://arxiv.org/pdf/1711.08565v2.pdf)
