# Datasets
* VOT
* Others
    * [OTB2015](#otb2015-tpami2015-globe_with_meridians-memo)
    * [TrackingNet](#trackingnet-eccv2018-globe_with_meridians-memo-octocat)
    * [LaSOT](#lasot-cvpr2019-globe_with_meridians-memo-octocat)
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
* Sequesters the test set and provides an [evaluation server](http://eval.tracking-net.org/web/challenges/challenge-page/39/overview)
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
