# EBAC – Módulo 18: primeira imagem no Docker Hub

Exercício do curso **Profissão: Desenvolvedor Full Stack Python** (EBAC).

Autor: **Pedro Badaró Ferreira** ([@Peobadaro](https://github.com/Peobadaro))

Imagem no Docker Hub: **[peobadaro/ebac-hello-world](https://hub.docker.com/r/peobadaro/ebac-hello-world)**

## Dockerfile

```dockerfile
FROM busybox
CMD ["echo", "Olá, EBAC! Hello World do Pedro Badaró Ferreira - Módulo 18 (Docker)"]
```

## Passo a passo (o mesmo da aula)

```bash
docker build -t peobadaro/ebac-hello-world:1.0 .      # monta a imagem no diretório atual (.)
docker tag peobadaro/ebac-hello-world:1.0 peobadaro/ebac-hello-world:latest
docker run --rm peobadaro/ebac-hello-world:1.0        # testa
docker login                                           # sem login o push dá erro de permissão
docker push peobadaro/ebac-hello-world:1.0
docker push peobadaro/ebac-hello-world:latest
```

## Rodar a imagem publicada

```bash
docker run --rm peobadaro/ebac-hello-world:1.0
```

## Automação

O workflow `.github/workflows/docker-publish.yml` faz o mesmo `build`, `run` e `push` no GitHub Actions, usando os secrets `DOCKERHUB_USERNAME` e `DOCKERHUB_TOKEN`.
