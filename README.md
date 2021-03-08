# tracking-sanity
This repository helps you study visual tracking (single & generic object tracking) by taking a close look at recent datasets and trackers.

## Datasets
Tracking datasets out there are huge, (often implicitly) different in format and not always well-annotated, where you could easily lead yourself astray. In addition to the rough statistics below, we provide more details about the individual datasets in [Datasets.md](Datasets.md).
### VOT
Coming soon!
### Others
| Name            | Publication | #Train <br> videos | #Test <br> videos |    #Frames | #Object <br> classes | #Attr. | Size <br> (GB) | Links |
| :-------------- | :---------: | -----------------: | ----------------: | ---------: | -------------------: | -----: | -------------: | :---- |
| OTB2015         |  TPAMI2015  |                  0 |               100 |     59,040 |                   16 |     11 |            2.7 | [:globe_with_meridians:](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html)       [:memo:](https://faculty.ucmerced.edu/mhyang/papers/pami15_tracking_benchmark.pdf) |
| TrackingNet     |   ECCV2018  |             30,132 |               511 | 14,431,266 |                   27 |     15 |          1,088 | [:globe_with_meridians:](https://tracking-net.org/)                                        [:memo:](https://arxiv.org/abs/1803.10794) [:octocat:](https://github.com/SilvioGiancola/TrackingNet-devkit) |

## Trackers
Trackers out there are often trained, tested or evaluated in different ways, which makes a fair comparison hard. Here, we not only keep track of the state-of-the-art but also try to clarify the way the results are produced, based on public papers, code and discussion. More details will be provided in [Trackers.md](Trackers.md).
