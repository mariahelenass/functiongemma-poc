# functiongemma-poc

Proof of Concept (PoC) utilizando o modelo **FunctionGemma (google/functiongemma-270m-it)** para **function calling**, com objetivo de testa-lo em ambientes embarcados.

## Modelo

* **google/functiongemma-270m-it**

## Instalação

Crie e ative um ambiente virtual:

```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

## Autenticação (Hugging Face)

Este projeto utiliza token via variável de ambiente.

1. Crie um arquivo `.env`:

```env
HF_TOKEN=seu_token_aqui
```

2. Garanta que o `.env` esteja no `.gitignore`.

3. Carregue o token no código:

```python
import os
from dotenv import load_dotenv

load_dotenv()
hf_token = os.getenv("HF_TOKEN")
```

## Exemplo de uso

```python
from transformers import AutoProcessor, AutoModelForCausalLM
import os

model_id = "google/functiongemma-270m-it"

processor = AutoProcessor.from_pretrained(
    model_id,
    token=os.getenv("HF_TOKEN")
)

model = AutoModelForCausalLM.from_pretrained(
    model_id,
    device_map="auto",
    torch_dtype="auto",
    token=os.getenv("HF_TOKEN")
)
```
