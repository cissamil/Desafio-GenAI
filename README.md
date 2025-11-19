# 📘 README — Como transformar a base de conhecimento em uma POC de agente GenAI (RAG)

 Transformar o arquivo  `base_conhecimento_ifood_genai.csv` em uma **prova de conceito (POC)** de um agente interno utilizado para decisões de **reembolsos e cancelamentos**, similar ao que times internos podem desenvolver no iFood.

A ideia não é construir um sistema completo, mas criar algo demonstrável para **portfólio, currículo ou entrevista técnica**.

> Desenvolvi uma POC de agente interno para decisões de reembolso/cancelamento utilizando RAG e uma base de conhecimento simulada.  
> A POC inclui fallback para baixa confiança e testes com cenários críticos (pedido já saiu para entrega, cancelamento por falha do restaurante, cobrança após cancelamento).  
> O foco foi garantir consistência operacional e evitar respostas incorretas ou inventadas.


---

## 🎯 Objetivo da POC

Criar um agente de IA capaz de:

1. **Consultar informações oficiais** (base de conhecimento)  
2. **Responder perguntas operacionais** de forma consistente  
3. **Evitar alucinações** (respostas inventadas)  
4. Aplicar **fallback seguro** quando não há confiança na resposta

---

## 🧰 O que você vai precisar

Você pode escolher entre duas abordagens:

| Tipo de POC | Ferramentas sugeridas |
|-------------|-----------------------|
| **Sem código (no-code)** | Flowise, Dify, ChatGPT Assistants, N8n, Zapier AI Actions |
| **Com código** | Python + biblioteca de RAG (LangChain, LlamaIndex etc.) |

Se seu foco é **portfólio rápido**, comece com **no-code**.

---

## 📥 1. Importe a base de conhecimento

Faça upload do CSV na ferramenta escolhida, na área onde ela aceita:

- **Knowledge Base**
- **Documents**
- **Files / Upload**
- **Sources / Data Sources**

Verifique se o conteúdo foi **indexado** corretamente.

---

## 🧩 2. Configure o propósito do agente

Sugestão de descrição:

> Você é um agente interno que auxilia colaboradores a decidirem sobre reembolsos e cancelamentos.  
> Sempre consulte a base de conhecimento antes de responder.  
> Se não houver confiança suficiente, sugira validação manual ou abertura de ticket interno, sem inventar informações.

---

## 🔍 3. Ative o uso da base com busca semântica (RAG)

Procure opções como:

- **Use knowledge in answers**
- **Ground responses on documents**
- **Retrieval / Semantic Search / RAG**
- **Search documents before answering**

Ative e mantenha as configurações padrão.

---

## ⚠️ 4. Configure o fallback de segurança

Mensagem sugerida:

> Não encontrei informações suficientes na base para responder com segurança. Sugiro abrir um ticket interno ou consultar a política oficial.

---

## 🧪 5. Teste com cenários reais

Use perguntas como:

| Pergunta | O que observar |
|---------|----------------|
| “O cliente quer reembolso, mas o pedido já saiu para entrega. Ainda é permitido?” | Diferença entre desistência do cliente e falhas do restaurante/app |
| “O restaurante cancelou por falta de ingrediente. O reembolso é automático?” | Deve identificar política de reembolso automático |
| “O cliente foi cobrado após o cancelamento. O que fazer?” | Deve orientar validação do estorno e possível ticket |

---

## 📄 Arquivo utilizado

`base_conhecimento_ifood_genai.csv`  
*(Simulação para fins educacionais — não representa políticas oficiais do iFood)*


