# Docker compose skeleton for the telegram bots written in go
This is a skeleton for the telegram bots written in go. It uses docker-compose to run the bot in the docker container. It also uses the Caddy http server to provide the https connection to the telegram bot api.

## Prerequisites
It is assumed that you have the dns name set up. 
I will implement the dns name setup (at least for Cloudflare) in the future.

## Usage
```
docker-compose --env-file envs/<yourbotenv> up -d
```
