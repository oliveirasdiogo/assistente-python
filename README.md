# Assistente de Programação Python

[![Qualidade](https://github.com/oliveirasdiogo/assistente-python/actions/workflows/quality.yml/badge.svg)](https://github.com/oliveirasdiogo/assistente-python/actions/workflows/quality.yml)
[![Python 3.14](https://img.shields.io/badge/Python-3.14-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Streamlit 1.59.2](https://img.shields.io/badge/Streamlit-1.59.2-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Groq 1.5.0](https://img.shields.io/badge/Groq-1.5.0-F55036)](https://groq.com/)
[![Licença MIT](https://img.shields.io/badge/Licen%C3%A7a-MIT-2EA44F)](LICENSE)

Aplicação web feita com Streamlit e a API da Groq para ajudar pessoas iniciantes
a estudar Python. O assistente fornece explicações, exemplos de código e links
para documentação oficial.

## Índice

- [Funcionalidades](#funcionalidades)
- [Requisitos](#requisitos)
- [Instalação com Conda](#instalação-com-conda)
- [Configuração da Groq](#configuração-da-groq)
- [Execução com Streamlit](#execução-com-streamlit)
- [Solução de problemas](#solução-de-problemas)
- [Exemplos de perguntas](#exemplos-de-perguntas)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Modelo de IA](#modelo-de-ia)
- [Limitações](#limitações)
- [Contribuição](#contribuição)
- [Licença](#licença)

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
git clone https://github.com/oliveirasdiogo/assistente-python.git
cd assistente-python
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
conda create --name assistente-python python=3.14 pip
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

## Configuração da Groq

A [Groq](https://groq.com/) fornece a API que executa o modelo de inteligência
artificial usado pelo chat. Para configurar:

1. Crie uma conta no [GroqCloud Console](https://console.groq.com/);
2. Abra a página [API Keys](https://console.groq.com/keys);
3. Crie uma chave e copie o valor exibido;
4. Defina a chave como variável de ambiente antes de iniciar a aplicação.

No Linux ou macOS:

```bash
export GROQ_API_KEY="sua-chave"
```

No Windows PowerShell:

```powershell
$env:GROQ_API_KEY="sua-chave"
```

Também é possível inserir a chave no campo protegido da barra lateral. Nunca
adicione uma chave real ao Git, ao código-fonte, ao `.env.example` ou a capturas
de tela. A API pode ter limites de uso e custos definidos pela sua conta Groq.

Consulte a [documentação da API Groq](https://console.groq.com/docs/overview)
para detalhes sobre modelos, limites e erros.

## Execução com Streamlit

O [Streamlit](https://streamlit.io/) transforma o script Python em uma aplicação
web local. Com o ambiente Conda ativado e a chave configurada, execute:

```bash
streamlit run assistente_python.py
```

O Streamlit mostrará no terminal o endereço local da aplicação, normalmente
`http://localhost:8501`. Abra esse endereço no navegador. Para encerrar o
servidor, volte ao terminal e pressione `Ctrl+C`.

Algumas opções úteis:

```bash
# Usar outra porta
streamlit run assistente_python.py --server.port 8502

# Confirmar a instalação e a versão
streamlit version
```

Consulte a [documentação do Streamlit](https://docs.streamlit.io/) para opções
de configuração, componentes e publicação.

## Solução de problemas

- **`streamlit: command not found`**: ative o ambiente com
  `conda activate assistente-python` e instale as dependências novamente;
- **Chave inválida ou não informada**: confirme `GROQ_API_KEY` ou use o campo
  protegido da barra lateral;
- **Porta 8501 ocupada**: execute com `--server.port 8502`;
- **Modelo indisponível**: consulte os
  [modelos ativos da Groq](https://console.groq.com/docs/models) e atualize
  `MODEL_NAME`.

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
