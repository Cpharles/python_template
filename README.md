# TEMPLATE PARA CRIAR NOVO PROJETO PYTHON

Template para criação de novos projetos Python utilizando **Copier**, **uv** e uma estrutura moderna baseada no padrão `src/`.

O objetivo deste projeto é fornecer uma base reutilizável para iniciar rapidamente novos projetos Python, mantendo uma estrutura consistente e preparada para ferramentas modernas de desenvolvimento.

---

## 📋 Características

O template fornece inicialmente:

* Estrutura Python utilizando `src/`
* Gerenciamento de ambiente e dependências com **uv**
* Configuração através de `pyproject.toml`
* Testes com **Pytest**
* Estrutura separada para testes:
  * `unit`
  * `integration`
  * `e2e`
* Lint e formatação com **Ruff**
* Diretório para documentação
* Diretório para scripts auxiliares
* Configuração automática do nome do pacote
* Configuração da versão mínima do Python
* Geração de projetos através do **Copier**

---

## 📁 Estrutura do Template

```text
python_template/
│
├── copier.yml
├── README.md
│
└── template/
    ├── pyproject.toml.jinja
    ├── README.md.jinja
    ├── .gitignore
    ├── .python-version
    │
    ├── src/
    │   └── {{ package_name }}/
    │       ├── __init__.py
    │       └── __main__.py
    │
    ├── tests/
    │   ├── __init__.py
    │   ├── unit/
    │   │   └── __init__.py
    │   ├── integration/
    │   │   └── __init__.py
    │   └── e2e/
    │       └── __init__.py
    │
    ├── docs/
    │   └── index.md
    │
    └── scripts/
        └── README.md
```

Durante a geração do projeto, `{{ package_name }}` é substituído automaticamente pelo nome do pacote Python.

Por exemplo:

```text
{{ package_name }}
```

pode resultar em:

```text
meu_projeto
```

gerando:

```text
src/
└── meu_projeto/
    ├── __init__.py
    └── __main__.py
```

---

## 🚀 Utilização

## 1. Pré-requisitos

Antes de utilizar o template, é necessário ter instalado:

* Python
* `uv`
* Git
* Copier

### Verificar Python

```bash
python --version
```

ou:

```bash
python3 --version
```

### Verificar uv

```bash
uv --version
```

### Verificar Git

```bash
git --version
```

### Verificar Copier

```bash
copier --version
```

---

## 📦 Instalação do Copier

A recomendação é instalar o Copier utilizando `uv`:

```bash
uv tool install copier
```

Depois verifique:

```bash
copier --version
```

Se o Copier já estiver instalado, esta etapa não é necessária.

---

## 🏗️ Criando um novo projeto

Existem duas formas principais de utilizar o template:

1. A partir de uma cópia local do template
2. Diretamente a partir do GitHub

## 2. Utilizando o template localmente

Para utilizar este template localmentente é necessário antes baixar o repositório do GitHut para seu PC, execute o seguinte comando para clonar o repositório:

```bash
git clone https://github.com/Cpharles/python_template.git
```

Quando o repositório já estiver disponível localmente execute:

Primeiro crie um diretório para o projeto:

```bash
mkdir meu_projeto
cd meu_projeto
```

Vamos ter algo como:

```text
Documents/
    ├── python_template/
    └── <MEU_PROJETO>/
```

Entre no diretório onde deseja criar o novo projeto:

```bash
cd ~/Documents/<MEU_PROJETO>
```

Execute o Copier:

```bash
copier copy ../python_template .
```
> [!NOTE]
> Atenção para o "ponto" ( . ) ao final do comando, garante e força que o projeto seja criado dentro da pasta atual

Durante a criação o projeto o Copier apresentará algumas perguntas, por exemplo:

```text
Nome do projeto: meu_projeto
Nome do pacote Python: meu_projeto
Descrição do projeto: Meu novo projeto Python
Versão mínima do Python: 3.12
Nome do autor: Charles
E-mail do autor:
Adicionar configuração do Pytest? Yes
Adicionar configuração do Ruff? Yes
```

O Copier utilizará essas informações para gerar os arquivos do projeto.

## 3. Utilizando o template diretamente do GitHub

Existe a possibilidade de criar seu projeto a partir do GitHub, sem a necessidade de abaixar o projeto do GitHub, neste caso execute o comando:

