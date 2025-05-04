# syntax=docker/dockerfile:1

FROM pytorch/pytorch:2.7.0-cuda12.6-cudnn9-devel

# CMD python --version

# ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt upgrade -y
# RUN apt install -y software-properties-common
# RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt install -y build-essential python3-pip python3-dev python3.10-dev git curl

RUN pip install comfy-cli

WORKDIR /app
RUN comfy --workspace=comfy --skip-prompt install --nvidia

RUN git clone https://github.com/thu-ml/SageAttention.git
WORKDIR /app/SageAttention
RUN python setup.py install
WORKDIR /app

# RUN comfy --workspace=comfy node install-deps --deps=~/comfy-cli-files/wan-flf_api-deps.json
CMD comfy --workspace=comfy launch -- --listen 0.0.0.0


# # COPY requirements.txt .

# # RUN python -m venv venv
# # # RUN venv/bin/pip install -r requirements.txt

# RUN pip install 'xformers>=0.0.22' torch==2.2.2 torchvision==0.17.2 torchaudio==2.2.2 --index-url https://download.pytorch.org/whl/cu121
# RUN pip install 'triton>=2.1.0'
# RUN pip install 'diffusers>=0.19.3'
# RUN pip install tomesd
# RUN pip install nest-asyncio aiofiles fastapi "uvicorn[standard]" python-multipart
# RUN pip install accelerate
# RUN pip install transformers

# COPY stable_fast-1.0.4.dev20240327+torch221cu121-cp310-cp310-manylinux2014_x86_64.whl .
# RUN pip install stable_fast-1.0.4.dev20240327+torch221cu121-cp310-cp310-manylinux2014_x86_64.whl

# # COPY stable_fast-0.0.15+torch210cu118-cp39-cp39-manylinux2014_x86_64.whl .
# # RUN venv/bin/pip install 'torch==2.1.0' torchvision --index-url https://download.pytorch.org/whl/cu118
# # RUN venv/bin/pip install xformers --index-url https://download.pytorch.org/whl/cu118
# # RUN venv/bin/pip install stable_fast-0.0.15+torch210cu118-cp39-cp39-manylinux2014_x86_64.whl  --index-url https://download.pytorch.org/whl/cu118
# # RUN venv/bin/pip install 'diffusers>=0.19.3'

# COPY hf_downloader.py .
# # RUN venv/bin/python hf_downloader.py "runwayml/stable-diffusion-v1-5" "sd15"
# # RUN venv/bin/python hf_downloader.py "segmind/SSD-1B" "ssd1b"
# # RUN venv/bin/python hf_downloader.py "stabilityai/stable-diffusion-xl-base-1.0" "sdxl"
# # RUN python hf_downloader.py "stabilityai/sd-turbo" "sd21"
# RUN python hf_downloader.py "stabilityai/sdxl-turbo" "sdxl"

# COPY daedalus.py .
# COPY server.py .

# CMD python server.py
# CMD python -m uvicorn server:app --host 0.0.0.0
