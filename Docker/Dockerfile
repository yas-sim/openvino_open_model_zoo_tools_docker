FROM openvino/ubuntu24_dev:2024.6.0

WORKDIR /home/openvino

USER root

RUN python3 -m pip install -U pip && \
    pip3 install -U setuptools wheel
RUN pip3 install openvino-dev==2024.6.0 tf_keras

USER openvino

WORKDIR /home/openvino/models

CMD [ "/usr/bin/bash" ]