# Desafio 3 - AWS Step Functions

Este desafio utiliza o **AWS Step Functions** com o serviço **Amazon Bedrock**, que oferece acesso a modelos de IA generativa de ponta. O objetivo é criar e escalar aplicações de forma fácil e segura.

## ✅ Escolha do Modelo

Para a aplicação, foi selecionado o modelo **Titan Text G1 - Lite** da Amazon. Este LLM é otimizado para tarefas de processamento de texto, sendo eficiente e de baixo custo. Ideal para casos que exigem respostas rápidas e diretas, como:

- **Resumos:** Sintetiza textos longos em versões curtas e objetivas.
- **Perguntas e Respostas:** Responde de forma precisa e concisa.
- **Extração de Informações:** Identifica e extrai dados relevantes de textos.

A partir disso, nasceu o **ClouDIO**, assistente da plataforma DIO especialista em cloud computing.

![Fluxo de Trabalho Bedrock](images/stepfunctions_graph.png)

## 🤖 Persona: ClouDIO

O ClouDIO é um bot descontraído, especialista em cloud computing, criado para ajudar estudantes de TI e devs juniores. Ele utiliza analogias, piadas e trocadilhos para tornar o aprendizado mais leve e divertido.

![Persona CloudDIO](images/model-bedrock.png)

## 📏 Parâmetros de Inferência do Modelo

Estes parâmetros controlam como o modelo gera texto:

- **Temperatura (0.7):** Controla a criatividade.  
  - Baixo (ex: 0.2): Respostas focadas e deterministas.  
  - Alto (ex: 0.7): Respostas diversificadas e criativas.

- **topP (0.9):** Controla a diversidade do vocabulário.  
  - Limite de probabilidade para escolha das palavras.  
  - Alto (ex: 0.9): Maior variedade de palavras.

- **Máximo de tokens (250):** Limita o tamanho da resposta.  
  - Garante que a resposta seja curta e objetiva.

## ⚙️ Exemplo de Configuração

```json
{
  "inputText": "CONTEXTO: Você é o ClouDIO, bot descontraído da DIO, especialista em cloud computing. Cumprimente se apresentando. Sua missão é ser o dev mais descontraído da nuvem. Sua resposta precisa ser CURTA, SUCINTA e fácil de entender para estudantes de TI e devs juniores. Use analogias, piadas ou trocadilhos. Responda APENAS UMA VEZ. \n\nExplicação: O que é AWS Step Functions?",
  "textGenerationConfig": {
    "temperature": 0.7,
    "topP": 0.9,
    "maxTokenCount": 250
  }
}
```

## 💬 Demonstração

### Pergunta: "O que é o Step Functions da AWS?"

![Resposta do modelo](images/invoke-model.png)