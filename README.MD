# LangChain Project 🔗

Uma poderosa biblioteca para construção de aplicações baseadas em LLMs (Large Language Models), permitindo criar aplicações de IA avançadas com processamento de linguagem natural.

## 📋 Tabela de Conteúdos

- [LangChain Project 🔗](#langchain-project-)
  - [📋 Tabela de Conteúdos](#-tabela-de-conteúdos)
  - [🔍 Sobre](#-sobre)
  - [✨ Funcionalidades](#-funcionalidades)
  - [📋 Pré-requisitos](#-pré-requisitos)
  - [🚀 Instalação](#-instalação)
  - [🎮 Como Usar](#-como-usar)
    - [Inicialização Básica](#inicialização-básica)
  - [📝 Exemplos](#-exemplos)
    - [Exemplo 1: Chatbot com Memória](#exemplo-1-chatbot-com-memória)
    - [Exemplo 2: Consulta a Documentos 📚](#exemplo-2-consulta-a-documentos-)
  - [⚙️ Configuração Avançada](#️-configuração-avançada)
    - [Personalização de Modelos](#personalização-de-modelos)

## 🔍 Sobre

LangChain é um framework que facilita o desenvolvimento de aplicações utilizando modelos de linguagem. Ele permite combinar LLMs com outras fontes de computação e conhecimento, criando aplicações mais poderosas e contextuais.

## ✨ Funcionalidades

- **Chains**: Combine componentes em sequências para tarefas complexas
- **Prompts**: Gerenciamento e otimização de prompts para LLMs
- **Memory**: Persistência de estado entre chamadas de chain/agent
- **Agents**: Permita que LLMs decidam quais ações tomar
- **Integração com Dados**: Conecte seus LLMs a outras fontes de dados
- **Callbacks**: Hooks que permitem monitorar e depurar a execução

## 📋 Pré-requisitos

- Python 3.8.1 ou superior
- Pip (gerenciador de pacotes)
- Acesso a chaves de API para LLMs (OpenAI, Anthropic, etc.)

## 🚀 Instalação

1. Clone este repositório:

```bash
git clone https://github.com/joaooliveira10/LangChain.git
cd LangChain
```

2. Crie e ative um ambiente virtual (recomendado):

```bash
python -m venv venv
# No Windows
venv\Scripts\activate
# No macOS/Linux
source venv/bin/activate
```

3. Instale as dependências:

```bash
pip install -r requirements.txt
```

4. Configure suas variáveis de ambiente:

```bash
# No Windows
set OPENAI_API_KEY=sua_chave_aqui
# No macOS/Linux
export OPENAI_API_KEY=sua_chave_aqui
```

## 🎮 Como Usar

### Inicialização Básica

```python
from langchain.llms import OpenAI
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate

# Inicialize o LLM
llm = OpenAI(temperature=0.7)

# Crie um template de prompt
prompt = PromptTemplate(
    input_variables=["produto"],
    template="O que você sabe sobre {produto}?",
)

# Crie uma chain
chain = LLMChain(llm=llm, prompt=prompt)

# Execute a chain
resposta = chain.run("LangChain")
print(resposta)
```

## 📝 Exemplos

### Exemplo 1: Chatbot com Memória

```python
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory

conversation = ConversationChain(
    llm=llm,
    memory=ConversationBufferMemory()
)

response = conversation.predict(input="Olá! Como você está?")
print(response)
```

### Exemplo 2: Consulta a Documentos 📚

```python
from langchain.document_loaders import TextLoader
from langchain.indexes import VectorstoreIndexCreator

loader = TextLoader("./meudocumento.txt")
index = VectorstoreIndexCreator().from_loaders([loader])

query = "Qual o principal tema deste documento?"
response = index.query(query)
```

## ⚙️ Configuração Avançada

### Personalização de Modelos

Para configurar diferentes modelos e parâmetros, edite o arquivo `config.yml`:

```yaml
model:
  provider: openai
  name: gpt-3.5-turbo
  temperature: 0.7
  max_tokens: 500

memory:
  type: buffer
  k: 5
```
