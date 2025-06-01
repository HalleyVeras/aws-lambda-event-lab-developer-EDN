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

![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-23.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-25.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-26.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-52.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-52_1.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/Role-Created-halley-veras.png)

---

## 3️⃣ Criar Função Lambda

1. Acesse o **AWS Lambda** no console.
2. Clique em **Criar função**.
3. Selecione **Criar do zero**.
4. Nomeie a função:
5. Selecione **Python 3.9** como tempo de execução.
6. Em **Permissões**, selecione **Usar uma função existente** e escolha:


![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-54.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-56.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_16-59.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-02.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-04.png)


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

![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-07.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-08.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-09.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-12.png)

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

![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-13.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-15.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-20.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-22.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/2025-06-01_17-24.png)
![1](https://raw.githubusercontent.com/HalleyVeras/aws-lambda-event-lab-developer-EDN/refs/heads/main/arquivos1/Lambda-Trigger-Created.png)

---



✅ **Laboratório concluído!🚀**



## 📝 Créditos

Este laboratório foi realizado no curso **Developer** da **Escola da Nuvem**.

---



    
