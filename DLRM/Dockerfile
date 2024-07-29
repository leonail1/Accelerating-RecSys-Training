# 使用一个较新的基础镜像来避免依赖问题
ARG FROM_IMAGE_NAME=pytorch/pytorch:1.3-cuda10.1-cudnn7-runtime
FROM ${FROM_IMAGE_NAME}

# 更新包列表并安装 cmake 和 protobuf 编译器
RUN apt-get update && apt-get install -y cmake protobuf-compiler

# 添加 requirements.txt
ADD requirements.txt .

# 安装指定版本的 protobuf 以确保兼容性
RUN pip install protobuf==3.19.6

# 安装 Python 依赖，并明确指定不使用 PEP 517
RUN pip install --no-use-pep517 onnx==1.8.1
RUN pip install -r requirements.txt

# 安装特定版本的 torch
RUN pip install torch==1.3.1

# 设置工作目录
WORKDIR /code

# 将当前目录内容添加到容器中
ADD . .
