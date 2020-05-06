# docker-keras - Keras in Docker with Python 3 and TensorFlow on CPU with Jupyter

FROM ubuntu:18.04
MAINTAINER Kuoying Wang [stu93303148@gmail.com]

# install debian packages
ENV DEBIAN_FRONTEND noninteractive

# install python3.6
RUN apt-get update && apt-get install -y software-properties-common && add-apt-repository ppa:deadsnakes/ppa && \
    apt-get update && apt-get install -y python3.6 python3.6-dev python3-pip
RUN ln -sfn /usr/bin/python3.6 /usr/bin/python3 && ln -sfn /usr/bin/python3 /usr/bin/python && ln -sfn /usr/bin/pip3 /usr/bin/pip

# install others
RUN apt-get update -qq \
 && apt-get install --no-install-recommends -y \
    # install essentials
    build-essential \
    g++ \
    git \
    openssh-client \
    python3-pip \
    python3-setuptools \
    python3-virtualenv \
    python3-wheel \
    pkg-config \
    # requirements for numpy
    libopenblas-base \
    python3-numpy \
    python3-scipy \
    # requirements for keras
    python3-h5py \
    python3-yaml \
    python3-pydot \
    # covid-chestxray-dataset
    python3-lxml \
    python3-pandas \
    wget \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# install plugins
RUN pip3 --no-cache-dir install -U numpy==1.16.0
RUN pip3 --no-cache-dir install -U pandas==0.25.3
RUN pip3 --no-cache-dir install -U dicom2nifti==2.2.7
RUN pip3 --no-cache-dir install -U scikit-image
RUN pip3 --no-cache-dir install -U dicom
RUN pip3 --no-cache-dir install -U matplotlib
RUN pip3 --no-cache-dir install -U opencv-python==4.2.0.34
RUN pip3 --no-cache-dir install -U ipykernel
RUN pip3 --no-cache-dir install -U scikit-learn
RUN pip3 --no-cache-dir install -U h5py==2.8.0rc1

# install tensorflow
RUN pip3 --no-cache-dir install tensorflow==1.13.2

# adding jupyter stuff
RUN pip3 --no-cache-dir install \
    jupyter \
    ipython \
    ipykernel \
    # data analysis (Python 3)
    pandas \
    scikit-learn \
    statsmodels \
    matplotlib \
    mpld3 \
 && python3 -m ipykernel.kernelspec \
 && ipython kernel install

# install keras
ARG KERAS_VERSION=2.2.4
ENV KERAS_BACKEND=tensorflow
RUN pip3 --no-cache-dir install --no-dependencies git+https://github.com/fchollet/keras.git@${KERAS_VERSION}

COPY jupyter_config.py /root/.jupyter/
COPY jupyter_launch.sh /
RUN chmod +x /jupyter_launch.sh

EXPOSE 8888

WORKDIR /srv/

CMD ["/jupyter_launch.sh"]
