> Material de apoio para o workshop de Docker

---

## 📚 O que é Docker?

Docker é uma plataforma open-source que permite criar, testar e implementar aplicações em containers (ambientes isolados).

### Taxonomia Docker

| Conceito | Definição | Analogia |
|----------|-----------|----------|
| **Imagens** | aruivo com informações para rodar o programa | Programa estático (como um .exe) |
| **Containers** | Imagem em execução (instância ativa) | Programa rodando |
| **Dockerfiles** | Instruções para construir uma imagem | Recipe (receita de bolo) |
| **Registros** | Repositórios de imagens (Docker Hub, AWS ECR, etc) | App Store para imagens |

---

## 💻 Comandos Básicos do Docker

### 1. Listando Containers

```bash
# Lista apenas containers em execução
docker ps

# Lista todos os containers (incluindo os parados)
docker ps -a
```

### 2. Rodando Imagens

```bash
# Roda a imagem hello-world (teste inicial)
docker run hello-world

# Roda um container Ubuntu (morre automaticamente após executar)
docker run ubuntu

# Roda o Ubuntu em modo interativo com terminal bash
docker run -it ubuntu bash
```

> 💡 Flag `-it` significa **interactive tty** - permite interagir com o terminal do container

### 3. Controlando Containers

```bash
# Para um container em execução
docker stop <CONTAINER_ID>

# Inicia um container parado
docker start <CONTAINER_ID>

# Acessa um container em execução
docker exec -it <CONTAINER_ID> bash
```

### 4. Limpando a Tela

```bash
# Limpa o terminal
clear
```

---

## 🛠️ Criando Nosso Primeiro Dockerfile

```dockerfile
# Define a imagem base
FROM ubuntu:22.04

# Define o mantenedor
MAINTAINER Seu Nome <seu@email.com>

# Atualiza pacotes e instala ferramentas
RUN apt-get update && apt-get install -y curl

# Define diretório de trabalho
WORKDIR /app

# Copia arquivos para o container
COPY . /app

# Define comando padrão
CMD ["bash"]
```

### Buildando a Imagem

```bash
docker build -t minha-imagem:latest .
```

### Rodando o Container

```bash
docker run -it minha-imagem:latest
```

---

## 📝 Próximos Passos Opcionais

- [ ] Executar os comandos deste guia
- [ ] Criar seu próprio Dockerfile
- [ ] Experimentar com outras imagens (Node, Python, etc)
- [ ] Subir imagens para o Docker Hub

## Adincional

- https://justpaste.it/
