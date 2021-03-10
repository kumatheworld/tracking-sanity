# Datasets
* [VOT](#vot-globe_with_meridians-octocat)
    * [Short-Term](vot-short-term-challenges) (VOT2013, VOT2014, VOT2015, VOT2016, VOT2017, VOT2018, VOT2019, VOT2020)
    * [Long-Term](vot-long-term-challenges) (VOT-LT2018, VOT-LT2019, VOT-LT2020)
* Others
    * [OTB2015](#otb2015-tpami2015-globe_with_meridians-memo)
    * [TrackingNet](#trackingnet-eccv2018-globe_with_meridians-memo-octocat)
    * [LaSOT](#lasot-cvpr2019-globe_with_meridians-memo-octocat)
    * [GOT-10k](#got-10k-tpami2019-globe_with_meridians-memo-octocat)
### General caveats
* **Don't optimize your tracker using test sets**. Doing this is not a good idea in any machine learning field. However in visual tracking, the smallness of datasets and sensitivity of metrics make it conceivable.
* Prepare well for the huge datasets!

## VOT [:globe_with_meridians:](https://www.votchallenge.net/) [:octocat:](https://github.com/votchallenge/vot-toolkit-python)
VOT (Visual Object Tracking) Challenge is a competition that has been held as a workshop of ICCV/ECCV every year since 2013. Besides its main [short-term challenges](vot-short-term-challenges), [long-term challenges](vot-long-term-challenges) and multimodal tracking challenges have taken place recently.
### Common Features
* Every dataset mostly consists of a **mixture of existing datasets**
* The datasets are carefully constructed and mostly recycled every year
* Small
### Common Caveats
* Since each dataset is made from existing datasets, **don't use them for training/tuning your tracker**.
### VOT Short-Term Challenges
#### Features
* Unique evaluation protocols and associated metrics of average overlap, robustness and expected average overlap (EAO, since `VOT2015`)
* The test sets sequestered completely (since `VOT2017`)
* Frame-level annotations of 5 attributes (occlusion, illumination change, motion change, size change, camera motion)
#### Statistics (of the public datasets, not of the sequestered datasets)
| Year | #Videos |    #Frames | Size <br> (GB) | Update from previous year               | Links |
| ---: | ------: | ---------: | -------------: | :-------------------------------------- | :---- |
| 2013 |      16 |      5,681 |            0.3 | N/A                                     | [:globe_with_meridians:](https://www.votchallenge.net/vot2013/) [:memo:](http://prints.vicos.si/publications/304) |
| 2014 |      25 |     10,213 |            0.4 | (Complicated)                           | [:globe_with_meridians:](https://www.votchallenge.net/vot2014/) [:memo:](http://prints.vicos.si/publications/315) |
| 2015 |      60 |     21,455 |            1.3 | (Complicated)                           | [:globe_with_meridians:](https://www.votchallenge.net/vot2015/) [:memo:](http://prints.vicos.si/publications/325) |
| 2016 |      60 |     21,455 |            1.3 | Nothing                                 | [:globe_with_meridians:](https://www.votchallenge.net/vot2016/) [:memo:](http://prints.vicos.si/publications/340) |
| 2017 |      60 |     21,356 |            1.3 | 10 videos replaced with some new videos | [:globe_with_meridians:](https://www.votchallenge.net/vot2017/) [:memo:](http://prints.vicos.si/publications/359) |
| 2018 |      60 |     21,356 |            1.7 | Nothing                                 | [:globe_with_meridians:](https://www.votchallenge.net/vot2018/) [:memo:](http://prints.vicos.si/publications/365) |
| 2019 |      60 |     19,935 |            1.6 | 12 videos replaced with GOT-10k videos  | [:globe_with_meridians:](https://www.votchallenge.net/vot2019/) [:memo:](http://prints.vicos.si/publications/375) |
| 2020 |      60 |     19,945 |            1.6 | 1 video replaced                        | [:globe_with_meridians:](https://www.votchallenge.net/vot2020/) [:memo:](http://prints.vicos.si/publications/384) |
#### Used Datasets (partially uncertain)
* ??? for `VOT2013`
* [VOT2013](https://www.votchallenge.net/vot2013/), [OTB2013](http://cvlab.hanyang.ac.kr/tracker_benchmark/benchmark_v10.html), [ALOV](https://ieeexplore.ieee.org/document/6671560) for `VOT2014`
* [OTB2013](http://cvlab.hanyang.ac.kr/tracker_benchmark/benchmark_v10.html), [ALOV](https://ieeexplore.ieee.org/document/6671560), [PTR](https://link.springer.com/chapter/10.1007/978-3-642-38886-6_61) for `VOT2015` and `VOT2016`
* [OTB2013](http://cvlab.hanyang.ac.kr/tracker_benchmark/benchmark_v10.html), [ALOV](https://ieeexplore.ieee.org/document/6671560), ??? for `VOT2017` and `VOT2018`
    * In the [VOT2018 paper](http://prints.vicos.si/publications/365), [NUS-PRO](https://www.ece.nus.edu.sg/lv/pro/nus_pro.html) was prohibited for learning, whereas PTR was not mentioned. Were some videos from PTR replaced with some NUS-PRO ones?
    * Note that [TempleColor128](https://www3.cs.stonybrook.edu/~hling/data/TColor-128/TColor-128.html) is also prohibited for learning because it has some OTB videos.
* [OTB2013](http://cvlab.hanyang.ac.kr/tracker_benchmark/benchmark_v10.html), [ALOV](https://ieeexplore.ieee.org/document/6671560), ???, [GOT-10k](#got-10k-tpami2019-globe_with_meridians-memo-octocat) for `VOT2019` and `VOT2020`
    * At most 15 GOT-10k videos are finally used for replacement but [1,000 videos](https://www.votchallenge.net/vot2019/res/list0_prohibited_1000.txt) were prohibited for learning.
#### Caveats (Important!!)
* Research papers use the public sets for test since the true test sets are not available.
* The test results seem **very sensitive**.
    * See e.g. https://github.com/STVIR/pysot/discussions/94, https://github.com/visionml/pytracking/issues/79 or https://github.com/MegviiDetection/video_analyst/issues/109.
    * You might see ~30% performance changes in EAO with a small perturbation to few of your parameters.
    * Some people take adventage of this and **try to overfit the dataset** by tuning some hyperparameters.
        * See e.g. https://github.com/hqucv/siamban/issues/32 or https://github.com/zhanght021/RPT/issues/11.
### VOT Long-Term Challenges
#### Features
* Unique metrics of tracking precision, tracking recall and tracking F-score
* Video-level annotations of 9 attributes (full occlusion, out-of-view, partial occlusion, camera motion, fast motion, scale change, aspect ratio change, viewpoint change, similar objects)
#### Statistics
| Year | #Videos |    #Frames | Size <br> (GB) | Update from previous year               | Links |
| ---: | ------: | ---------: | -------------: | :-------------------------------------- | :---- |
| 2018 |      35 |    146,847 |             10 | N/A                                     | [:globe_with_meridians:](https://www.votchallenge.net/vot2018/) [:memo:](http://prints.vicos.si/publications/365) |
| 2019 |      50 |    215,294 |             16 | 15 videos added                         | [:globe_with_meridians:](https://www.votchallenge.net/vot2019/) [:memo:](http://prints.vicos.si/publications/375) |
| 2020 |      50 |    215,294 |             16 | Nothing                                 | [:globe_with_meridians:](https://www.votchallenge.net/vot2020/) [:memo:](http://prints.vicos.si/publications/384) |
#### Used Datasets
* [LTB35](https://arxiv.org/abs/1804.07056) for `VOT-LT2018`
    * Made from [UAV20L](https://cemse.kaust.edu.sa/ivul/uav123) (20), [TLD](http://vision.stanford.edu/teaching/cs231b_spring1415/papers/Kalal-PAMI.pdf) (3), some YouTube videos (6), and [AMP](https://arxiv.org/abs/1612.00089) (6).
* LTB50 for `VOT-LT2019` and `VOT-LT2020`
    * The construction is not clear but seems a superset of [LTB35](https://arxiv.org/abs/1804.07056).

## OTB2015 [TPAMI2015] [:globe_with_meridians:](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html) [:memo:](https://faculty.ucmerced.edu/mhyang/papers/pami15_tracking_benchmark.pdf)
### Features
* Test-only (not for training)
* Small
* Easy
### Statistics
| #Videos | #Frames | #Object <br> classes | #Attr. | Size <br> (GB) |  Coordinate <br> origin |
| ------: | ------: | -------------------: | -----: | -------------: |  ---------------------: |
|     100 |  59,040 |                   16 |     11 |            2.7 |                       ? |
### Caveats
* In the following 5 videos, the annotation length is shorter than the video length.
    | Video     | #Frames | #BBoxes | True range in .jpg | Remarks |
    | :-------- | ------: | ------: | :----------------: | :------ |
    | David     |     770 |     471 |    0300 ~ 0770     | |
    | Diving    |     231 |     215 |    0001 ~ 0215?    | Not mentioned in the website |
    | Football1 |      81 |      74 |    0001 ~ 0074     | |
    | Freeman3  |     474 |     460 |    0001 ~ 0460     | |
    | Freeman4  |     297 |     283 |    0001 ~ 0283     | |
* Delimiters in `groundtruth_rect.txt` vary.
    * 68 videos use `','` and 32 videos use `'\t'`.
    * The 496th bounding box of `BlurCar1` is delimited by `' '` while the rest is delimited by ```'\t'```.
* The following 4 videos do not have `0001.jpg` unlike the rest.
    | Video    | First frame |
    | :------- | ----------: |
    | BlurCar1 |    0247.jpg |
    | BlurCar3 |    0003.jpg |
    | BlurCar4 |    0018.jpg |
    | Board    |   00001.jpg |
* There are files whose purpose is obscure.
    * 48 directories out of the 98 have `cfg.mat`.
    * `Box` has `box.zip`.
    * `Human4` has empty `groundtruth_rect1.txt`.
    * `Panda` has `panda-all.txt`.
* There are bounding boxes sticking out of the FOV.
    * Examples:
        * The 75th bounding box `(348, -10, 32, 35)` of `Biker`
        * The 274th bounding box `(268, 60, 60, 83)` of `Trellis`, whose resolution is `320 x 240`
    * The coordinate origin is not clear for this reason.
* 2 videos have invalid bounding boxes at the very end.
    * The 698th bounding box `(0, 0, 0, 0)` of `Board`
    * The 472nd bounding box `(0, 0, 0, 0)` of `Twinnings`

## TrackingNet [ECCV2018] [:globe_with_meridians:](https://tracking-net.org/) [:memo:](https://arxiv.org/abs/1803.10794) [:octocat:](https://github.com/SilvioGiancola/TrackingNet-devkit)
### Features
* **Human annotations take up only ~3% and the rest is annotated by running trackers**
* Available for training
* Sequesters the test set annotations and provides an [evaluation server](http://eval.tracking-net.org/web/challenges/challenge-page/39/overview)
* Huge
* Short
* Easy
### Statistics
* Overall
    | #Videos |    #Frames | #Object <br> classes | #Attr. | Size <br> (GB) |  Coordinate <br> origin |
    | ------: | ---------: | -------------------: | -----: | -------------: |  ---------------------: |
    |  30,643 | 14,431,266 |                   27 |     15 |          1,088 |                       1 |
* Split-wise
    | Split | #Videos |    #Frames | Size <br> (GB) |
    | :-----| ------: | ---------: | -------------: |
    | TRAIN |  30,132 | 14,205,677 |          1,054 |
    | TEST  |     511 |    225,589 |             34 |
### Caveats
* The dataset is **Huge**.
    * It is provided as multiple nested .zip files.
        * `TRAIN_{0..11}.zip` (~90GB each) and `TEST.zip` (34GB).
        * If you don't delete .zip files after extraction, you'll end up using over a **3TB** of space!
* Watch out for the "human annotations at 1 fps" feature!
    * Many bounding boxes are sticking out of the FOV.
        * See https://github.com/SilvioGiancola/TrackingNet-devkit/issues/23.
    * Human annotations do not happen every 30 frames exactly.
        * E.g. `TRAIN_0/A1RSx6j_ra0_4` seems to have human annotations at the following: `1, 31, 61, 91, ..., 451, 481, 510, 540`.
        * Is this because of the backward test?
* Image sequence format is `%d.jpg`, not like `%03d.jpg`.
    * That means you can't get the correct order just by sorting them (e.g. `10.jpg` comes before `1.jpg`). Use [natsort](https://natsort.readthedocs.io/en/master/) instead.

## LaSOT [CVPR2019] [:globe_with_meridians:](http://vision.cs.stonybrook.edu/~lasot/) [:memo:](https://arxiv.org/abs/1809.07845) [:octocat:](https://github.com/HengLan/LaSOT_Evaluation_Toolkit)
### Features
* Balanced class distribution (70 object classes x 20 videos/class)
    * Stratified splits of train (80%) and test (20%)
* Offers extra annotations
    * Frame-level binary labels of full occlusion
    * Frame-level binary labels of out-of-view
    * Video-level short lingual descriptions
* Has 2 different evaluation protocols
    * `Protocol I`: All the 1,400 videos are used for evaluation
    * `Protocol II`: All the 280 videos of `testing` are used for evaluation and all the 1,120 videos of `training` are allowed to use for training
* Available for training (if you don't follow `Protocol I`)
* Test set labels are made public
* Long
* Large
### Statistics
* Overall
    | #Videos |    #Frames | #Object <br> classes | #Attr. | Size <br> (GB) | Coordinate <br> origin |
    | ------: | ---------: | -------------------: | -----: | -------------: | ---------------------: |
    |   1,400 |  3,517,342 |                   70 |     14 |            237 |                      1 |
* Split-wise
    | Split    | #Videos |   #Frames | Size <br> (GB) |
    | :------- | ------: | --------: | -------------: |
    | training |   1,120 | 2,831,982 |            188 |
    | testing  |     280 |   685,360 |             48 |
### Caveats
* A few videos have invalid bounding boxes where the target is present (i.e. not occluded nor out-of-view).
    | Video        | Split    | Frame No. |     BBox (x, y, w, h) |
    | :----------- | :------- | --------: | --------------------: |
    | lizard-16    | training |       322 |          (1, 1, 0, 0) |
    | person-7     | training |     2,111 |        (2, 2, -1, -1) |
    | pool-4       | training |       146 |        (1, 1, -1, -1) |
    | tank-17      | training |       627 | (1125, 730, 155, -10) |
    | tiger-6      |  testing |       118 |  (613, 731, 247, -11) |
    | lion-5       |  testing |       553 |        (1, 1, -1, -1) |
    | microphone-6 |  testing |      1108 |          (1, 1, 0, 0) |

## GOT-10k [TPAMI2019] [:globe_with_meridians:](http://got-10k.aitestunion.com/) [:memo:](https://arxiv.org/abs/1810.11981) [:octocat:](https://github.com/got-10k/toolkit)
### Features
* Meant for one-shot evaluation
    * No object class overlap but `person` between the training set and the test set
    * **To evaluate your tracker on GOT-10k, you're only allowed to use the training split of GOT-10k for training**
        * Pre-training on ImageNet is allowed
* Offers extra annotations
    * Video-level labels are: object class, motion class, ...
    * Frame-level labels are: target presence, object visibility at 9 different levels, target being clipped or not
* Available for training
* Sequesters the test set annotations and provides an [evaluation server](http://got-10k.aitestunion.com/submit_instructions)
* Large
### Statistics
* Overall
    | #Videos |   #Frames | #Object <br> classes | #Attr. | Size <br> (GB) | Coordinate <br> origin |
    | ------: | --------: | -------------------: | -----: | -------------: | ---------------------: |
    |   9,695 | 1,447,200 |                  563 |      6 |             75 |                     1? |
* Split-wise
    | Split  | #Videos |   #Frames | #Object <br> classes | Size <br> (GB) |
    | :----- | ------: | --------: | -------------------: | -------------: |
    | Train  |   9,335 | 1,403,359 |                  480 |             72 |
    | Val    |     180 |    21,007 |                  150 |            1.2 |
    | Test   |     180 |    22,834 |                   84 |            1.3 |
### Caveats
* There are neither 10K videos nor 1.5M frames in contrast to authors' claim.
* `Test` has only 180 videos, not 420 videos as the authors say.
* The frame resolution sometimes changes in a video.
    * See https://github.com/got-10k/toolkit/issues/25.
* There are at least 33 ill-annotated videos.
    * Examples:
        * ```
            $ head -5 train/GOT-10k_Train_004419/groundtruth.txt
            371.0000,0.0000,150.0000,0.0000
            352.0000,0.0000,157.0000,0.0000
            346.0000,0.0000,157.0000,0.0000
            333.0000,0.0000,138.0000,0.0000
            320.0000,0.0000,144.0000,0.0000
          ```
        * ```
            $ head -5 train/GOT-10k_Train_005996/groundtruth.txt
            1197.0000,86.0000,374.0000,548.0000
            1223.0000,38.0000,386.0000,89.0000
            1304.0000,0.0000,321.0000,1.0000
            1341.0000,0.0000,293.0000,1.0000
            1353.0000,0.0000,270.0000,1.0000
          ```
* The coordinate origin is not clear.
    * It is supposed to be 1 (see https://github.com/got-10k/toolkit/issues/6) but there are many videos (including 6 `Test` videos) that have `0`'s as the left end or the top end coordinate.
* Some `Train` videos and `Val` videos are made from the same YouTube videos.
    * 107 videos out of the 180 `Val` videos have some overlaps with `Train`.
        * E.g. `GOT-10k_Val_000002` is from `https://youtu.be/kjQGSiLvFac`, which `GOT-10k_Train_000147`, `GOT-10k_Train_000148` and `GOT-10k_Train_000149` are also made from.
    * Authors claim that `Val` is randomly sampled from `Train` but this is not true.
* Watch out for the statement "no overlap between `Train` and `Test`".
    * As is written in the paper, the `person` class shows up in both. The `person` videos are differentiated by motion class.
* [Leaderboard](http://got-10k.aitestunion.com/leaderboard) is fun to watch but...
    * Not sure if every tracker follows the protocol of "Train only on GOT-10k". Take the results with a grain of salt.
* You might not get the dataset link after sending a request with your e-mail address.
    * See https://github.com/got-10k/toolkit/issues/41.
    * I tried 2 different e-mail addresses but none of them worked.
