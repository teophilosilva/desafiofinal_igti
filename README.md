# desafiofinal_igti
Desafio FInal do curso Desenv FullStack IGTI

Dicas importante sobre a integração MongoDB Atlas com Heroku e comandos GIT e GITHUB

.gitignore

Para evitar de enviar informações sensiveis ao servidor github é necessário criar variáveis de ambiente
Criar variaveis
1. Instalar pacote npm install dotenv
2. Importar no arquivo require('dotenv').config(); // Condição para buscar local ou do arquivo if(process.env.PRD !=='true'require('dotenv').config();
3. Criar no projeto um arquivo .env (ex: USERDB=igti) e coloque no .gitignore
4. Crie um arquivo sample-env para definir quais variaveis vazias do .env

git init
git add * se for só os alterados git add -A

git status (ver arquivos no index)

commit -am "Mensagem"

Criar BRANCH
git checkout -b "Nome da Branch"

Criar um Novo Branch
git checkout -b "Novo Branch"

Apagar Branch
git branch -d "Nome do  Branch"

Voltar para Master
git checkout master

Ir para BRANCH criado
git checkout Nome da Branch

Consultar BRANCH
git branch

Aplicar BRANCH criado no Master
1. Ir para Branch MASTER
2. Comando git merge Nome da Branch

Ver logs 
git log

Enviar para repositorio local
git push -u origin  "Nome do Branch"

COMANDOS GITHUB

git remote add origin https://github.com/teophilosilva/meusprojetosweb.git
git push -u origin master

Atualizar Local com remoto
git pull

Trazer os Branchs remotos para local
git fetch origin


INSTALAÇÃO DO HEROKU no DEBIAN

##Melhor resultado pelo curl
Usar conta do como root
curl https://cli-assets.heroku.com/install.sh | sh
##CRIAR LINK SIMBÓLICO PARA COMANDO
ln -s  /usr/local/bin/heroku /bin/
##USO DO HEROKU CLI
1.heroku login
##Será aberta a página do heroku na web para você se autenticar. Após isso o CLI exibe a mensagem logado.
##Criar uma instância (como se fosse o git init)
2.heroku create
##Ver pelo git as instâncias remotas criadas
3.git remote -v
##Enviar projeto para heroku (como se fosse o git push -u origin master)
4.git push heroku master
##Criar uma estância na WEB pelo Heroku
5.heroku ps:scale web=1
##Se quiser parar uma instância existente o comando é:
heroku ps:scale web=0
##Acessar a aplicação
6.heroku open
##Ele vai dar um erro porque o comando que usa para startar é o NPM START e o que enviamos é a API. 
##Resolve criando na raiz do projeto um arquivo chamado procFile e atribui a ele o seguinte texto 
web: node app.js
##Após isso é necessário commitar novamente o projeto
git commit -a -m "Adiciona procfile para Heroku"
##Depois
git push -u origin master
##Depois 
git push heroku master
##Depois
heroku open
##Ver as variáveis do HEROKU
heroku config

Em deploy no heroku você pode integrar o heroku a seu deploy no github. Basta autorizar por lá.

Obs: É necessário enviar para commit o arquivo .env para que o Heroku após receber os arquivos funcionar ou criar variáveis de ambiente por lá.

As vezes o número de visualizações é grande sendo necessário alterar alguma configuração
(ERRO System limit for number of file watchers )
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

No caso de deploy de projeto React seguir os passos abaixo antes de enviar

1.heroku buildpacks -a <appname>
2.heroku buildpacks:set mars/create-react-app -a <appname>
3.deploy

