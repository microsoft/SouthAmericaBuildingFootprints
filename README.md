## Introduction

Bing Maps is releasing open building footprints dataset for countries in South America. We have detected 44.5 million buildings from Maxar imagery collected between 2020 and 2021 for regions encompassing approximately 50% of the South American population. The data is freely available for download and use under applicable license.

![sample footprints](/images/image009.png)

### Regions included 

![building regions](/images/image011.png)


## License
This data is licensed by Microsoft under the [Open Data Commons Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/).

## FAQ
### What does the data include?
44,495,865 building footprint polygon geometries located in South America in GeoJSON format. You may download the data in GeoJSON format here:

| Location | Count | Link | Size (Compressed) |
| :---: | :---: | :---: |:---: |
| Continent | 44,495,865 | [SouthAmericaPolygons.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/SouthAmericaPolygons.zip) | 15GB |
| Argentina | 3,427,787 | [Argentina.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Argentina.geojsonl.zip) | 323MB |
| Bolivia | 1,015,151 | [Bolivia.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Bolivia.geojsonl.zip) | 82MB |
| Brazil | 18,711,536 | [Brazil.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Brazil.geojsonl.zip) | 1.6GB |
| Chile | 2,208,744 | [Chile.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Chile.geojsonl.zip) | 187MB |
| Colombia | 6,083,821 | [Colombia.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Colombia.geojsonl.zip) | 482MB |
| Ecuador | 3,674,190 | [Ecuador.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Ecuador.geojsonl.zip) | 287MB |
| Guyana | 3,339 | [Guyana.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Guyana.geojsonl.zip) | 236KB |
| Paraguay | 990,756 | [Paraguay.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Paraguay.geojsonl.zip) | 73MB |
| Peru | 1,710,431 | [Peru.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Peru.geojsonl.zip) | 144MB |
| Uruguay | 2,656 | [Uruguay.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Uruguay.geojsonl.zip) | 200KB |
| Venezuela | 6,572,969 | [Venezuela.geojsonl.zip](https://minedbuildings.z5.web.core.windows.net/legacy/southamerica/Venezuela.geojsonl.zip) | 497MB |


### What is the GeoJSON format?
GeoJSON is a format for encoding a variety of geographic data structures. 
For intensive documentation and tutorials, refer to [GeoJson blog](http://geojson.org/).

### Why is the data being released?
Microsoft has a continued interest in supporting a thriving OpenStreetMap ecosystem.

### Should we import the data into OpenStreetMap?
Maybe. Never overwrite the hard work of other contributors or blindly import data into OSM without first checking the local quality. While our metrics show that this data meets or exceeds the quality of hand-drawn building footprints, the data does vary in quality from place to place, between rural and urban, mountains and plains, and so on. Inspect quality locally and discuss an import plan with the community. Always follow the [OSM import community guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines).

### Will the data be used or made available in larger OpenStreetMap ecosystem?
Yes. Currently Microsoft Open Buildings dataset is used in ml-enabler for task creation. You can try it out at [AI assisted Tasking Manager](https://tasks-assisted.hotosm.org/). The data will also be made available in Facebook [RapiD](https://mapwith.ai/rapid#background=Bing&disable_features=boundaries&map=2.00/0.0/0.0).

### How did we create the data?
The building extraction is done in two stages:
1.	Semantic Segmentation – Recognizing building pixels on an aerial image using deep neural networks (DNNs)
2.	Polygonization – Converting building pixel detections into polygons

#### Stage1: Semantic Segmentation
![](/images/segmentation.jpg)

#### Stage 2: Polygonization
![](/images/polygonization.jpg)

### Were there any modeling improvements used for this release? 
Our building extraction model for South America was tuned using only unsupervised training (no training labels), specifically style-transfer and self-training techniques that we have developed internally.

### Evaluation set metrics
The evaluation metrics are computed on the set of 2,500 building labels.

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

We estimate ~1.5% false positive ratio in 1,000 randomly sampled buildings from the entire output corpus.


### What is the vintage of this data?
Vintage of extracted building footprints depends on vintage of the underlying imagery. Underlying imagery is from Maxar between 2020 and 2021.

### How good is the data?
Our metrics show that in the vast majority of cases the quality is at least as good as hand digitized buildings in OpenStreetMap. It is not perfect, particularly in dense urban areas but it provides good recall in rural areas.

### What is the coordinate reference system?
EPSG: 4326

### Will there be more data coming for other geographies?
Maybe. This is a work in progress. Also, check out our other building releases!
*  [US](https://github.com/microsoft/USBuildingFootprints)
* [Australia](https://github.com/microsoft/AustraliaBuildingFootprints)
* [Canada](https://github.com/microsoft/CanadianBuildingFootprints)
* [Uganda and Tanzania](https://github.com/microsoft/Uganda-Tanzania-Building-Footprints)

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
