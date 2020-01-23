# Procolo HTTP (HyperText Transfer Protocol)

O protocolo HTTP é a base da troca de dados na Web, sendo responsável por transmitir  documentos de hipertexto - como o HTML -, imagens, vídeos e resultados de formulários entre cliente e servidor.

O HTTP é um protocolo _stateless_ (comunicação feita por meio de mensagens individuais) cliente-servidor e segue o seguinte modelo de comunicação: um cliente (geralmente o _browser_) abre uma conexão por meio de uma requisição feita ao servidor, que recebe a requisição e envia uma resposta ao cliente. Entretanto, entre o navegador que faz a requisição e o servidor que envia a resposta existem vários dispositivos tratando e retransmitindo a mensagem (roteadores, modems, computadores e outras máquinas).

## Etapas de comunicação - Fluxo HTTP

Conforme dito anteriormente, a comunicação entre cliente e servidor ocorre por meio de mensagens individuais. Porém, quando um cliente quer comunicar-se com um servidor ele realiza os seguintes passos:
1. **Abrir uma conexão TCP**: essa conexão é utilizada para enviar uma ou várias requisições e receber respostas.

2. **Enviar uma mensagem HTTP**: um detalhe **importantíssimo** do protocolo HTTP é que essa mensagem **não é criptografada**, ou seja, ela pode ser lida por qualquer um que esteja monitorando o fluxo de pacotes da rede. A mensagem segue esse padrão:

<img src="https://i.imgur.com/OxDXcP7.png"/> 

3. **Ler a mensagem de resposta do servidor**: após enviar uma requisição, se não houver problemas, o servidor enviará uma resposta. Essa resposta também **não é criptografada** e segue esse padrão:

<img src="https://mdn.mozillademos.org/files/13691/HTTP_Response.png"/>

4. **Fechar ou reutilizar a conexão TCP que foi aberta**.

## Requisições 

Conforme mostrado nas duas últimas imagens, requisições e a respostas são compostas de certos elementos.

