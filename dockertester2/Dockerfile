# Use CUDA 11.2 base image as specified in the installation guide
FROM runpod/pytorch:2.4.0-py3.11-cuda12.4.1-devel-ubuntu22.04


# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Add NVIDIA's GPG key manually
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC

# Run system updates and install required packages including zlib1g-dev
RUN apt-get update && \
    apt-get install -y \
    git \
    python3-pip \
    gcc \
    g++ \
    zlib1g-dev \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /paddle

# Install PaddlePaddle GPU version
RUN pip3 install --no-cache-dir paddlepaddle-gpu==2.6.0

# Clone ArcFace-paddle repository
# RUN git clone https://github.com/PaddlePaddle/PaddleDetection.git

# Install PaddleDetection requirements
# WORKDIR /paddle/PaddleDetection
# RUN pip3 install --no-cache-dir -r requirements.txt

# Verify PaddlePaddle installation
RUN python3 -c "import paddle; paddle.utils.run_check(); print(paddle.__version__)"

# Set default command
CMD ["/bin/bash"]