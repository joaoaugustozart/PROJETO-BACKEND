# 1º Etapa: Construir diretório e definir organização do projeto

* Administrar projeto com gitBash
* Anotar etapas e comandos
* Publicar no gitHub

<hr>

#### Construir diretório da aplicação
```
mkdir backendProject
```

#### Entrar no diretório
```
cd backendProject
```

#### Gerar arquivo para documentar o projeto
```
touch documentacao.md
```
* Arquivos com a extensão .md referem-se a markdown, um formato de marcação de texto. A proposta é destacar informações no texto, identificando pontos importantes, links e imagens, sem a necessidade de recorrer a marcações mais elaboradas, como o HTML.

* Utilize este arquivo para registrar as ações realizadas, facilitando a compreensão posterior.

#### Ativar o gerenciador de pacotes Node
```
npm init -y
```
* Será gerado um arquivo package.json no diretório principal do projeto

* Imagem mostrando o resultado do comando no terminal

#### Instalar os pacotes necessários
```
npm i express nodemon dotenv
```
* express: framework web para estruturação da API;
* nodemon: supervisiona alterações nos arquivos e reinicia o servidor Node automaticamente;
* dotenv: controla as variáveis de ambiente do projeto;
* A confirmação da instalação dos pacotes estará visível na seção 'dependencies' do arquivo package.json, como mostrado na imagem a seguir.

#### Iniciar o VSCode
```
code .
```

#### Gerar arquivo .gitignore
```
nano .gitignore
```
* Com o comando nano, é possível criar e editar um arquivo via terminal.
* Ctrl + o: Salvar.
* Enter: Confirmar.
* Ctrl + x: Sair.
* Este arquivo serve para excluir certos arquivos e pastas do envio ao gitHub.

#### No arquivo .gitignore, adicione o nome da pasta gerada após instalação dos pacotes
```
node_modules
```
* Não precisamos enviar a pasta node_modules para o gitHub, pois ela pode ser recriada usando o comando 'npm install'.

#### Formar estrutura de arquivos e diretórios
```
mkdir src
```

#### Gerar arquivos dentro do diretório src
```
touch src/api.js
```
* Arquivo para configurar a API.
```
touch src/servidor.js
```
* Arquivo para receber as configurações e iniciar a API.

#### Criar subdiretórios dentro de src
```
mkdir src/configs
```
* Pasta para controle da conexão com a base de dados.
```
mkdir src/controladores
```
* Pasta para tratar as requisições das rotas e interação com a base de dados.
```
mkdir src/rotas
```
* Pasta para administrar as rotas da API.

#### Verificar organização do projeto

* Certifique-se de que a estrutura do projeto esteja conforme a imagem apresentada.

#### Publicar organização do projeto no gitHub

* Iniciar o gerenciamento de arquivos .git
```
git init
```

* Registrar seu nome e email.
* Substitua 'SEU_NOME' pelo seu nome.
* Substitua 'SEU_EMAIL@EXEMPLO.COM' pelo seu email do gitHub.
```
git config --global user.name "SEU_NOME"
```
```
git config --global user.email "SEU_EMAIL@EXEMPLO.COM"
```

* Verificar arquivos que serão enviados ao gitHub.
```
git status
```

* Incluir todos os arquivos para versionamento.
```
git add .
```
* Salvar projeto com um comentário sobre as ações realizadas.
```
git commit -m 'organização inicial do projeto'
```
* Criar um novo repositório no gitHub.
* Clique no local indicado na imagem para copiar a URL do repositório.

* Voltando ao terminal, defina a branch principal.
```
git branch -M main
```
* Indique o repositório de destino.
* Cole a URL do seu repositório.
```
git remote add origin COLE_A_URL
```
* Envie os arquivos para o gitHub.
```
git push -u origin main
```

### Atualize a visualização no gitHub e confira se os arquivos foram enviados.
* Com o projeto no servidor externo, é possível eliminar os arquivos locais.
```
cd ..
```
* Comando para retornar ao diretório anterior.
* Feche o VSCode com o projeto aberto.

```
rm -rf backendProject
```
* rm (remove): comando para deletar arquivos.
* -r (recursivo): apaga diretórios e subdiretórios.
* -f (força): não solicita confirmações.
* backendProject: nome do diretório com os arquivos do projeto.

# 2º Etapa: Baixar o projeto do gitHub, configurar a API e realizar testes.

* Utilizar o comando clone do git.
* Configurar pacotes.
* Criar comando para iniciar o servidor.
* Testar o servidor.

<hr>

#### Copie a URL do projeto.

* Acesse o repositório do projeto no gitHub.
* Clique no botão verde '<> Código'.
* Clique no ícone para copiar a URL, conforme mostrado na imagem.

#### Baixar o repositório no seu computador.

* Abra o gitBash no local desejado.
* Digite o comando 'git clone' seguido da URL do seu repositório.

```
git clone URL_DO_REPOSITORIO
```

#### Entrar no diretório.
* Use o comando 'cd' seguido do nome do seu repositório.
```
cd NOME_DO_REPOSITORIO
```

#### Reinstalar os pacotes do projeto.
```
npm i
```
* Este comando recriará o diretório node_modules no projeto.

#### Gerar arquivo .env no diretório principal do projeto.
```
nano .env
```

#### Escreva no arquivo .env.
```
PORTA = 3008
```

#### Adicione o arquivo .env ao .gitignore.
```
nano .gitignore
```
```
.env
```

#### Iniciar o VSCode.
```
code .
```

#### Gerar arquivo de amostra para as variáveis do sistema.
```
nano .env.exemplo
```

#### Adicione ao arquivo .env.exemplo.
```
PORTA = 
```

#### Abra o arquivo api.js e adicione o código.
```
const express = require('express');
const dotenv = require('dotenv').config();
const app = express();
app.set('porta', process.env.PORTA || 3333);
module.exports = app;
```

#### Abra o arquivo servidor.js e adicione o código.
```
const api = require('./api');
const

 porta = api.get('porta');
api.listen(porta, () => {
    console.log(`Funcionando na porta ${porta}!`);
});
```

#### Após configurar os pacotes e testar o servidor, vamos criar o comando para iniciá-lo.

#### Abra o arquivo package.json e modifique a seção 'scripts'.
```
"start":"nodemon src/servidor.js"
```

#### Execute o comando no terminal gitBash.
```
