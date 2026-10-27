# Gerador de Senhas em Python

Um gerador de senhas desenvolvido com Python, Flask, Flask-CORS, HTML, CSS e JavaScript. O projeto permite que o usuário personalize o tamanho da senha e escolha os tipos de caracteres utilizados, incluindo letras maiúsculas e minúsculas, números e símbolos.

A senha é gerada pelo backend em Python e enviada para a interface por meio de uma API REST, demonstrando a integração entre frontend e backend em uma aplicação web.

## Funcionalidades

- Definição do tamanho da senha.
- Utilização de letras maiúsculas e minúsculas.
- Inclusão de números.
- Inclusão de símbolos.
- Geração de senhas aleatórias conforme as opções selecionadas.
- Validação para informar ao usuário quando nenhuma categoria de caracteres for selecionada.
- Comunicação entre JavaScript e Python por meio de uma API REST.
- Utilização de CORS para permitir a comunicação entre frontend e backend.
- Interface responsiva com elementos visuais relacionados à segurança.

## Tecnologias utilizadas

### Backend

- **Python 3:** lógica de geração das senhas.
- **Flask:** criação do servidor e da API.
- **Flask-CORS:** configuração do compartilhamento de recursos entre origens.
- **Random:** seleção aleatória dos caracteres.

### Frontend

- **HTML5:** estrutura da página.
- **CSS3:** estilização e layout.
- **JavaScript:** interação com o usuário e comunicação com a API.

## Estrutura do projeto

```text
Gerador-de-Senhas-em-Python/
├── senha.py
├── index.html
├── script.js
└── README.md
```

### Descrição dos arquivos

- **`senha.py`:** responsável pelo backend, pela criação do servidor Flask e pela geração das senhas.
- **`index.html`:** contém a estrutura da interface, os campos de configuração e a área de exibição da senha.
- **`script.js`:** coleta as opções selecionadas pelo usuário, envia as requisições para a API e apresenta o resultado.
- **`README.md`:** documentação do projeto, com informações sobre as funcionalidades e instruções de execução.

## Instalação e execução

### 1. Requisitos

Antes de iniciar, verifique se o Python 3 está instalado:

```bash
python --version
```

Caso esteja utilizando Windows e o comando anterior não funcione, tente:

```powershell
py --version
```

### 2. Instalar as dependências

Instale o Flask e o Flask-CORS:

```bash
python -m pip install flask flask-cors
```

No Windows, caso necessário, utilize:

```powershell
py -m pip install flask flask-cors
```

### 3. Iniciar o servidor

Abra a pasta do projeto no Visual Studio Code e execute o seguinte comando no terminal:

```bash
python senha.py
```

Se o servidor iniciar corretamente, será exibido um endereço semelhante a:

```text
http://127.0.0.1:5000
```

Mantenha o terminal aberto enquanto utilizar a aplicação.

### 4. Abrir a interface

Abra o arquivo `index.html` no navegador.

O JavaScript fará as requisições para o servidor Flask, portanto, o backend precisa estar em execução para que a geração de senhas funcione.

## Funcionamento da aplicação

O processo de geração de senhas ocorre nas seguintes etapas:

1. **Configuração:** o usuário define o tamanho da senha e seleciona as categorias de caracteres desejadas.
2. **Envio dos dados:** o arquivo `script.js` coleta as opções e utiliza `fetch()` para enviar uma requisição HTTP `POST`.
3. **Processamento:** o Flask recebe os dados em formato JSON por meio do endpoint `/gerar`.
4. **Geração da senha:** o backend verifica as opções selecionadas e utiliza o módulo `random` para escolher os caracteres.
5. **Retorno da resposta:** o servidor envia a senha gerada em formato JSON.
6. **Exibição:** o JavaScript recebe a resposta e apresenta a senha na interface.

### Fluxo da aplicação

```text
Usuário
   |
   v
index.html
   |
   v
script.js
   |
   v
API Flask (/gerar)
   |
   v
senha.py
   |
   v
Geração da senha
   |
   v
Resposta JSON
   |
   v
script.js
   |
   v
Senha exibida na interface
```

## API

O backend disponibiliza um endpoint responsável pela geração das senhas.

### Gerar senha

| Propriedade | Valor |
|---|---|
| Método HTTP | `POST` |
| Endpoint | `/gerar` |
| URL local | `http://127.0.0.1:5000/gerar` |
| Formato da requisição | JSON |
| Formato da resposta | JSON |

### Exemplo de requisição

Os dados enviados pelo frontend possuem a seguinte estrutura:

```json
{
  "tamanho": 12,
  "letras": true,
  "numeros": true,
  "simbolos": true
}
```

| Campo | Descrição |
|---|---|
| `tamanho` | Quantidade de caracteres desejada para a senha. |
| `letras` | Define se letras serão utilizadas. |
| `numeros` | Define se números serão utilizados. |
| `simbolos` | Define se símbolos serão utilizados. |

### Caracteres disponíveis

O backend utiliza conjuntos de caracteres para compor a senha:

**Letras**

```python
letras = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
```

**Números**

```python
numeros = "0123456789"
```

**Símbolos**

```python
simbolos = "!@#$%&*;:()-_=+[]{}"
```

Os caracteres disponíveis são combinados conforme as opções selecionadas pelo usuário.

### Resposta de sucesso

Quando a senha é gerada, a API retorna um objeto JSON:

```json
{
  "senha": "A8@kP2#xLm91"
}
```

O valor apresentado é apenas um exemplo ilustrativo.

### Resposta de erro

Caso nenhuma categoria de caracteres seja selecionada, a API retorna uma mensagem de erro:

```json
{
  "erro": "Escolha pelo menos uma opção."
}
```

Nesse caso, o status HTTP esperado é `400 Bad Request`.

## Configuração do CORS

O projeto utiliza Flask-CORS para permitir que o frontend realize requisições ao backend quando estiver sendo servido por uma origem diferente.

A configuração no arquivo `senha.py` segue este padrão:

```python
from flask import Flask
from flask_cors import CORS

app = Flask(__name__)
CORS(app)
```

Essa configuração habilita o CORS para as rotas da aplicação. Em ambientes de produção, recomenda-se restringir as origens permitidas conforme a necessidade.

## Interface

A interface foi desenvolvida para oferecer uma experiência simples e intuitiva, com os seguintes elementos:

- Tema visual relacionado à segurança.
- Fundo com gradiente.
- Layout centralizado.
- Campo para definir o tamanho da senha.
- Opções para selecionar letras, números e símbolos.
- Botão para gerar a senha.
- Área para exibir o resultado.
- Mensagens de erro para situações inválidas ou falhas na operação.
- Layout responsivo para diferentes tamanhos de tela.

## Segurança

Este projeto possui finalidade educacional e demonstra conceitos de lógica de programação, desenvolvimento web e comunicação entre frontend e backend.

A implementação utiliza o módulo `random`, que não é recomendado para a geração de senhas que exigem segurança criptográfica. Para aplicações que lidam com credenciais reais, recomenda-se utilizar o módulo `secrets` do Python.

## Objetivo acadêmico

O objetivo do projeto é praticar a programação em Python, o desenvolvimento de interfaces web, a criação de APIs com Flask, o tratamento de requisições HTTP e a integração entre JavaScript e um backend.

---

## Autor

Desenvolvido por [EdeNet00](https://github.com/EdeNet00).

Projeto desenvolvido para fins educacionais.
