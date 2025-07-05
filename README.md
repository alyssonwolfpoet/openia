# 🤖 openia — LLM Local com Ollama + Open WebUI

Este projeto fornece um ambiente completo para rodar **modelos de linguagem (LLMs)** localmente utilizando [Ollama](https://ollama.com) e a interface gráfica [Open WebUI](https://github.com/open-webui/open-webui).

## 🚀 Visão geral

- 🧠 **Ollama**: executa modelos LLM localmente via API.
- 🌐 **Open WebUI**: interface web para interagir com os modelos.
- 💾 **Persistência**: volumes Docker garantem que dados e modelos não sejam perdidos.
- 📦 **Modelos pré-instalados**:
  - `llama3.2`
  - `nomic-embed-text`

---

## 📁 Estrutura do projeto

```bash
openia/
├── docker-compose.yml      # Define os serviços Ollama e WebUI
├── README.md               # Este arquivo
└── zera.ps1                # Script PowerShell para limpar o ambiente Docker
````

---

## 🛠️ Como usar

### 1. Clone o repositório

```bash
git clone https://github.com/alyssonwolfpoet/openia.git
cd openia
```

### 2. Suba os containers

```bash
docker compose up -d
```

### 3. Acesse pelo navegador

* 🌐 Open WebUI: [http://localhost:3000](http://localhost:3000)
* 🔌 API do Ollama: [http://localhost:11434](http://localhost:11434)

---

## 🧼 Limpeza do ambiente Docker

### Executar o script de limpeza total (recomendado para ambiente local):

```powershell
.\zera.ps1
```

### Ou, manualmente:

```powershell
# Parar todos os containers
docker ps -q | ForEach-Object { docker stop $_ }

# Remover todos os containers
docker ps -aq | ForEach-Object { docker rm $_ }

# Remover todas as imagens
docker images -q | ForEach-Object { docker rmi -f $_ }

# Remover todos os volumes
docker volume ls -q | ForEach-Object { docker volume rm $_ }

# Limpeza geral
docker system prune --all --force --volumes
```

---

## 🧠 Gerenciar modelos manualmente

Você pode rodar comandos diretamente dentro do container `ollama`:

### Listar modelos disponíveis:

```bash
docker exec -it ollama ollama list
```

### Baixar um novo modelo:

```bash
docker exec -it ollama ollama pull mistral
```

### Remover modelo:

```bash
docker exec -it ollama ollama rm llama3.2
```

---

## 🐞 Logs e Debug

### Ver logs em tempo real:

```bash
docker compose logs -f
```

### Ver logs apenas do WebUI:

```bash
docker logs -f open-webui
```

### Ver logs do Ollama:

```bash
docker logs -f ollama
```

---

## 📦 Parar / Reiniciar containers

### Parar os serviços:

```bash
docker compose down
```

### Reiniciar os serviços:

```bash
docker compose down && docker compose up -d
```

---

## 📝 Licença

Distribuído sob a licença [MIT](LICENSE).

---

## 🙋‍♀️ Contribuindo

Sinta-se à vontade para abrir *issues*, propor melhorias ou enviar *pull requests*!

```

Se quiser, posso também gerar o arquivo `zera.ps1` com seu script de limpeza, ou criar `.gitignore` e outras coisas para completar o projeto. Quer que eu faça?
```
