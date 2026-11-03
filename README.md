# Desafio RAG — Os Sertões

Três abordagens de RAG (Recuperação e Geração de Respostas) para responder perguntas sobre *Os Sertões*, de Euclides da Cunha.

| Notebook | Abordagem | Como recupera |
|---|---|---|
| [`1_naive_rag.ipynb`](1_naive_rag.ipynb) | Naive RAG | Trechos de 1000 caracteres; os 5 mais parecidos vão ao LLM |
| [`2_parent_rag.ipynb`](2_parent_rag.ipynb) | Parent RAG | Busca em "filhos" pequenos (~400) e envia ao LLM os "pais" (~3000) |
| [`3_rerank_rag.ipynb`](3_rerank_rag.ipynb) | Rerank RAG | Busca 25 candidatos e reordena com cross-encoder; os 5 melhores vão ao LLM |

## Stack

- **PDF:** `pypdf` + limpeza de hifenização e quebras de linha
- **Embeddings:** `intfloat/multilingual-e5-base`
- **Banco vetorial:** ChromaDB (em memória)
- **Reranker:** `BAAI/bge-reranker-v2-m3`
- **LLM:** Google Gemini (`gemini-2.5-flash`)

## Como rodar

1. Abra o notebook no Google Colab e ative a GPU (*Ambiente de execução → Alterar tipo*).
2. Crie uma chave gratuita em [Google AI Studio](https://aistudio.google.com/apikey) e salve em **Secrets** do Colab com o nome `GEMINI_API_KEY`.
3. Execute todas as células. O PDF é baixado automaticamente; se falhar, faça upload manual como `os-sertoes.pdf`.

Cada notebook salva suas respostas em `respostas_<abordagem>.json`, com as páginas recuperadas, para comparação entre as abordagens.

## Questões

1. Qual é a visão de Euclides da Cunha sobre o ambiente natural do sertão nordestino e como ele influencia a vida dos habitantes?
2. Quais são as principais características da população sertaneja descritas por Euclides da Cunha? Como ele relaciona essas características com o ambiente em que vivem?
3. Qual foi o contexto histórico e político que levou à Guerra de Canudos, segundo Euclides da Cunha?
4. Como Euclides da Cunha descreve a figura de Antônio Conselheiro e seu papel na Guerra de Canudos?
5. Quais são os principais aspectos da crítica social e política presentes em "Os Sertões"? Como esses aspectos refletem a visão do autor sobre o Brasil da época?

Livro: [PDF da Fundar](https://fundar.org.br/wp-content/uploads/2021/06/os-sertoes.pdf)
