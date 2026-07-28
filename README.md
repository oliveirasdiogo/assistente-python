# Assistente de Programação Python

Aplicação web feita com Streamlit e a API da Groq para ajudar pessoas iniciantes
a estudar Python. O assistente fornece explicações, exemplos de código e links
para documentação oficial.

## Funcionalidades

- Interface de chat no navegador;
- Histórico da conversa durante a sessão;
- Respostas direcionadas a programação e Python;
- Contexto limitado às 12 mensagens mais recentes para controlar latência e custo;
- Chave da Groq lida da variável de ambiente ou informada pela interface;
- Botão para limpar a conversa.

## Requisitos

- [Conda](https://docs.conda.io/) (Anaconda ou Miniconda);
- Uma chave da API Groq, disponível em
  [console.groq.com/keys](https://console.groq.com/keys).

## Instalação com Conda

Clone o repositório e entre na pasta:

```bash
git clone URL_DO_SEU_REPOSITORIO
cd NOME_DO_REPOSITORIO
```

Crie o ambiente isolado `assistente-python` a partir do arquivo do projeto:

```bash
conda env create -f environment.yml
conda activate assistente-python
```

Para atualizar um ambiente existente após alterações nas dependências:

```bash
conda env update --name assistente-python --file environment.yml --prune
```

Como alternativa, o ambiente pode ser criado manualmente:

```bash
conda create --name assistente-python python=3.13 pip
conda activate assistente-python
pip install -r requirements.txt
```

O Conda mantém o Python e as dependências deste projeto separados dos demais
programas instalados no computador.

Para sair do ambiente, execute `conda deactivate`. Para removê-lo:

```bash
conda env remove --name assistente-python
```

### Alternativa sem Conda

Também é possível usar o módulo `venv`:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Configuração

Defina a chave como variável de ambiente:

```bash
export GROQ_API_KEY="sua-chave"
```

No Windows PowerShell:

```powershell
$env:GROQ_API_KEY="sua-chave"
```

Também é possível inserir a chave no campo protegido da barra lateral. Nunca
adicione uma chave real ao Git ou ao código-fonte.

## Execução

```bash
streamlit run assistente_python.py
```

O Streamlit mostrará no terminal o endereço local da aplicação, normalmente
`http://localhost:8501`.

## Exemplos de perguntas

- Como crio um “Hello, World!” em Python?
- Qual é a sintaxe de um laço `for`?
- Como uso `map` com uma função `lambda`?

## Estrutura do projeto

```text
.
├── assistente_python.py
├── environment.yml
├── requirements.txt
├── .gitignore
└── README.md
```

## Modelo de IA

O projeto usa `qwen/qwen3.6-27b`, atualmente classificado como Preview pela
Groq. Modelos Preview podem mudar ou ser removidos; se isso ocorrer, atualize
`MODEL_NAME` em `assistente_python.py` com um modelo ativo.

## Limitações

- Respostas de IA podem conter erros e devem ser verificadas;
- O histórico existe apenas durante a sessão do navegador;
- A aplicação depende da disponibilidade e dos limites da API Groq;
- As 12 mensagens mais recentes são enviadas como contexto.

## Contribuição

Contribuições são bem-vindas. Abra uma issue descrevendo a proposta ou envie
um pull request com uma alteração pequena e bem explicada.

## Licença

Distribuído sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.