Os **elementos das requsições** são:
- Método HTTP: operação que o cliente deseja fazer;
- O caminho do recurso a ser buscado: em outras palavras, a parte da URL que vem após o ".com", ".br", ".org" etc. (ou seja, a URL sem os elementos de contexto*), indicando a localização do recurso no servidor;
- A versão do protocolo HTTP;
- Headers opcionais: são cabeçalhos que contém informações adicionais para os servidores, como cookies, data, linguagem aceita, tamanho da requisição e outros. Headers padrões podem ser encontrados [aqui](https://flaviocopes.com/http-request-headers/);
- Corpo de dados: contém o recursos requisitado. Normalmente, eles vêm em respostas, mas também se fazem presentes em requisições do tipo `POST` por exemplo.

E os **elementos das respostas** são:
- Versão do protocolo HTTP seguida pelo servidor;
- Código de status: indica se a requisição foi bem sucedidade ou não (e o porquê);
- Mensagem de status: breve descrição do código de status;
- Cabeçalhos HTTP: igual aos da requisição
- Corpo com dados do recurso requisitado (se algo foi requisitado)

<i style="background-color: yellow; font-size: 15px;"> * Elementos de contexto são coisas como: protocolo (`http://`), domínios e subdmínios (`www.google.com`) e a porta da conexão TCP (após a URL pode vir um`:80` por exemplo) </i>

### Tipos de requisições (métodos HTTP)
As requisições HTTP podem ser de vários tipos, indicando a ação que deve ser realizada com determinado conteúdo. Os principais tipos são **`GET`** e **`POST`**, mas também há: **`HEAD`**, **`PUT`**, **`DELETE`**, **`CONNECT`**, **`OPTIONS`**, **`TRACE`**, **`PATCH`**.
- **`GET`** é utilizado para requisitar certo conteúdo (normalmente a apresentação desse conteúdo no navegador). Esse método serve para reaver/solicitar dados.
- **`POST`** é utilizado para enviar algum conteúdo para o servidor (como os dados de um formulário preenchido ou uma tentativa de login).

### Respostas HTTP (status codes)
Os códigos de status presentes em respostas HTTP (_HTTP responses_) indicam se a requisição foi realizada com sucesso ou não. Esses códigos são divididos em:
- Informational responses (100–199),
- Successful responses (200–299),
- Redirects (300–399),
- Client errors (400–499),
- Server errors (500–599).

### Os códigos que mais aparecem são:
- **`200` `OK`**: a requisição foi um sucesso, ou seja, o conteúdo da requisição foi obtido ou transmitido sem erros.
- **`301` `Moved Permanently`**: código de redirecionamento indicando que a recurso solicitado  foi movido permanentemente para outro local - indicado no _header_ `Location`. O _browser_ é redirecionado para lá automaticamente. O código 308 funciona da mesma forma.
- **`302` `Found`**: código de redirecionamento indicando que o conteúdo procurado está temporáriamente em outro local - também indicado no _header_ de resposta `Location`. O _browser_ é redirecionado para lá automaticamente. O código 307 funciona da mesma forma.
- **`400` `Bad Request`**: erro de sintaxe na requisição, ou seja, o servidor não conseguiu processar bem a requisição.
- **`401` `Unauthorized`**: requisição não autorizada. O cliente precisa se autenticar (ex.: fazer login) para conseguir o acesso ao que foi requisitado.
- **`403` `Forbidden`**: o cliente não pode acessar o conteúdo solicitado, ou seja, ele não está autorizado a ver certa informação (mesmo que autenticado - o servidor sabe a identidade do cliente).
- **`404` `Not Found`**: o servidor não encontrou o que foi requisitado - e o conteúdo buscado provavelmente não existe. Em _browsers_, isso significado que a URL passada não foi reconhecida.
- **`500` `Internal Server Error`**: erro interno do servidor, ou seja, o servidor está com problemas para lidar com certa situação.
- **`502` `Bad Gateweay`**: erro que indicado que o servidor, atuando como gateway (buscando a resposta para retransmitir ao cliente), recebeu uma resposta inválida.
- **`503` `Service Unavailable`**: o servidor não está pronto para processar a requisição. Normalmente, isso indica que o servidor está desligado ou sobrecarregado.

## Cookies e sessões
### [ ESCREVER AQUI DEPOIS ]

Como o HTTP não mantém estados, _cookies_ HTTP permitem que as sessões tenham estados. Usando a extensibilidade dos cabeçalhos, os cookies são adicionados ao fluxo do HTTP, permitindo que a criação de sessão em cada requisição HTTP compartilhem o mesmo contexto, ou o mesmo estado.

https://klauslaube.com.br/2012/04/05/entendendo-os-cookies-e-sessoes.html

---

Mais coisas:
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

https://developer.mozilla.org/en-US/docs/Tools

---

# Procolo HTTPS (Hyper Text Transfer Protocol Secure)

O HTTPS é uma implementação do HTTP com uma camada adicional de segurança: o **protocolo SSL/TLS**. Isso permite que os dados sejam transmitidos por meio de uma conexão **criptografada** e que verifica a autenticidade do servidor e do cliente por meio de **certificados digitais**.

A porta TCP normalmente utilizada para o HTTPS é a 443, enquanto a para o HTTP é a porta 80.

O HTTPS serve para criar um canal seguro sobre uma rede insegura - dado que o algoritmo de criptografia utilizado é bom e o certificado do servidor é confiável -, dificultando que pessoas "escutando" na rede (por meio de ataques como _man-in-the-midde_ ou algum tipo de _spoofing_) possam capturar e enteder pacotes que não são deles ou fingir serem quem não são.

A "confiança" fornecida pelo HTTPS é baseada em **autoridades de certificação** que vêm pré-instaladas no navegador

## Protocolo TLS/SSL
O TLS (Transport Layer Security) é o sucesso do SSL (Secure Sockets Layer). Ambos são protocolos de segurança usado em comunicações sobre redes de computadores.

Em se tratando do TLS, o protocolo visa fornecer privacidade e integridade de dados entre duas aplicações que se comuniquem pela internet. Isso ocorre meio da **autenticação do servidor e/ou do cliente** e da **cifragem dos dados** transmitidos.

_Lembrando que isso não torna a conexão necessariamente segura_, mas sim menos insegura...

### Cifragem dos dados

O protocolo TLS usa [criptografia de chave simétrica](https://pt.wikipedia.org/wiki/Algoritmo_de_chave_sim%C3%A9trica) para criptografar os dados transmitidos. As chaves são únicas para cada conexão e trocadas por meio de um Handshake TLS no começo da comunicação (o handshake usa criptografia assimétrica).

#### Handshake TLS
Ao estabelecer uma comunicação cliente-servidor, a primeira operação que ocorre é o Handshake para determinar como o resto da comunicação será feita.

Esse handshake determina qual cifra de encriptação será usada, verifica a identidade/confiabilidade do servidor e, por fim, estabelece uma canal de comunicação criptografado.

O processo de handshake segue o fluxo abaixo:
1. Cliente manda uma mensagem para o servidor pedindo para estabelecer um canal de comunicação criptografado (passa nos headers a lista de cifras que ele aceita e a versão do protocolo TLS que ele aceita usar);
2. Servidor resposte com a cifra e a versão do TLS que será usada. Também envia um certificado digital (que autentica sua confiabilidade e permite a comunicação com HTTPS) junto de sua chave pública (criptografia assimétrica);
3. Cliente verifica o certificado do servidor e extrai sua chave pública. Em seguida, ele usa essa chave para encriptar uma "pre-master key" e a envia para o servidor;
4. Servidor usa sua chave privada para decriptar a "pre-master key";
5. Cliente e servidor usam a "pre-master key" para gerar uma chave secreta compartilhada;
6. Cliente envia uma mensagem criptografada (com a chave secreta compartilhada) e avisa que a partir daquele momento, toda a comunicação será feita dessa forma;
7. Servidor decripta a mensagem e, se tudo correr conforme o esperado, ele envia uma última mensagem criptografada (com a chave secreta compartilhada) avisando que ele foi capaz de descriptografar a mensagem do cliente e que, a partir desse momento, todas as mensagem serão enviadas dessa forma (criptografas com essa chave);
8. Pronto! O resto da comunicação é feita usando a chave secreta compartilhada até o fim da sessão.

- A conexão é confiável porque cada mensagem transmitida inclui uma verificação de integridade de mensagem usando um código de autenticação de mensagem para evitar perda não detectada ou alteração dos dados durante a transmissão.

## Certificados digitais e autoridades cerificadoras


