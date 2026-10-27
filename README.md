# Gerador-de-Senhas-em-Python

Um gerador de senhas desenvolvido com Python, Flask, Flask-CORS, HTML, CSS e JavaScript.
O projeto permite que o usuário escolha o tamanho da senha e quais tipos de caracteres deseja utilizar: letras, números e símbolos. A senha é gerada pelo backend em Python e enviada para a interface através de uma API.


# Funcionalidades:
1. Escolher o tamanho da senha.
2.Utilizar letras maiúsculas e minúsculas.
3.Utilizar números.
4. Utilizar símbolos.
5. Gerar uma senha aleatória.
6. Informar ao usuário caso nenhuma opção de caractere seja selecionada.
7. Comunicação entre JavaScript e Python através de uma API REST.
8.Utilização de CORS para permitir a comunicação entre frontend e backend.



# Tecnologias utilizadas:
# Backend
Python 3
Flask
Flask-CORS
Random

# Frontend
HTML5
CSS3
JavaScript


# A estrutura recomendada para o projeto é:
projeto senhas/
1. │
2. ├── senha.py
3. ├── index.html
4. ├── script.js
5. └── README.md

# senha.py
É o arquivo responsável pelo backend da aplicação.
Ele utiliza Flask para criar o servidor e disponibiliza a rota:

# POST /gerar
Essa rota recebe as configurações enviadas pelo JavaScript, gera uma senha aleatória e retorna o resultado.

# index.html
É a página principal da aplicação.

# Nela estão:
Campo para definir o tamanho da senha.
Opção para utilizar letras.
Opção para utilizar números.
Opção para utilizar símbolos.
Botão para gerar a senha.
Área onde a senha gerada é exibida.
O arquivo também contém o código CSS responsável pelo visual da página.

# script.js
É responsável pela interação da página com o backend.

Quando o usuário clica no botão GERAR SENHA, o JavaScript coleta as opções selecionadas e envia uma requisição POST para o servidor Flask.

# Instalação no terminal
1. Verifique se o Python está instalado
python --version

3. Instale o Flask
python -m pip install flask

5. Instale o Flask-CORS
python -m pip install flask-cors

Ou instale os dois de uma vez:
python -m pip install flask flask-cors

# Como executar:
1. Abra a pasta do projeto
Abra a pasta projeto senhas no VS Code.

2. Inicie o servidor
No terminal, execute:

python senha.py
Se tudo estiver funcionando corretamente, aparecerá:
* Running on http://127.0.0.1:5000
  
3. Abra o index.html
Abra o arquivo index.html no navegador.

# O JavaScript irá se comunicar com o servidor Flask através do endereço:

http://127.0.0.1:5000


# O funcionamento ocorre da seguinte maneira:

* Usuário
*    ↓
* index.html
*    ↓
* script.js
*    ↓
* API Flask
*    ↓
* senha.py
*    ↓
* Geração da senha
*    ↓
* Resposta JSON
*    ↓
* script.js
*    ↓
* Senha exibida na tela



1. Usuário escolhe as configurações
O usuário informa o tamanho da senha e escolhe se deseja utilizar:

Letras.
Números.
Símbolos.



2. script.js envia os dados
O JavaScript utiliza fetch() para enviar uma requisição POST para:
http://127.0.0.1:5000/gerar


Os dados são enviados em formato JSON:

{
    "tamanho": 12,
    "letras": true,
    "numeros": true,
    "simbolos": true
}
3. senha.py recebe os dados
O Flask recebe as informações:

dados = request.json
Depois, o programa verifica quais tipos de caracteres foram selecionados.

4. A senha é gerada
O programa utiliza o módulo random para escolher caracteres aleatoriamente.

Os caracteres disponíveis são:
letras = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
numeros = "0123456789"
simbolos = "!@#$%&*;:()-_=+[]{}"

5. A senha é enviada para o frontend
Depois de gerar a senha, o Flask retorna um JSON:

{
    "senha": "A8@kP2#xLm91"
}

O script.js recebe a resposta e exibe a senha no index.html.


# API:
POST /gerar
Endpoint responsável por gerar uma nova senha.

Requisição
{
    "tamanho": 12,
    "letras": true,
    "numeros": true,
    "simbolos": true
}
Resposta de sucesso
{
    "senha": "aB8@xP2#Lm91"
}
Resposta de erro
Caso nenhuma opção seja selecionada:

{
    "erro": "Escolha pelo menos uma opção."
}
Nesse caso, a API retorna:

400 Bad Request

# CORS
O projeto utiliza Flask-CORS para permitir a comunicação entre o frontend e o backend.

No arquivo senha.py:

from flask_cors import CORS
app = Flask(__name__)
CORS(app)


# Interface
A interface possui:

1. Tema relacionado a segurança.
2. Fundo com gradiente.
3. Layout centralizado.
4. Botão para gerar a senha.
5. Área para exibir a senha.
6. Mensagem de erro caso ocorra algum problema.
7. Layout responsivo.
8. Observação

OBS:
Este projeto foi desenvolvido com finalidade educacional, demonstrando a comunicação entre um frontend em HTML/JavaScript e um backend em Python utilizando Flask.
Para sistemas que exigem alto nível de segurança, recomenda-se utilizar métodos de geração de números aleatórios apropriados para fins criptográficos.
👨‍💻

A-------------------------------------------------------------------------------------------------------------------------------------------A

# Gerador de Senhas em Python

Aplicação web desenvolvida com Python, Flask, HTML, CSS e JavaScript para gerar senhas aleatórias personalizadas de acordo com as preferências do usuário.

