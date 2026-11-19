# Geração de Conteúdo Personalizado com IA - Tema e Público-Alvo

Projeto desenvolvido em **Python**, utilizando **LangChain**, **PromptTemplate** e **Groq API** para gerar explicações personalizadas com Inteligência Artificial.

O sistema permite definir um tema e um público-alvo, adaptando a linguagem, a profundidade técnica e os exemplos utilizados na resposta.

## Objetivo

Demonstrar a utilização de prompts dinâmicos e reutilizáveis com LangChain, aplicando conceitos de **Prompt Engineering** e integração com modelos de linguagem (LLMs).

O projeto explora como um mesmo tema pode ser explicado de maneiras diferentes de acordo com o público informado.

## Funcionalidades

- Geração de explicações utilizando Inteligência Artificial.
- Personalização do conteúdo por tema e público-alvo.
- Construção de prompts dinâmicos com `PromptTemplate`.
- Integração com a Groq API utilizando LangChain.
- Exibição das respostas diretamente no terminal.
- Configuração da chave de API por variável de ambiente.

## Tecnologias utilizadas

- Python 3.12
- LangChain Core
- LangChain Groq
- Groq API
- Modelo `openai/gpt-oss-120b`
- Python Dotenv
- Prompt Engineering

## Estrutura do projeto

```text
Geracao-de-Conteudo-Personalizado-com-IA-Tema-Publico-Alvo/
│
├── nivel4_prompt_template_OK.py   # Script principal
├── README.md                      # Documentação
└── .env                           # Chave da API (arquivo local)
```

O ambiente virtual `.venv` é criado localmente durante a configuração.

**Importante:** o arquivo `.env` contém informações sensíveis e não deve ser enviado ao GitHub.

## Como funciona

O sistema utiliza um `PromptTemplate` com duas variáveis:

- `tema`: assunto que será explicado.
- `publico`: público-alvo para o qual a explicação será direcionada.

Exemplo:

```python
from langchain_core.prompts import PromptTemplate

template = """
Explique o tema abaixo de forma clara e simples.

Tema: {tema}
Público-alvo: {publico}
"""

prompt_template = PromptTemplate(
    input_variables=["tema", "publico"],
    template=template
)

prompt_final = prompt_template.format(
    tema="Banco de Dados",
    publico="quem nunca programou"
)
```

O prompt preenchido é enviado ao modelo de linguagem, que gera a explicação de acordo com as informações fornecidas.

### Integração com a Groq

```python
from langchain_groq import ChatGroq

llm = ChatGroq(
    model="openai/gpt-oss-120b",
    temperature=0
)

resposta = llm.invoke(prompt_final)

print("Resposta da IA:\n")
print(resposta.content)
```

## Como executar

### 1. Clonar o repositório

```bash
git clone https://github.com/jrm0316/Geracao-de-Conteudo-Personalizado-com-IA-Tema-Publico-Alvo.git
```

Entre na pasta do projeto:

```bash
cd Geracao-de-Conteudo-Personalizado-com-IA-Tema-Publico-Alvo
```

### 2. Criar o ambiente virtual

Recomenda-se utilizar Python 3.12.

No Windows, com o Python 3.12 instalado:

```powershell
py -3.12 -m venv .venv
```

Ative o ambiente virtual no PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Instalar as dependências

```powershell
python -m pip install langchain-groq langchain-core python-dotenv
```

### 4. Configurar a chave da Groq

Crie um arquivo `.env` na raiz do projeto:

```env
GROQ_API_KEY=sua_chave_da_api_aqui
```

A chave pode ser obtida no [Groq Console](https://console.groq.com/).

### 5. Executar o programa

```powershell
python .\nivel4_prompt_template_OK.py
```

O programa enviará o prompt configurado para a Groq e exibirá a resposta no terminal.

É necessária uma conexão com a internet e uma chave de API válida.

## Testes realizados

Foram realizados dois testes de geração de conteúdo utilizando o mesmo tema, mas públicos-alvo diferentes.

### Teste 1 — Público iniciante

**Tema:** Banco de Dados

**Público-alvo:** Quem nunca programou

A resposta gerada apresentou:

- Explicações introdutórias.
- Analogias com situações cotidianas.
- Conceitos de tabelas, registros e colunas.
- Introdução às operações CRUD.
- Exemplos básicos de SQL.

**Resultado:** geração concluída com sucesso.

### Teste 2 — Público técnico

**Tema:** Banco de Dados

**Público-alvo:** Desenvolvedores Backend Python experientes

A resposta apresentou assuntos mais avançados, incluindo:

- Transações ACID e níveis de isolamento.
- Índices e otimização de consultas.
- PostgreSQL e Redis.
- SQLAlchemy e integração com Python.
- Connection pooling.
- Estratégias de desempenho e segurança.

**Resultado:** geração concluída com sucesso.

Os testes demonstraram que a alteração do público-alvo modifica o nível de detalhamento e a linguagem da resposta.

## Personalizando o conteúdo

Para gerar explicações sobre outros assuntos, basta alterar os valores das variáveis utilizadas no `PromptTemplate`.

Exemplo:

```python
prompt_final = prompt_template.format(
    tema="Inteligência Artificial",
    publico="estudantes do ensino médio"
)
```

Outro exemplo:

```python
prompt_final = prompt_template.format(
    tema="APIs REST",
    publico="desenvolvedores Backend Python iniciantes"
)
```

Não é necessário modificar a estrutura do prompt para utilizar diferentes temas e públicos.

## Limitações atuais

- Os valores de tema e público-alvo são definidos diretamente no código.
- O programa funciona por meio do terminal.
- Não possui interface gráfica ou web.
- Não armazena o histórico das respostas.
- Depende da disponibilidade da Groq API.
- As respostas geradas por IA podem conter informações incorretas e devem ser verificadas quando necessário.

## Possíveis melhorias futuras

- Permitir que o usuário informe tema e público-alvo pelo terminal.
- Adicionar controle de tamanho das respostas.
- Implementar diferentes níveis de profundidade.
- Permitir salvar o conteúdo gerado em arquivos.
- Desenvolver uma interface web utilizando Streamlit ou FastAPI.

Essas funcionalidades são possibilidades de evolução e não fazem parte da versão atual.

## Autor

**Juliano Rodrigues Madeira**

Projeto desenvolvido para estudo e aplicação prática de Python, LangChain, modelos de linguagem e Prompt Engineering.

GitHub: [jrm0316](https://github.com/jrm0316)
