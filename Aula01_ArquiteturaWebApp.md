# Internet e Web

Imagine que a Internet é uma imensa loja de livros e a Web é uma coleção de livros presente nessa loja.

De forma simples, a Internet é uma rede global de redes, conectando milhões de dispositivos através de: email eletrônico, compartilhamento de arquivos (via FTP), jogos online, aplicativos mobile, Web etc. 

Já a Web (World Wide Web) representa um conjunto de informações acessado via Internet por meio de Hyperlinks - referenciando URIs ([Uniform Resource Identifier](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)). Ou seja, a Web é uma rede presente na Internet. Os recursos presentes na Web são normalmente acessados por meio de navegadores (Chrome, Firefox, Safari etc.), fazendo uso do protocolo HTTP ou HTTPS.

Os recursos na Web costumam ser apresentados na forma de _web pages_ - que formam _websites_. Essas páginas são criadas e estilizadas por meio de linguagens como HTML, CSS e Javascript, principalmente - sendo possível utilizar também outras, como PHP e Python.

# Arquitetura de uma aplicação Web

![Arquitetura de uma aplicação Web: front-end e back-end](https://github.com/Haltz01/Ganesh_PingWeb2020_Aula01/blob/master/arquitetura_web_back_front.png "Arquitetura de um web app")

Em uma aplicação Web, há dois tipos de "sub-programas", um client-side e outro server-side. O código client-side (HTML, CSS e Javascript) é o que está na página do navegador e interage com as entradas do usuário. Já o código server-side está em um servidor e responde às requisições HTTP que chegam até ele. Para o código client-side, pode-se utilizar C#, Java, Javascript, Python, PHP, Ruby e mais - basicamente, qualquer linguagem que entenda e responda requisições HTTP.

## Componentes estruturais

Esses componentes são responsáveis pela funcionalidade da aplicação web com a qual o usuário interage e pelo controle, tratamento e armazenamento dos dados passados para o servidor. 

Esses componentes englobam:
    - Páginas web + navegador (_browser_); -> client-side
    - Servidor da aplicação web; -> server-side
    - Servidor do banco de dados. -> server-side
_Obs.: o servidor da aplicação e do banco de dados podem ser a mesma máquina.

### Navegador e páginas web
O navagador web permite que o usuário interaja com as funções das aplicações web e as páginas por ele exibidas são geralmente desenvolvidas usando HTML, CSS e Javascript.

### Servidor da aplicação Web 
O servidor da aplicação é responsável por tratar as requisições que chegam dos cliente, "chamar" APIs, fazer requisições para bancos de dados e enviar respostas aos clientes (na forma de páginas Web, arquivos, JSONs etc.). Esse servidor pode ser desenvolvido em Python, PHP, Java, .NET, Ruby, Node.js...

### Servidor do banco de dados
O banco de dados é responsável por armazenar dados - como informações de login de usuários ou itens de uma loja - de forma persistente e no server-side. Além de armanenar esses dados, ele é capaz de fazer buscas e retornar informações para o servidor da aplicação Web utilizar e possivelmente devolver ao cliente.

## Entendo o "fluxo" de informação do front-end

Primeiramente, ao digitar a URL de um site, o navegador deve convertê-la em um endereço IP. Esse processo é chamado de "name resolution" e é realizado através de um DNS (Domain Name System), que faz a associação `hostname da URL:endereço IP`.

Em seguida, o navegador fará uma requisição para o servidor referente ao endereço IP encontrado no primeiro passo. Essa requisição, em geral, será um `GET` solicitando a página web especificada na URL ou um `POST` enviando dados que serão usados pelo back-end do servidor.

Como resposta, o servidor (back-end) enviará arquivos e informações do tipo HTML, CSS, JS, PHP, JSON, JPG e possivelemnte outros. Esses arquivos são tratados pelo navegador, que é responsável por exibí-los ao usuário, e pelo código da página web presente no front-end. Além disso, podem haver _headers_ importantes nesses arquivos, contendo, por exemplo, informações sobre a sessão atual.

Além disso, vale destacar que o SO do cliente é responsável por fazer as requisições saírem do navegador em direção à Internet e recuperar as respostas vindas do servidor pela Internet. O sistema operacional expõe o computador à rede através de certas portas, que permitem a troca de informação via HTPP/HTTPS e outros.