O projeto permite definir o tamanho da senha e selecionar os tipos de caracteres utilizados na geração, integrando uma interface web a um backend em Python por meio de uma API REST.

## Tecnologias utilizadas

- **Python 3:** lógica de geração das senhas.
- **Flask:** criação do servidor e da API.
- **Flask-CORS:** suporte à comunicação entre diferentes origens.
- **HTML5:** estrutura da interface.
- **CSS3:** estilização e organização visual.
- **JavaScript:** interatividade e comunicação com o backend.
- **Random:** seleção aleatória de caracteres.

## Funcionalidades

- Definição do tamanho da senha.
- Utilização de letras maiúsculas e minúsculas.
- Inclusão de números.
- Inclusão de símbolos.
- Geração de senhas conforme as opções selecionadas.
- Validação para impedir a geração sem selecionar uma categoria de caracteres.
- Comunicação entre frontend e backend por meio de uma API REST.
- Exibição da senha gerada diretamente na interface.

## Requisitos

Para executar o projeto, é necessário ter:

- Python 3 instalado.
- Um navegador atualizado.
- Visual Studio Code ou outro editor de código (recomendado).

## Instalação e execução

### 1. Clonar o repositório

Abra o terminal e execute:

```bash
git clone https://github.com/EdeNet00/GeradorDeSenhasEmPython.git
```

Entre na pasta do projeto:

```bash
cd GeradorDeSenhasEmPython
```

### 2. Instalar as dependências

Instale o Flask e o Flask-CORS com o seguinte comando:

```bash
python -m pip install flask flask-cors
```

No Windows, caso o comando `python` não funcione, tente:

```powershell
py -m pip install flask flask-cors
```

### 3. Iniciar o servidor

Execute o arquivo responsável pelo backend:

```bash
python senhas.py
```

Se a inicialização ocorrer corretamente, o servidor ficará disponível no endereço:

http://127.0.0.1:5000

Mantenha o terminal aberto enquanto utilizar a aplicação.

### 4. Abrir a interface

Abra o arquivo `index.html` no navegador.

O JavaScript fará a comunicação com o servidor Flask para enviar as configurações e receber a senha gerada. Por isso, o backend precisa estar em execução para que a funcionalidade principal opere corretamente.

## Funcionamento da aplicação

O funcionamento ocorre nas seguintes etapas:

1. O usuário acessa a interface web.
2. Define o tamanho desejado para a senha.
3. Seleciona se deseja utilizar letras, números e símbolos.
4. O arquivo `script.js` coleta as opções selecionadas.
5. O JavaScript envia uma requisição HTTP `POST` para a API Flask.
6. O backend processa as configurações e gera a senha.
7. A API retorna o resultado em formato JSON.
8. A interface recebe a resposta e exibe a senha gerada.

## API

O backend disponibiliza um endpoint para a geração de senhas.

### Gerar senha

| Propriedade | Valor |
|---|---|
| Método HTTP | `POST` |
| Endpoint | `/gerar` |
| Endereço local | `http://127.0.0.1:5000/gerar` |
| Formato de entrada | JSON |
| Formato de resposta | JSON |

### Exemplo de requisição

O frontend envia as configurações selecionadas pelo usuário:

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
| `tamanho` | Quantidade de caracteres desejada |
| `letras` | Define se letras serão utilizadas |
| `numeros` | Define se números serão utilizados |
| `simbolos` | Define se símbolos serão utilizados |

### Resposta de sucesso

Quando a senha é gerada, a API retorna um objeto JSON:

```json
{
  "senha": "aB8@xP2#Lm91"
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

Nesse caso, a resposta utiliza o status HTTP `400 Bad Request`.

## Estrutura do projeto

```text
GeradorDeSenhasEmPython/
├── index.html
├── script.js
├── senhas.py
├── .gitignore
└── README.md
```

### Descrição dos arquivos

- **`index.html`:** contém a estrutura da interface, os campos de configuração e a área de exibição da senha.
- **`script.js`:** controla as interações da página, envia as configurações para a API e apresenta o resultado.
- **`senhas.py`:** implementa o backend em Python, o servidor Flask e a lógica de geração das senhas.
- **`.gitignore`:** define os arquivos e diretórios que devem ser ignorados pelo Git.
- **`README.md`:** documenta o projeto, suas dependências e instruções de execução.

## Interface

A aplicação apresenta uma interface centralizada, com elementos voltados à configuração e à geração de senhas.

Entre os componentes estão:

- Campo para definir o tamanho da senha.
- Opções para selecionar letras, números e símbolos.
- Botão para iniciar a geração.
- Área para exibir a senha resultante.
- Mensagens para indicar erros ou problemas durante a operação.

## Segurança

Este projeto possui finalidade educacional e demonstra conceitos de programação em Python, desenvolvimento web e integração entre frontend e backend.

A implementação utiliza o módulo `random` para selecionar os caracteres. Esse módulo não é recomendado para a geração de senhas que exigem segurança criptográfica. Para aplicações que lidam com credenciais reais, recomenda-se utilizar o módulo `secrets` do Python.

## Objetivo acadêmico

O projeto tem como objetivo praticar lógica de programação em Python, desenvolvimento de interfaces web, criação de APIs com Flask, manipulação de dados JSON e integração entre diferentes componentes de uma aplicação.

## Autor

Desenvolvido por [EdeNet00](https://github.com/EdeNet00).

Projeto desenvolvido para fins educacionais.
