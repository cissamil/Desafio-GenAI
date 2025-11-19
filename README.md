# 🤖 POC: Agente GenAI para Decisões de Reembolso e Cancelamento (RAG No-Code)

Transformar o arquivo `base_conhecimento_ifood_genai.csv` em uma **Prova de Conceito (POC)** de um agente interno utilizado para decisões de **reembolsos e cancelamentos**, simulando o desenvolvimento interno de times no iFood.

A ideia central é criar algo **demonstrável** e robusto para **portfólio, currículo ou entrevista técnica**.

> Desenvolvi uma POC de agente interno para decisões de reembolso/cancelamento utilizando RAG e uma base de conhecimento simulada.
> A POC inclui fallback para baixa confiança e testes com cenários críticos (pedido já saiu para entrega, cancelamento por falha do restaurante, cobrança após cancelamento).
> O foco foi garantir **consistência operacional** e evitar respostas incorretas ou inventadas (alucinações).

---

## 🎯 Objetivo da POC

O projeto visa criar um agente de IA capaz de:

1.  **Consultar informações oficiais** (base de conhecimento).
2.  **Responder perguntas operacionais** de forma consistente.
3.  **Evitar alucinações** (respostas inventadas).
4.  Aplicar **fallback seguro** quando não há confiança na resposta.

---

## 🛠️ Arquitetura e Implementação (Dify Workflow)

A POC foi construída usando a abordagem **No-Code** através da ferramenta **Dify**, priorizando a velocidade de desenvolvimento e a clareza da arquitetura RAG.

### Fluxo RAG Implementado:

A lógica do agente é orquestrada através da seguinte sequência de blocos no Dify:

$$\text{INICIAR (Pergunta)} \longrightarrow \text{RECUPERAÇÃO DE CONHECIMENTO (RAG)} \longrightarrow \text{LLM (GPT-4 + System Prompt)} \longrightarrow \text{RESPOSTA}$$

### 🧩 Configuração do Agente (System Prompt e RAG)

O comportamento do agente foi definido no **System Prompt** do bloco LLM (GPT-4), forçando a consulta à base de conhecimento e a aderência à política de segurança:

| Configuração | Detalhe |
| :--- | :--- |
| **Ferramenta Usada** | Dify (Abordagem No-Code) |
| **Modelo LLM** | GPT-4 (ou similar) |
| **Base de Conhecimento** | `base_conhecimento_ifood_genai.csv` (indexada via **Knowledge Retrieval**) |
| **Prompt Central** | Força o uso exclusivo do contexto recuperado para garantir consistência. |
| **Regra de Segurança (Fallback)** | Se não houver confiança, o agente não responde e orienta a abertura de ticket ou validação manual. |

---

## 🧰 O que você vai precisar (Ferramentas Sugeridas)

| Tipo de POC | Ferramentas Sugeridas |
| :--- | :--- |
| **Sem Código (No-Code)** | **Dify** (utilizado nesta POC), Flowise, ChatGPT Assistants, N8n, Zapier AI Actions |
| **Com Código** | Python + biblioteca de RAG (LangChain, LlamaIndex etc.) |

---

## 📄 Arquivo Base de Conhecimento

O arquivo utilizado para indexação RAG é:

* **`base_conhecimento_ifood_genai.csv`**

*(Simulação para fins educacionais — não representa políticas oficiais do iFood).*

---

## 🧪 Testes com Cenários Críticos

O agente foi validado com cenários operacionais complexos para garantir que o RAG e o Fallback de segurança funcionassem corretamente.

| Pergunta (Teste) | Objetivo de Validação |
| :--- | :--- |
| “O cliente quer reembolso, mas o pedido já saiu para entrega. Ainda é permitido?” | Testar a **diferença** entre desistência do cliente e falhas do restaurante/app, consultando a base. |
| “O restaurante cancelou por falta de ingrediente. O reembolso é automático?” | Validar a identificação da política de **reembolso automático** em caso de falha do restaurante. |
| “O cliente foi cobrado após o cancelamento. O que fazer?” | Testar a orientação para validação do estorno e a ativação do **fallback** para abertura de ticket interno (se o estorno não for claro na base). |
| **Teste Fallback:** (e.g., "Qual a melhor cor para o logo?") | Verificar se o **Fallback de Segurança** é ativado, sugerindo ticket em vez de inventar informações. |
