# Auto-GPT in Docker

This repo will help you setup Auto GPT in an easy to use Docker container.

## Prerequisites

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
2. Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
3. Obtain an [OpenAI key](https://platform.openai.com/account/api-keys).
4. *(Optional)* Install [Visual Studio Code](https://code.visualstudio.com/Download).
3. Clone this repo.

## Build the containers

1. Copy the `docker-compose.yaml.template` file to `docker-compose.yaml`
2. Edit the `docker-compose.yaml` file and add your OpenAI API key
3. Choose a password for your `redis` server and add it to both placeholders
4. Open a terminal and navigate to the directory you cloned this repo into (or power-shell, if you're on Windows)
5. Type the following command to build:
    ```bash
    docker compose up -d
    ```

## Run auto-gpt

1. *(Optional)* Edit the `files/ai_settings.yml` file to configure the bot.
2. Start the bot by running
    ```bash
    docker compose run -T auto-gpt ./run.sh
