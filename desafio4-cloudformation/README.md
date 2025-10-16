# Desafio 3 - Step Function Chatbot com Amazon Bedrock (via CloudFormation)

Este projeto usa **AWS CloudFormation** para implantar uma **AWS Step Function** que orquestra interações com um Modelo de Linguagem Grande (LLM) do **Amazon Bedrock**.

A Step Function atua como um "chatbot" simples, encadeando prompts e utilizando o Bedrock para gerar respostas.

## 🚀 Pré-requisitos

1.  **Conta AWS Configurada:** Credenciais de acesso com permissão para criar recursos no IAM, CloudFormation, Step Functions e Bedrock.
2.  **Acesso ao Modelo Bedrock:** Você **DEVE** habilitar o acesso ao modelo **manualmente** na sua conta AWS antes da implantação.

    * **Modelo Usado no Template:** `amazon.titan-text-lite-v1`
    * **Região:** `us-east-1` (Verifique se é a região onde você está implantando)

    **🚨 Passo Manual Necessário:** Vá ao console do **Amazon Bedrock** -> **Model catalog** -> **Request model access** e habilite o modelo utilizado aqui. Caso queira utilizar outro modelo, consulte as alterações necessárias descritas na seção **[Mudar o modelo LLM](#mudar-o-modelo-llm)**.

## 🛠️ Implantação

O template do CloudFormation cuida de toda a configuração, incluindo:

1.  **AWS::IAM::Role:** Cria a *Role* de execução necessária para a Step Function, já com a política `bedrock:InvokeModel` anexada.
2.  **AWS::StepFunctions::StateMachine:** Cria a máquina de estado (**Chatbot**) que define o fluxo de interação com o Bedrock.

## ❗Mudar o modelo LLM
Caso deseje usar um outro modelo, é necessário fazer duas alterações no template do CloudFormation:

1. Atualizar o ID do Modelo (Template JSON)
* Localizar o recurso <b>DefinitionSubstitutions -> bedrockinvokeModel_ModelId</b> e trocar o ARN do modelo pelo ARN do novo modelo desejado.

2. Atualizar a Permissão do IAM (Template JSON)
* Localize a seção <b>Policies -> PolicyDocument -> Resource</b> e atualize para o novo ARN.

## Demonstrações
### ✔️ Stack criada no CloudFormation
![Stack criada no CloudFormation](images/stack.png)

### ✔️ State Machine rodando no StepFunctions
![State Machine criada no StepFunctions](images/state-machine.png)
