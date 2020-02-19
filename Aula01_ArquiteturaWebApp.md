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

## Entendo o "funcionamento" do front-end

A partir da imagem a seguir, iremos entender os componentes do que conhecemos como "front-end" e quais suas respectivas funções e importâncias para o funcionamento de uma aplicação Web.