> [!NOTE]
> Neste caso não é necessário a criação da pasta do projeto, pois o comando via GitHub já leva o nome da pasta do projeto que será criado.

Exemplo:

```bash
copier copy gh:Cpharles/python_template.git meu_projeto
```

Ou utilizando a URL completa:

```bash
copier copy https://github.com/Cpharles/python_template.git meu_projeto
```

Depois:

```bash
cd meu_projeto
```

> Durante o desenvolvimento do template, recomenda-se utilizar a versão local para facilitar os testes e a depuração.

### 🔧 Configuração do projeto

Assim como na execução local para a criação do seu projeto, durante a execução do Copier pelo GitHub, os valores definidos em `copier.yml` serão solicitados.

Um exemplo:

```text
Nome do projeto: meu_projeto
Nome do pacote Python: meu_projeto
Descrição do projeto: Meu novo projeto Python
Versão mínima do Python: 3.12
Nome do autor: Charles
E-mail do autor:
Adicionar configuração do Pytest? Yes
Adicionar configuração do Ruff? Yes
```

O Copier utilizará essas informações para gerar os arquivos do projeto.

---

## 📂 Projeto gerado

Após a execução do Copier, a estrutura será semelhante a:

```text
meu_projeto/
│
├── .env
├── .gitignore
├── .python-version
├── README.md
├── pyproject.toml
│
├── docs/
│   └── index.md
│
├── scripts/
│   └── README.md
│
├── src/
│   └── meu_projeto/
│       ├── __init__.py
│       └── __main__.py
│
└── tests/
    ├── __init__.py
    ├── unit/
    │   └── __init__.py
    ├── integration/
    │   └── __init__.py
    └── e2e/
        └── __init__.py
```

---

## 🐍 Configurando o ambiente

Entre no diretório do projeto:

```bash
cd meu_projeto
```

Execute:

> Execute uma linha por vez

```bash
uv python list
uv venv --python "py_version"
uv sync
```

O `uv` irá:

* criar o ambiente virtual `.venv`;
* resolver as dependências;
* instalar as dependências caso já tenha;
* instalar o próprio projeto em modo editável.

Após isso, o ambiente estará pronto para utilização.

---

## ▶️ Executando o projeto

O projeto possui um `__main__.py`, permitindo sua execução através do Python.

Utilize:

```bash
uv run python -m meu_projeto
```

Exemplo de saída:

```text
Hello from meu_projeto!
```

---

## 🧪 Executando os testes

Caso o Pytest esteja habilitado no template:

```bash
uv run pytest
```

Para executar testes com informações mais detalhadas:

```bash
uv run pytest -v
```

Os testes estão organizados em:

```text
tests/
├── unit/
├── integration/
└── e2e/
```

---

## 🔍 Verificando o código com Ruff

Para executar o lint:

```bash
uv run ruff check .
```

Para corrigir automaticamente problemas que possam ser corrigidos pelo Ruff:

```bash
uv run ruff check . --fix
```

---

## ✨ Formatando o código

Para formatar o projeto:

```bash
uv run ruff format .
```

Para apenas verificar se o código está formatado:

```bash
uv run ruff format --check .
```

---

## 🔁 Atualizando um projeto criado pelo template

O Copier também permite atualizar um projeto existente a partir do template.

Dentro do projeto gerado:

```bash
copier update
```

Antes de executar a atualização em um projeto real, recomenda-se verificar as alterações que serão aplicadas e manter o projeto versionado com Git.

Um fluxo seguro é:

```bash
git status
git add .
git commit -m "chore: save current state before template update"
copier update
```

Depois:

```bash
git diff
```

para revisar as alterações.

---

## 🌿 Controle de versão

Após gerar o projeto, inicialize um repositório Git:

```bash
git init
```

Adicione os arquivos:

```bash
git add .
```

Crie o primeiro commit:

```bash
git commit -m "chore: initial project structure"
```

Para conectar ao GitHub:

```bash
git remote add origin https://github.com/USUARIO/REPOSITORIO.git
```

Depois:

```bash
git branch -M main
git push -u origin main
```

---

## 📄 Licença

:books: [Read license](./LICENSE.txt)

---

## 👤 Autor

**Charles**

Repositório: [Repo New project Python Template](https://github.com/Cpharles/python_template.git)
