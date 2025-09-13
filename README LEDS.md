# 🚀 Projeto LEDS – Sistema de Concursos Públicos
📌 Autor: **Eliabe de Jesus Loureiro**  
📌 Desafio proposto no **Projeto LEDS**.

---

## 📖 Contexto do Desafio

O objetivo do desafio é desenvolver um programa que permita:

1. **Buscar concursos públicos pelo CPF do candidato**  
   → A partir do CPF informado, o sistema lista **Órgão, Edital e Código do Concurso** cujas vagas combinam com as profissões do candidato.

2. **Buscar candidatos pelo código do concurso**  
   → A partir do código de um concurso público, o sistema lista os **nomes, datas de nascimento e CPFs** dos candidatos que se encaixam no perfil desse concurso.

Os dados utilizados estão nos arquivos:
- `candidatos.txt`
- `concursos.txt`

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.10+**
- **FastAPI** – para expor a aplicação como API REST
- **Uvicorn** – servidor ASGI para rodar a API
- **Pydantic** – validação e tipagem de dados
- **SQLite** *(opcional, para diferencial de banco de dados)*

---

## 📂 Estrutura do Projeto

projeto-leds/
│── main.py # Interface CLI (menu interativo no terminal)
│── api.py # API FastAPI com os endpoints
│── modulo.py # Funções de carregamento e busca de dados
│── candidatos.txt # Base de candidatos
│── concursos.txt # Base de concursos
│── requirements.txt # Dependências do projeto
│── README.md # Documentação do projeto

yaml
Copiar código

---

## ▶️ Como Executar

### 1. Clonar o Repositório
```bash
git clone https://github.com/seu-usuario/projeto-leds.git
cd projeto-leds
2. Criar Ambiente Virtual (recomendado)
bash
Copiar código
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
3. Instalar Dependências
bash
Copiar código
pip install -r requirements.txt
4. Rodar o Programa no Terminal (modo CLI)
bash
Copiar código
python main.py
No menu, você poderá:

Buscar concursos por CPF

Buscar candidatos por código

Sair do sistema

5. Rodar a API (modo web)
bash
Copiar código
uvicorn api:app --reload --port 8001
➡️ Acesse no navegador:

Swagger UI: http://127.0.0.1:8001/docs

ReDoc: http://127.0.0.1:8001/redoc

📑 Endpoints da API
🔎 Buscar Concursos por CPF
GET /buscar-concursos/{cpf}

Parâmetro: CPF do candidato

Resposta: Lista de concursos compatíveis

json
Copiar código
[
  {
    "orgao": "SEDU",
    "edital": "9/2016",
    "codigo": "61828450843",
    "vagas": ["analista de sistemas", "marceneiro"]
  }
]
🔎 Buscar Candidatos por Código
GET /buscar-candidatos/{codigo}

Parâmetro: Código do concurso

Resposta: Lista de candidatos aptos

json
Copiar código
[
  {
    "nome": "Jackie Dawson",
    "nascimento": "14/08/1970",
    "cpf": "311.667.973-47",
    "profissoes": ["marceneiro", "assistente administrativo"]
  }
]
📘 Documentação do Código
main.py → Interface de linha de comando (CLI). Gerencia o menu e chama funções do modulo.py.

modulo.py → Responsável por:

Carregar dados dos arquivos .txt

Função buscar_concurso(cpf, candidatos, concursos)

Função buscar_candidato(codigo, candidatos, concursos)

api.py → Expõe o sistema como API REST utilizando FastAPI.

GET /buscar-concursos/{cpf}

GET /buscar-candidatos/{codigo}

Pydantic Models → Garantem que as respostas da API sejam estruturadas e bem documentadas no Swagger.

📚 Documentação da Solução
Critérios obrigatórios (40 pontos):

✅ Legibilidade do código → Código modular, dividido em arquivos e funções.

✅ Documentação do código → Docstrings em funções e módulos.

✅ Documentação da solução → README completo.

✅ Tratamento de erros → Entradas inválidas tratadas (CPF inexistente, concurso não encontrado, etc.).

Diferenciais (até 170 pontos extras):

✅ Criar um serviço com o problema (API com FastAPI) → +30 pontos

✅ Clean Code → Código modular, tipado e organizado → +20 pontos

✅ Padrão da tecnologia escolhida → Uso de FastAPI com Pydantic → +20 pontos

🟡 Banco de dados (SQLite/Postgres) → Ainda opcional (vale +30 pontos)


✅ Conclusão
Este projeto atende aos requisitos obrigatórios do desafio, com diferencial da API REST documentada automaticamente via Swagger.
A arquitetura modular facilita manutenção, futuras integrações e melhorias (como uso de banco de dados e testes).

