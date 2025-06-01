# 🛡️ Automating the End: Terminating EC2 Instances with Lambda | Developer EDN

![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/Image1.jpg)

**Curso: Developer – Escola da Nuvem**  
**Autor: Halley Veras**

Este repositório contém o passo a passo detalhado do laboratório **"Automatizando o Fim das Instâncias EC2"** realizado no curso **Developer EDN** da **Escola da Nuvem**.

## 🎯 Objetivos:
> - Criar uma política IAM para finalizar instâncias EC2.
> - Criar e configurar uma função Lambda.
> - Associar permissões corretas.
> - Configurar o gatilho com Amazon EventBridge.
> - Automatizar a execução da função Lambda para terminar instâncias EC2.

---

## 📂 Índice

- [1️⃣ Criar Política IAM](#1️⃣-criar-política-iam)
- [2️⃣ Criar Role/Função IAM](#2️⃣-criar-rolefunção-iam)
- [3️⃣ Criar Função Lambda](#3️⃣-criar-função-lambda)
- [4️⃣ Configurar Script Lambda](#4️⃣-configurar-script-lambda)
- [5️⃣ Agendar com EventBridge](#5️⃣-agendar-com-eventbridge)
- [6️⃣ Excluir Recursos (Limpeza)](#6️⃣-excluir-recursos-limpeza)

---

## 1️⃣ Criar Política IAM

1. Acesse o **AWS IAM** no console.
2. No painel esquerdo, clique em **Políticas**.
3. Clique em **Criar política**.
4. Selecione a aba **JSON**.
5. Copie o conteúdo do arquivo **Política IAM** (fornecido pelo curso) e cole.
6. Nomeie a política como:
7. Clique em **Criar política**.

![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-09.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-09_1.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-11.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-12.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-13.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-14.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-15.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-19.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/Policy-Created-halley-veras.png)




---

## 2️⃣ Criar Role/Função IAM

1. Acesse **IAM > Funções**.
2. Clique em **Criar função**.
3. Selecione **Serviço da AWS** e escolha **Lambda**.
4. Avance e anexe a política criada:
5. Nomeie a Role como:
6. Clique em **Criar função**.

<!-- 📸 Adicione aqui o print da criação da função com Lambda e a política anexada -->

---

## 3️⃣ Criar Função Lambda

1. Acesse o **AWS Lambda** no console.
2. Clique em **Criar função**.
3. Selecione **Criar do zero**.
4. Nomeie a função:
5. Selecione **Python 3.9** como tempo de execução.
6. Em **Permissões**, selecione **Usar uma função existente** e escolha:


<!-- 📸 Adicione aqui o print da criação da função Lambda -->

---

## 4️⃣ Configurar Script Lambda

1. Baixe o arquivo **Terminator** (fornecido pelo curso).
2. Na função Lambda, vá em **Origem do código** e clique em **Fazer upload de arquivo .zip**.
3. Carregue o arquivo **Terminator.zip**.
4. Clique em **Deploy**.
5. Configure:
- **Tempo limite:** 10 segundos.
- **Manipulador (Handler):**  
  ```
  Terminator.lambda_handler
  ```
6. Clique em **Salvar**.

<!-- 📸 Adicione aqui o print do upload do código, configuração de timeout e handler -->

---

## 5️⃣ Agendar com EventBridge

1. Na função Lambda, clique em **Adicionar gatilho**.
2. Selecione **EventBridge**.
3. Clique em **Criar uma regra**:
- Nome da regra:  
  ```
  GatilhoTerminarEC2-<seu_nome_sobrenome>
  ```
- Tipo de regra: **Expressão de agendamento**.
- Exemplo de expressão:
  ```
  rate(5 minutes)
  ```
4. Clique em **Adicionar**.

<!-- 📸 Adicione aqui o print da configuração do gatilho EventBridge -->

---

## 6️⃣ Excluir Recursos (Limpeza)

1. Exclua a **Função Lambda**:
- Lambda > Funções > Selecione a função > Ações > Excluir.
2. Exclua a **Role IAM**:
- IAM > Funções > Selecione a função > Excluir.
3. Exclua a **Política IAM**:
- IAM > Políticas > Selecione a política > Excluir.
4. Exclua a **Regra EventBridge**:
- EventBridge > Regras > Selecione a regra > Excluir.

<!-- 📸 Adicione aqui o print da exclusão dos recursos -->

---

✅ **Laboratório concluído!**

Parabéns por finalizar o laboratório! 🚀

---

## 📝 Créditos

Este laboratório foi realizado no curso **Developer EDN** da **Escola da Nuvem**.

---



    
