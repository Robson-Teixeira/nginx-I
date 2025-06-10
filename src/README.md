## Instalações

### Linux

```bash
sudo apt install nginx
```

### MacOS

```bash
brew install nginx
```

### Windows
Para Windows, você pode baixar o Nginx do site oficial: [nginx.org](https://nginx.org/en/download.html). Após o download, extraia o conteúdo do arquivo ZIP e execute o arquivo `nginx.exe` na pasta extraída.

> Todo sistema operacional possui um arquivo de hosts. No Linux, por padrão fica em /etc/hosts. No Mac, /private/etc/hosts. Já no Windows, C:\Windows\System32\Drivers\Etc\hosts. Esse arquivo informa ao sistema operacional que quando uma conexão for estabelecida usando algum nome, o IP correspondente deve ser usado. Para o nome localhost, temos o IP da nossa própria máquina (127.0.0.1).

## Comandos

- `start nginx` iniciar o Nginx
- `stop nginx` parar o Nginx
- `restart nginx` reiniciar o Nginx
- `nginx -h` exibir ajuda do Nginx
- `nginx -s reload` recarregar a configuração do Nginx sem parar o serviço
- `nginx -t` testar a configuração do Nginx para verificar se há erros

## Configuração
O arquivo de configuração do Nginx geralmente está localizado em `/etc/nginx/nginx.conf` no Linux e MacOS, e no diretório onde o Nginx foi instalado no Windows.

- `worker_processes  1` número de processos de trabalho
- `events { worker_connections 1024; }` número máximo de conexões simultâneas por processo de trabalho
- `http { ... }` bloco de configuração HTTP
    - `include /etc/nginx/mime.types;` inclui tipos MIME
    - `default_type application/octet-stream;` tipo MIME padrão
    - `sendfile on;` ativa o envio de arquivos
    - `keepalive_timeout 65;` tempo limite de conexão
    - `gzip on;` ativa a compressão gzip
    - `server { ... }` bloco de configuração do servidor
        - `listen 8080;` porta que o servidor irá escutar
        - `server_name localhost;` nome do servidor
        - `location / { ... }` bloco de configuração para a localização raiz
        - `root /var/www/html;` diretório raiz onde os arquivos estão localizados
        - `index index.html index.htm;` arquivo padrão a ser servido

> Proxy reverso é uma técnica onde um servidor atua como intermediário para solicitações de clientes, encaminhando-as para outro servidor. O Nginx pode ser configurado como um proxy reverso para encaminhar solicitações para um servidor de aplicativos, como Node.js, Python, etc. Além disso, o Nginx pode ser usado para balanceamento de carga, cache de conteúdo estático e muito mais.

> API Gateway é um padrão de design que atua como um ponto de entrada único para um conjunto de serviços. O Nginx pode ser configurado como um API Gateway para gerenciar solicitações, autenticação, roteamento e outras funcionalidades relacionadas a APIs.