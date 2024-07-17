# Exemplo

Aplicativo usado para workshops e para testes de infraestrutura.

## Setup Local

### Como "build" as imagens Docker

```bash
docker compose --file docker-compose.local.yml build
```

### Como rodar o linter

O linter `ruff` serve para conferir se o estilo e a formatação estão OK.

```bash
docker compose --file docker-compose.local.yml run --rm django ruff check
```

### Como rodar os testes

```bash
docker compose --file docker-compose.local.yml run --rm django coverage run -m pytest
```

### Como armazenar as imagens no DockerHub

Caso o comando vá ser utilizado em um computador pessoal, substituir "SUBSTITUIR_POR_USUARIO" pelo seu usuário do DockerHub, e substituir "SUBSTITUIR_POR_SENHA" pela sua senha.

Caso o comando vá ser rodado em uma pipeline de CI, substituir por variáveis adequadas. Por exemplo, em um workflow do GitHub, o nome de usuário poderia ser especificado assim: `${{ secrets.DOCKERHUB_USERNAME }}`.

#### Escolher nome da imagem docker

O comando `docker tag` é utilizado para dar um novo "nome" a uma imagem Docker. O foco deste exemplo não é explorar os detalhes desse "nome", porém é possível especificar a qual usuário do DockerHub (Docker Registry escolhido para o exemplo) a imagem Docker pertence.

```bash
docker tag exemplo_local_django SUBSTITUIR_POR_USUARIO/exemplo_local_django:latest
```

#### Faz login no DockerHub

```bash
docker login --username SUBSTITUIR_POR_USUARIO --password SUBSTITUIR_POR_SENHA
```

#### Armazena a imagem docker no DockerHub

Similar ao `git push`, só que usado para imagens Docker.

```bash
docker push SUBSTITUIR_POR_USUARIO/exemplo_local_django:latest
```

### Como executar o aplicativo

```bash
docker compose --file docker-compose.local.yml up
```

## Setup de Produção

### Como "build" as imagens Docker

```bash
docker compose --file docker-compose.production.yml build
```

### Como armazenar as imagens no DockerHub

Caso o comando vá ser utilizado em um computador pessoal, substituir "SUBSTITUIR_POR_USUARIO" pelo seu usuário do DockerHub, e substituir "SUBSTITUIR_POR_SENHA" pela sua senha.

Caso o comando vá ser rodado em uma pipeline de CI, substituir por variáveis adequadas. Por exemplo, em um workflow do GitHub, o nome de usuário poderia ser especificado assim: `${{ secrets.DOCKERHUB_USERNAME }}`.

```bash
docker tag exemplo_production_django SUBSTITUIR_POR_USUARIO/exemplo_production_django:latest
```

#### Faz login no DockerHub

```bash
docker login --username SUBSTITUIR_POR_USUARIO --password SUBSTITUIR_POR_SENHA
```

#### Armazena a imagem docker no DockerHub

```bash
docker push SUBSTITUIR_POR_USUARIO/exemplo_production_django:latest
```

### Como executar o aplicativo

TODO
