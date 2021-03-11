# tracking-sanity
This repository helps you study visual tracking (single & generic object tracking) by taking a close look at recent datasets and trackers.

## Datasets
Tracking datasets out there are not always well-annotated, (often implicitly) different in format and not always mutually exclusive, where you could easily lead yourself astray. In addition to the rough statistics below, we provide more details about the individual datasets in [Datasets.md](Datasets.md).
### [VOT](Datasets.md/#vot-globe_with_meridians-octocat) [:globe_with_meridians:](https://www.votchallenge.net/) [:octocat:](https://github.com/votchallenge/vot-toolkit-python)
* [Short-term challenges](Datasets.md/#vot-short-term-challenges) (Note: the table below is about the public datasets, not about the sequestered datasets)
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
* [Long-term challenges](Datasets.md/#vot-short-term-challenges)
    | Year | #Videos |    #Frames | Size <br> (GB) | Update from previous year               | Links |
    | ---: | ------: | ---------: | -------------: | :-------------------------------------- | :---- |
    | 2018 |      35 |    146,847 |             10 | N/A                                     | [:globe_with_meridians:](https://www.votchallenge.net/vot2018/) [:memo:](http://prints.vicos.si/publications/365) |
    | 2019 |      50 |    215,294 |             16 | 15 videos added                         | [:globe_with_meridians:](https://www.votchallenge.net/vot2019/) [:memo:](http://prints.vicos.si/publications/375) |
    | 2020 |      50 |    215,294 |             16 | Nothing                                 | [:globe_with_meridians:](https://www.votchallenge.net/vot2020/) [:memo:](http://prints.vicos.si/publications/384) |
### Others
| Name                                                                                       | Publication | #Train <br> videos | #Test <br> videos |    #Frames | #Object <br> classes | #Attr. | Size <br> (GB) | Links |
| :----------------------------------------------------------------------------------------- | :---------: | -----------------: | ----------------: | ---------: | -------------------: | -----: | -------------: | :---- |
| [OTB2015](Datasets.md/#otb2015-tpami2015-globe_with_meridians-memo)                        |  TPAMI2015  |                  0 |               100 |     59,040 |                   16 |     11 |            2.7 | [:globe_with_meridians:](http://cvlab.hanyang.ac.kr/tracker_benchmark/datasets.html)       [:memo:](https://faculty.ucmerced.edu/mhyang/papers/pami15_tracking_benchmark.pdf) |
| [TrackingNet](Datasets.md/#trackingnet-eccv2018-globe_with_meridians-memo-octocat)         |   ECCV2018  |             30,132 |               511 | 14,431,266 |                   27 |     15 |          1,088 | [:globe_with_meridians:](https://tracking-net.org/)                                        [:memo:](https://arxiv.org/abs/1803.10794) [:octocat:](https://github.com/SilvioGiancola/TrackingNet-devkit) |
| [LaSOT](Datasets.md/#lasot-cvpr2019-globe_with_meridians-memo-octocat)                     |   CVPR2019  |              1,120 |               280 |  3,517,342 |                   70 |     14 |            237 | [:globe_with_meridians:](http://vision.cs.stonybrook.edu/~lasot/)                          [:memo:](https://arxiv.org/abs/1809.07845) [:octocat:](https://github.com/HengLan/LaSOT_Evaluation_Toolkit) |
| [GOT-10k](Datasets.md/#got-10k-tpami2019-globe_with_meridians-memo-octocat)                |  TPAMI2019  |              9,335 |               180 |  1,447,200 |                  563 |      6 |             75 | [:globe_with_meridians:](http://got-10k.aitestunion.com/)                                  [:memo:](https://arxiv.org/abs/1810.11981) [:octocat:](https://github.com/got-10k/toolkit) |
| [LaSOT-extension](Datasets.md/#lasot-extension-ijcv2021-globe_with_meridians-memo-octocat) |   IJCV2021  |                  0 |               150 |    359,169 |                   15 |     14 |             60 | [:globe_with_meridians:](http://vision.cs.stonybrook.edu/~lasot/)                          [:memo:](https://arxiv.org/abs/2009.03465) [:octocat:](https://github.com/HengLan/LaSOT_Evaluation_Toolkit) |

## Trackers
Trackers out there are often trained, tested or evaluated in different ways, which makes a fair comparison hard. Here, we not only keep track of the state-of-the-art but also try to clarify the way the results are produced, based on public papers, code and discussion. More details will be provided in [Trackers.md](Trackers.md).
