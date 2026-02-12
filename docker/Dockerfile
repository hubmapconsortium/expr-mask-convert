FROM continuumio/anaconda3:2024.10-1

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
 && apt-get -y install \
    build-essential \
    libgl1-mesa-glx \
 && rm -rf /var/cache/apt/*

WORKDIR /opt
RUN python3 -m pip install --upgrade pip setuptools wheel

COPY docker/requirements.txt /opt
RUN python3 -m pip install -r /opt/requirements.txt \
 && rm -rf /root/.cache/pip

RUN python3 -m pip install -U numexpr bottleneck

COPY bin /opt

CMD ["/bin/bash"]
