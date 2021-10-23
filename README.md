# Project

> This repo has been populated by an initial template to help get you started. Please
> make sure to update the content to build a great experience for community-building.

As the maintainer of this project, please make a few updates:

- Improving this README.MD file to provide a great experience
- Updating SUPPORT.MD with content about this project's support experience
- Understanding the security reporting process in SECURITY.MD
- Remove this section from the README

## Introduction

Bing Maps is releasing open building footprints datasets in South America countries. We have detected 44.5 million buildings on recently updated Maxar imagery that covers around 61% (258 million) of the South American population. The data is freely available for download and use under applicable license.
![](/images/image009.png)![](/images/image011.png)


## License
This data is licensed by Microsoft under the [Open Data Commons Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/).

## FAQ
### What does the data include?
44,495,865‬ building footprint polygon geometries in South America in GeoJSON format. You may download the data in GeoJSON format here:

https://minedbuildings.blob.core.windows.net/southamerica/SouthAmericaPolygons.zip


### What is the GeoJSON format?
GeoJSON is a format for encoding a variety of geographic data structures. 
For intensive documentation and tutorials, refer to [GeoJson blog](http://geojson.org/).

### Why is the data being released?
Microsoft has a continued interest in supporting a thriving OpenStreetMap ecosystem.

### Should we import the data into OpenStreetMap?
Maybe. Never overwrite the hard work of other contributors or blindly import data into OSM without first checking the local quality. While our metrics show that this data meets or exceeds the quality of hand-drawn building footprints, the data does vary in quality from place to place, between rural and urban, mountains and plains, and so on. Inspect quality locally and discuss an import plan with the community. Always follow the [OSM import community guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines).

### Will the data be used or made available in larger OpenStreetMap ecosystem?
Yes. Currently Microsoft Open Buildings dataset is used in ml-enabler for task creation. You can try it out at [AI assisted Tasking Manager](https://tasks-assisted.hotosm.org/). The data will also be made avaialble in Facebook [RapiD](https://mapwith.ai/rapid#background=Bing&disable_features=boundaries&map=2.00/0.0/0.0).

### What is the creation process for this data?
The building extraction is done in two stages:
1.	Semantic Segmentation – Recognizing building pixels on the aerial image using DNNs
2.	Polygonization – Converting building pixel blobs into polygons

#### Stage1: Semantic Segmentation
![](/images/segmentation.jpg)

#### Stage 2: Polygonization
![](/images/polygonization.jpg)

### Is there any technical improvement used in this round than previous ones? 
Our building extraction model for South America was tuned using only unsupervised training (no training labels), specifically style-transfer and self-training techniques we have developed internally.

### Evaluation set metrics
The evaluation metrics are computed on the set of 2500 building labels.

Building match metrics on the evaluation set:

| Metric | Value |
| --- | :---: |
| Precision | 96.0% |
| Recall | 68.7% |

We track following metrics to measure the quality of matched buildings in the evaluation set:
1. Intersection over Union – This is a standard metric measuring the overlap quality against the labels
2. Dominant angle rotation error – This measures the polygon rotation deviation

| IoU | Rotation error [deg] |
| :---: | :---: |
|  0.69 | 6.9 |

![](/images/bldgmetrics.JPG)

### False positive ratio in the corpus

We estimate ~1.5% false postive ratio in 1000 randomly sampled buildings from the entire output corpus.

### Evaluation recall error space examples


In highly urban areas problems and regression start to occur, driving the following metrics down: recall, IoU, and average rotation angle. The most frequent problem is a large number of false negatives caused by a lack of prediction granularity, like in the image below. 
![](/images/urban.png)

Here is a larger example in urban areas. Our model that splits connected buildings could not adapt without new domain training data. I would say that even training with new data is very unlikely to produce better building splits since the imagery quality in combination with high off-nadir angle makes the whole task extremely hard.

![](/images/urban_large.png)
Some areas have a high off-nadir angle, which results in wrong footprints: 
![](/images/off_nadir.png)

### What is the vintage of this data?
Vintage of extracted building footprints depends on vintage of the underlying imagery. Bing Imagery is a composite of multiple sources, therefore it is difficult to know the exact dates for individual pieces of data. However we believe the vintage is anywhere from 2013 to 2018, with majority being from 2018.

### How good is the data?
Our metrics show that in the vast majority of cases the quality is at least as good as data hand digitized buildings in OpenStreetMap. It is not perfect, particularly in dense urban areas but it provides good recall in rural areas.

### What is the coordinate reference system?
EPSG: 4326

### Will there be more data coming for other geographies?
Maybe. This is a work in progress.

<br>

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Legal Notices

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found [here](http://go.microsoft.com/fwlink/?LinkID=254653).

Privacy information can be found [here](https://privacy.microsoft.com/en-us/).

Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
