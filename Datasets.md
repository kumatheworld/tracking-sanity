# Datasets
## OTB2015 [:globe_with_meridians:](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html) [:memo:](https://faculty.ucmerced.edu/mhyang/papers/pami15_tracking_benchmark.pdf)
### Features
Coming soon!
### Statistics
Coming soon!
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
