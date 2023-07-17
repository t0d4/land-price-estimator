# Land price dataset preparation

`CHIKA.ipynb` reads a CSV file containing land price information of various areas distributed by Japanese Ministry of Land, Infrastructure, Transport and Tourism [here](https://nlftp.mlit.go.jp/ksj/gml/datalist/KsjTmplt-L01-v3_1.html), and retrieves satellite image of the area using `leafmap` library. Satellite images are saved in TIFF format.