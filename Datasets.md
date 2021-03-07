# Datasets
## OTB2015 [TPAMI2015] [:globe_with_meridians:](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html) [:memo:](https://faculty.ucmerced.edu/mhyang/papers/pami15_tracking_benchmark.pdf)
### Features
* Test-only (not for training)
* Small
* Easy
### Statistics
| #Videos | #Frames |#Object <br> classes | #Attributes | Size <br> (GB) |  Coordinate <br> origin |
| ------: | ------: |-------------------: | ----------: | -------------: |  ---------------------: |
|     100 |  59,040 |                  16 |          11 |            2.7 |                       ? |
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
