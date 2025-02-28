# Docker container for OpenVINO Model Zoo tools (omz_downloader, omz_converter, omz_data_downloader, omz_info_dumper)

This project provides a Dockerfile to build a Docker image to run Intel's Open Model Zoo support tools easily.

### Building image and preparation
```sh
cd Docker
docker build -t omz:latest .
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
