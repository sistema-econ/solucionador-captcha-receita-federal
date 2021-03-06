# Solucionador de captcha da receita federal

### Requisitos
* NodeJS >= 6
* Python
* RScript
* openssl-dev
* libcurl-dev
* libhdf5-dev
* libmagick++-dev (Não necessário para Windows)

### Instalação
Crie uma pasta para baixar o projeto e clone o projeto usando
```
git clone https://github.com/baragatti/solucionador-captcha-receita-federal.git
```

Após o término do download, navegue com o terminal até a pasta e execute o npm para instalar as dependências
```
npm install
```

Instale as dependências do Python
```
pip install -Iv tensorflow==1.5.0 keras virtualenv h5py --user
```

E, finalmente, instale dependências da linguagem R
```
rscript install.R
```

Para testar se as dependências foram instaladas corretamente, vá até a pasta do projeto, e execute o comando
```
rscript test.R
```
Deverá ser exibido no console uma mensagem contendo o resultado "tkozf6"

### Configuração
No momento a configuração do projeto é bem simples, contendo apenas parâmetros estritamente necessários.

A configuração se encontra no arquivo config.json, conforme exemplo abaixo
```json5
{ 
  "porta": 8080 // Porta utizada pelo servidor
}
```

### Rodando o projeto
Para deixar o microservice rodando, basta executar o comando
```
node index.js
```
### Como usar

#### Endpoint /solucionar
Basta enviar uma requisição REST, como POST, para o endpoint, enviando o arquivo de imagem no parâmetro "arquivo".

O resultado é retornado sempre em JSON, e retornará com código de status do HTTP 200 em caso de sucesso.

#### Endpoint /solucionar-base64
Basta enviar uma requisição REST, como POST, para o endpoint, enviando o arquivo de imagem como base64 no parâmetro "arquivo".

O resultado é retornado sempre em JSON, e retornará com código de status do HTTP 200 em caso de sucesso.

#### Exemplo de retorno com sucesso
```json
{ "resultado": "abcdef" }
```

#### Exemplo de retorno com erro
```json
{ "erro": "Descrição do erro" }
```
