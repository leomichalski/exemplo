# Exemplo

## Comandos de cada etapa

### Etapa Build

```bash
docker compose --file docker-compose.local.yml build
```

### Etapa Lint

```bash
docker compose --file docker-compose.local.yml run --no-deps --rm django ruff check
```

### Etapa Teste

```bash
docker compose --file docker-compose.local.yml run --rm django coverage run -m pytest
```

### Etapa Push

Caso o comando vá ser utilizado em um computador pessoal, substituir "SUBSTITUIR_POR_USUARIO" pelo seu usuário do DockerHub, e substituir "SUBSTITUIR_POR_SENHA" pela sua senha.

Caso o comando vá ser rodado em uma pipeline de CI, substituir por variáveis adequadas. Por exemplo, em um workflow do GitHub, o nome de usuário poderia ser especificado assim: `${{ secrets.DOCKERHUB_USERNAME }}`.

#### Escolher nome da imagem docker

```bash
docker tag exemplo_local_django docker.io/SUBSTITUIR_POR_USUARIO/exemplo_local_django:latest
```

#### Faz login no DockerHub

```bash
docker login --username SUBSTITUIR_POR_USUARIO --password SUBSTITUIR_POR_SENHA
```

#### Armazena a imagem docker no DockerHub

```bash
docker push exemplo_local_django docker.io/SUBSTITUIR_POR_USUARIO/exemplo_local_django:latest
```
