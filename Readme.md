# Docker container for OpenVINO Model Zoo tools (omz_downloader, omz_converter, omz_data_downloader, omz_info_dumper)

This project provides a Dockerfile to build a Docker image to run Intel's Open Model Zoo support tools easily.

### Building image and preparation
```sh
cd Docker
docker build -t omz:2024.6.0 .
docker tag omz:2024.6.0 omz:latest
makdir -p models
# To make the Docker container user (openvino) is able to write the files in the directory
chmod 777 models
```

### Usage - Downloading and converting model
The downloaded models will be found in the `./models` directory after running following commands.
```sh
docker run --rm -v ./models:/home/openvino/models omz omz_downloader --name yolo-v3-onnx
docker run --rm -v ./models:/home/openvino/models omz omz_converter --name yolo-v3-onnx --precisions FP16
```

### Usage - Display the names of all supported models
You can check which models are supported by the tool with following command.
```sh
docker run --rm -v ./models:/home/openvino/models omz omz_downloader --print_all
```

### Usage - Work in the container console.
You can work in the container terminal to do multiple steps.
```sh
docker run --rm -it -v ./models:/home/openvino/models omz
```

### Reference
- [OpenVINO Open Model Zoo (OMZ)](https://github.com/openvinotoolkit/open_model_zoo)
- List of available models at OMZ
    - [Intel pre-trained models](https://github.com/openvinotoolkit/open_model_zoo/blob/master/models/intel/index.md)
    - [Public pre-trained models](https://github.com/openvinotoolkit/open_model_zoo/blob/master/models/public/index.md)
- [OMZ downloader tools](https://github.com/openvinotoolkit/open_model_zoo/blob/master/tools/model_tools/README.md)

You can use NNCF to compress/quantize the DL models.
- [Intel Neural Network Compression Framework (NNCF)](https://github.com/openvinotoolkit/nncf)