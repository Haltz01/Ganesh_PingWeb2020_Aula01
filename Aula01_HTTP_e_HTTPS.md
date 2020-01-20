# Procolo HTTP (HyperText Transfer Protocol)

O protocolo HTTP é a base da troca de dados na Web, sendo responsável por transmitir  documentos de hipertexto - como o HTML -, imagens, vídeos e resultados de formulários para o servidor.

O HTTP é um protocolo _stateless_ (comunicação feita por meio de mensagens individuais) cliente-servidor e segue um modelo de comunicação: um cliente (geralmente o _browser_) abre uma conexão por meio de uma requisição feita ao servidor, que recebe a requisição e envia uma resposta ao cliente. Entretanto, entre o navegador que fez a requisição e o servidor que envia a resposta existem vários dispositivos tratando e retransmitindo a mensagem (roteadores, modems, computadores e outras máquinas).

## Etapas de comunicação por meio do HTTP

https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Overview

## Requisições 

https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

### GET


### POST

## Respostas HTTP (status codes)
Os códigos de status presentes em respostas HTTP (_HTTP responses_) indicam se a requisição foi realizada com sucesso ou não. Esses códigos são divididos em:
- Informational responses (100–199),
- Successful responses (200–299),
- Redirects (300–399),
- Client errors (400–499),
- Server errors (500–599).

Os códigos que mais aparecem são:
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

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

https://developer.mozilla.org/en-US/docs/Tools

## Cookies e sessões
### [ ESCREVER AQUI DEPOIS ]

Como o HTTP não mantém estados, _cookies_ HTTP permitem que as sessões tenham estados. Usando a extensibilidade dos cabeçalhos, os cookies são adicionados ao fluxo do HTTP, permitindo que a criação de sessão em cada requisição HTTP compartilhem o mesmo contexto, ou o mesmo estado.

https://klauslaube.com.br/2012/04/05/entendendo-os-cookies-e-sessoes.html

