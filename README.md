# tracking-sanity
This repository helps you study visual tracking (single & generic object tracking) by taking a close look at recent datasets and trackers.

## Datasets
Tracking datasets out there are huge, (often implicitly) different in format and not always well-annotated, where you could easily lead yourself astray. In addition to the rough statistics below, we provide more details about the individual datasets in [Datasets.md](Datasets.md).
### VOT
Coming soon!
### Others
| Name                                                                               | Publication | #Train <br> videos | #Test <br> videos |    #Frames | #Object <br> classes | #Attr. | Size <br> (GB) | Links |
| :--------------------------------------------------------------------------------- | :---------: | -----------------: | ----------------: | ---------: | -------------------: | -----: | -------------: | :---- |
| [OTB2015](Datasets.md/#otb2015-tpami2015-globe_with_meridians-memo)                |  TPAMI2015  |                  0 |               100 |     59,040 |                   16 |     11 |            2.7 | [:globe_with_meridians:](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html)       [:memo:](https://faculty.ucmerced.edu/mhyang/papers/pami15_tracking_benchmark.pdf) |
| [TrackingNet](Datasets.md/#trackingnet-eccv2018-globe_with_meridians-memo-octocat) |   ECCV2018  |             30,132 |               511 | 14,431,266 |                   27 |     15 |          1,088 | [:globe_with_meridians:](https://tracking-net.org/)                                        [:memo:](https://arxiv.org/abs/1803.10794) [:octocat:](https://github.com/SilvioGiancola/TrackingNet-devkit) |
| [LaSOT](Datasets.md/#lasot-cvpr2019-globe_with_meridians-memo-octocat)             |   CVPR2019  |              1,120 |               280 |  3,517,342 |                   70 |     14 |            237 | [:globe_with_meridians:](http://vision.cs.stonybrook.edu/~lasot/)                          [:memo:](https://arxiv.org/abs/1809.07845) [:octocat:](https://github.com/HengLan/LaSOT_Evaluation_Toolkit) |
| [GOT-10k](Datasets.md/#got-10k-tpami2019-globe_with_meridians-memo-octocat)           |  TPAMI2019  |              9,335 |               180 |  1,447,200 |                  563 |      6 |             75 | [:globe_with_meridians:](http://got-10k.aitestunion.com/)                                  [:memo:](https://arxiv.org/abs/1810.11981) [:octocat:](https://github.com/got-10k/toolkit) |

## Trackers
Trackers out there are often trained, tested or evaluated in different ways, which makes a fair comparison hard. Here, we not only keep track of the state-of-the-art but also try to clarify the way the results are produced, based on public papers, code and discussion. More details will be provided in [Trackers.md](Trackers.md).
