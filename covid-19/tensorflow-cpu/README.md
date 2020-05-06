# TensorFlow-Keras-Jupyter-Python3 on CPU

### Building
Clone the repo and build the docker image from the Dockerfile:
```
docker build -t kerascpu .
```

When it is complete, you can run the image by running:
```
docker run -p 8888:8888 kerascpu
```

### Reference

Implementation

[COVID-Net](https://github.com/lindawangg/COVID-Net)  
[Docker-Keras-CPU](https://github.com/boxxa/Docker-Keras-CPU) 

The current COVIDx dataset is constructed by the following open source chest radiography datasets:

- https://github.com/ieee8023/covid-chestxray-dataset
- https://github.com/agchung/Figure1-COVID-chestxray-dataset
- https://www.kaggle.com/c/rsna-pneumonia-detection-challenge  
