# syntax=docker/dockerfile:1

FROM aarondot/comfy-base:latest

RUN apt-get update && apt-get install -y curl wget
WORKDIR /app

RUN wget -O comfy/models/diffusion_models/Wan2_1-FLF2V-14B-720P_fp8_e4m3fn.safetensors https://huggingface.co/Kijai/WanVideo_comfy/resolve/main/Wan2_1-FLF2V-14B-720P_fp8_e4m3fn.safetensors?download=true
RUN wget -O comfy/models/text_encoders/umt5-xxl-enc-fp8_e4m3fn.safetensors https://huggingface.co/Kijai/WanVideo_comfy/resolve/main/umt5-xxl-enc-fp8_e4m3fn.safetensors?download=true
RUN wget -O comfy/models/vae/Wan2_1_VAE_bf16.safetensors https://huggingface.co/Kijai/WanVideo_comfy/resolve/main/Wan2_1_VAE_bf16.safetensors?download=true
RUN wget -O comfy/models/clip_vision/open-clip-xlm-roberta-large-vit-huge-14_visual_fp16.safetensors https://huggingface.co/Kijai/WanVideo_comfy/resolve/main/open-clip-xlm-roberta-large-vit-huge-14_visual_fp16.safetensors?download=true

COPY wan-flf_api-deps.json .

RUN comfy --workspace=comfy node install-deps --deps=wan-flf_api-deps.json
RUN comfy --workspace=comfy node install ComfyUI-WanVideoWrapper

COPY start_flf.sh .

CMD bash start_flf.sh

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
