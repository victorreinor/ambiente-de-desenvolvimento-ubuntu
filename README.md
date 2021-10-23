## Ferramentas essenciais

### Google Chrome

Para instalar o Google Chrome a partir do terminal, precisamos baixar o arquivo DEB usando o comando wget:

`wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`

Agora podemos usar o dpkg para instalar o Chrome a partir do arquivo DEB baixado:

`sudo dpkg -i google-chrome-stable_current_amd64.deb`

### Memoria Swap

Um computador tem essencialmente dois tipos de memória: a memória RAM e a memória de armazenamento em disco. A memória RAM é volátil, mas é a mais rápida de um sistema. No entanto, comparativamente à memória de armazenamento (memória em disco), a memória RAM é mais cara e de menor dimensão.

No Linux podemos ter uma partição Swap que permite usar memória de armazenamento do disco como se fosse memória RAM (obviamente sendo mais lenta). 

**1 – Obter informação sobre a partição/memória Swap:**

Para saber o tamanho da partição Swap e saber quanta memória está em uso basta que use o comando:

`sudo swapon --show`

**2 – Criar um ficheiro Swap no Ubuntu:**

Vamos agora criar um ficheiro Swap usando o comando fallocate. Para este exemplo, estamos a definir um ficheiro com 8GB.

`sudo fallocate -l 8G /swap.img`

**4 – Ativar o ficheiro swap no Ubuntu:**

Para ativar o ficheiro Swap vamos primeiro definir as permissões necessárias (chmod 600, permissões de read e write para o utilizador). 

`sudo chmod 600 /swap.img`

Em seguida use os seguintes comandos para definir o tamanho reservado como Swap e para dar indicações da sua inicialização:

`sudo mkswap /swap.img`

`sudo swapon /swap.img`

Para verificarem se a 'nova memória' já está em uso, execute o seguinte comando:

`sudo swapon --show`

**5 – Montar Swap de forma no Ubuntu:**

As configurações anteriormente são temporárias e para a sessão. Para que se tornem permanentes, ou seja, aplicadas assim que o sistema inicie, devem adicionar uma entrada ao ficheiro /etc/fstab.

`echo '/swap.img none swap sw 0 0' | sudo tee -a /etc/fstab`

https://pplware.sapo.pt/linux/dica-linux-como-aumentar-a-memoria-swap-do-sistema/

### Adicionar GIT

`sudo apt-get install git`

A primeira coisa que você deve fazer ao instalar Git é configurar seu nome de usuário e endereço de e-mail. Isto é importante porque cada commit usa esta informação, e ela é carimbada de forma imutável nos commits que você começa a criar:

`git config --global user.name "Fulano de Tal"`

`git config --global user.email fulanodetal@exemplo.br`

### Gerar e adicionar SSH (GIT)

Gerar SSH

https://docs.github.com/pt/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

Adicionar SSH

https://docs.github.com/pt/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account

### Adicionar Terminal ZSH

https://blog.rocketseat.com.br/terminal-com-oh-my-zsh-spaceship-dracula-e-mais/

### Adicionar Postgres

Instale as libs e postgres:

`sudo apt-get install make python g++ libpq-dev postgresql postgresql-contrib -y`

Alterar a senha padrão do postgres:

`sudo -i -u postgres`

`psql`

`ALTER USER postgres WITH PASSWORD 'test';`

`\q`

`exit`

### Adicionar NVM

Instale o NVM:

`wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`

Agora é necessário adicionar um script para as variaveis de ambiente do NVM:

Adicione no seu profile file (~/.bash_profile, ~/.zshrc, ~/profile ou ~/.bashrc)

`export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm`

### Adicionar fonte Fira Code

https://github.com/tonsky/FiraCode/releases

### Adicionar Visual Studio Code (vscode) e configuração

Instale o vscode:

`sudo snap install --classic code`

(Opcional)
Agora abra o vscode e vá até settings.json

copie e cole as configurações a seguir:

https://github.com/victorreinor/ambiente-de-desenvolvimento-ubuntu/blob/main/settings.json

### Slack

`sudo snap install slack --classic`

### Gitg

Mostra as informações relacionadas a cada commit e os arquivos nas árvores dos repositorios.

`sudo apt-get update`

`sudo apt-get install gitg`

## Ferramentas complementares

### Adicionar Peek

Grava uma seleção de sua tela para uma imagem GIF animada

`sudo add-apt-repository ppa:peek-developers/stable`

`sudo apt update`

`sudo apt install peek`

### Adicionar Shutter

É uma ferramenta gratuita de captura de tela, com diversos recursos de edição.

`sudo apt-add-repository ppa:shutter/ppa`

`sudo apt-get update`

`sudo apt-get install shutter`

### Adicionar Flameshot (Alternativa leve para Shutter)

É uma ferramenta gratuita de captura de tela, com diversos recursos de edição.

`sudo snap install flameshot`

### Adicionar Spotify

`sudo snap install spotify`

### Adicionar Plank Dock (Opcional)

`sudo add-apt-repository -y ppa:ricotz/docky`

`sudo apt-get update`

`sudo apt-get install plank`

**Desabilitar a barra lateral**

`sudo apt install gnome-tweak-tool`

Extensões -> Ubuntu Dock -> Disable

### Sticky Notes

Para instalar o Sticky Notes no Ubuntu e derivados, faça o seguinte:

`sudo apt-add-repository ppa:umang/indicator-stickynotes`

`sudo apt-get update`

`sudo apt-get install indicator-stickynotes`
