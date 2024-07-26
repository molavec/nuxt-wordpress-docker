# Nuxt 3 Minimal Starter + Wordpress + Docker

A Docker Development Environment for a Minimal Nuxt 3 conected with Wordpress.  

## Setup

Start containers. 

```bash
npm run docker:dev:up
```
Note: Consider a minute to start systems.

Nuxt: http://localhost:3000
Wordpress: http://localhost:8080

## How it works

Development server is running in conteainers, so `it is not required start dev server`.

Check `.dockerfiles/Dockerfile.dev` nuxt development server image and `.dockerfiles/docker-compose.dev.yaml` for container compose.  

## Install dependencies

To keep correct module versions access to container shell.

```bash
 npm run docker:dev:sh
```
Then, install new packages from conatiner shell

```bash
 npm run docker:dev:sh
```


## Restart development server.

Some alternatives

1. Stop Contianer

```bash
npm run docker:dev:stop nuxt
npm run docker:dev:up nuxt
```
2. Stop server by PID

```bash
npm run docker:dev:sh # Host Terminal: access to container
ps aux #inside container: check process PID
kill -9 pid #inside container: kill process by PID
npm run docker:dev:up nuxt # Host Terminal: restart container 
```


## Docker Logs

```bash
npm run docker:dev:logs --tail nuxt
```


## Troubleshooting

### Wordpress API Access

To ger access to API is necessary setup Permalinks

![permalinks setup](./docs/permalink.jpg)

https://stackoverflow.com/questions/69681308/cannot-access-woocommerce-rest-api-in-wordpress-5-8-1

### NUXT reaload problem docker
Nuxt nitro server has a bug with docker when refresh a file. So, it is necessary remove `/tmp/nitro`. In `package.json`:

```bash
"dev": "rm -rf /tmp/nitro && nuxt dev",
``` 
https://github.com/nuxt/nuxt/issues/13587#issuecomment-1397308015

