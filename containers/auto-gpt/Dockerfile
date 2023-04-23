FROM python:3.10.11-slim

# Installing in root's home
WORKDIR /root/auto-gpt

# Prerequisites: 
# wget to download the latest stable 
# git, as it's required by Auto-GPT
# and sed to pass the OpenAPI key
RUN apt update && apt install wget sed git -y

# Download the latest stable version
ARG VERSION='0.2.2'
RUN wget https://github.com/Significant-Gravitas/Auto-GPT/archive/refs/tags/v${VERSION}.tar.gz && \
    tar -xf v${VERSION}.tar.gz && \
    cp -r ./Auto-GPT-${VERSION}/. ./ && \
    rm v${VERSION}.tar.gz && \
    rm -rf Auto-GPT-${VERSION} && \
    pip install -r requirements.txt

# Set the OpenAPI key
ARG OPENAPI_KEY='NOT_SET'
RUN cp .env.template .env && \
    sed -i "s/OPENAI_API_KEY=your-openai-api-key/OPENAI_API_KEY=${OPENAPI_KEY}/g" .env && \
    sed -s "s/# MEMORY_BACKEND=local/MEMORY_BACKEND=local/g" .env && \
    sed -s "s/# REDIS_HOST=localhost/REDIS_HOST=redis/g" .env && \
    sed -s "s/# REDIS_PORT=6379/REDIS_PORT=6379/g" .env && \
    sed -s "s/# REDIS_PASSWORD=/REDIS_PASSWORD=${REDIS_PASSWORD}/g" .env && \
    sed -s "s/# WIPE_REDIS_ON_START=True/WIPE_REDIS_ON_START=False/g" .env

CMD ["python3"]