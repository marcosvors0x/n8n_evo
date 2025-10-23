# Evolução API + N8N: Guia de Implantação para Mac M1 (Self-Hosted)

Este guia descreve o procedimento para rodar a stack de automação Evolution API (Baileys) e N8N no Docker em máquinas com chip Apple Silicon (M1/ARM64).

## 1. Preparação

1.  **Instalar Docker Desktop:** Garanta que o Docker Desktop esteja instalado e em execução.
2.  **Diretório:** Crie uma pasta para o projeto e coloque os arquivos `.env` e `docker-compose.yml` nela.
    ```bash
    mkdir evolution-stack
    cd evolution-stack
    # Copie os arquivos .env e docker-compose.yml para cá
    ```

## 2. Inicialização da Stack (Algoritmo Principal)

Execute os comandos na sequência para iniciar a stack, garantindo que as correções de M1 e Baileys sejam aplicadas:

1.  **Parar e Limpar:** (Opcional, mas recomendado para um início limpo)
    ```bash
    docker-compose down
    ```

2.  **Iniciar a Stack (Corrigida):**
    ```bash
    docker-compose up -d --force-recreate
    ```
    *OBSERVAÇÃO:* O `--force-recreate` garante que a diretiva `platform: linux/amd64` seja lida e aplicada para a emulação no M1.

3.  **Verificar Logs da API:**
    ```bash
    docker logs evolution_api --follow
    ```
    Aguarde até ver a mensagem `Evolution API is working!`.

## 3. Configuração de Webhook e QR Code

### 3.1. Conexão do WhatsApp (QR Code)

1.  Acesse o Painel Manager: `http://localhost:8080/manager`
2.  Crie ou acesse sua instância.
3.  O QR Code deve aparecer. Caso não apareça, a correção da variável `CONFIG_SESSION_PHONE_VERSION` falhou e você deve buscar uma **versão mais atualizada** de `2.3000...` e reiniciar a API.

### 3.2. Configuração do Webhook (N8N)

Esta etapa exige o uso do DNS interno do Docker:

1.  Acesse o N8N: `http://localhost:5678`
2.  Na configuração da instância da Evolution API (no Manager ou via API):
    * **URL CORRETA:** Use o nome do serviço **`n8n`**, e não `localhost`.
    * **Exemplo de URL de Webhook:** `http://n8n:5678/webhook/<seu_caminho_webhook>`

Com este guia, você tem a receita completa e comprovada para replicar sua stack com sucesso.
