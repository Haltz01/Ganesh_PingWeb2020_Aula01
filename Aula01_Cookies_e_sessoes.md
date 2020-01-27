# Cookie e Sessão


## Cookies

_Cookies_ são pequenos fragmentos de informação que um site pode armazenar no computador do usuário para uso posterior. Eles se mostram úteis, uma vez que 
a conexão HTTP não apresenta nenhum meio de tornar as informações de uma conexão persistente. Se dependêssemos apenas das conexões HTTP, seria impossível usar um carrinho de compras, pois ao trocar para a página de compra, as informações seriam perdidas.

Em um site de jogos de navegador, é muito comum que o progresso do jogo seja salvo em _cookies_ no navegador. Os _cookies_ também são bastante usados para armazenar configurações do cliente como volume do player de música ou vídeo, cor do fundo do site, etc.

Geralmente, os navegadores limitam o tamanho que um _cookie_ pode ter para 4KB, além de apagar _cookies_ que já tiveram sua validade vencida.

Exemplo de _cookie_ feito pelo PHP.
```php
<?php
    // cookies.php

    if (isset($_COOKIE['cookie_teste'])) {
        echo 'Você JÁ passou por aqui!';
    } else {
        echo 'Você NUNCA passou por aqui.'; 
        //Pode ser que você tenha passado há uma hora, mas o servidor não tem como saber
        setcookie('cookie_teste', 'Algum valor...', time() + 3600);
    }
?>
```
Retirado de https://klauslaube.com.br/2012/04/05/entendendo-os-cookies-e-sessoes.html.

Esse código implementa um conceito similar a sessão (mas ainda não é uma sessão), de forma que um certo conteúdo pode ser exibido de acordo com o intervalo de tempo desde a última visita. O _cookie_ no código possui uma hora de vida (3600 segundos).

Um _cookie_ é de acesso limitado ao site que o criou, de modo a garantir que um site mal intencionado não roube os _cookies_ que o site do seu banco armazenou no seu computador.

## Sessões

Agora, ao que nos interessa, **os _cookies_ podem ser usados como forma de autenticação**, geralmente armazenando o id de uma **sessão**. É graças às sessões que é possível se logar em sites de redes sociais apenas uma vez em muito tempo. Quando o usuário se conecta, uma sessão é iniciada e o id dessa sessão é salvo em um _cookie_ em seu computador. Este será usado mais tarde para informar ao servidor que o usuário já possui um sessão ativa. A maioria dos sites que implementa esse recurso estabelece uma data de expiração da sessão, de modo a invalidar o id salvo no _cookie_.

A grande diferença aqui é que **a sessão é armazenada no servidor**, enquanto **o _cookie_ é armazenado localmente**.

Exemplo de sessão em PHP

```php
<?php
    // sessions.php

    session_start();

    if (isset($_SESSION['usuario'])) {
        echo "Bem vindo {$_SESSION['usuario']}!";
    } else {
        echo 'Você NUNCA passou por aqui.';
        $_SESSION['usuario'] = 'João';
    }
?>
```
Retirado de (https://klauslaube.com.br/2012/04/05/entendendo-os-cookies-e-sessoes.html)

## Falhas

### Uso inocente de _cookies_

É necessário saber como usar os _cookies_. Um exemplo exagerado de mau uso seria um site que lê e salva um _cookie_ `admin=1` para admins e `admin=0` para usuários normais. Na primeira conexão o _cookie_ não existe, então o site manda o browser salvar `admin=0`. Quando o usuário entra com uma conta de administrador, o site manda o browser mudar para `admin=1` e o site exibe conteúdo que não era visível. Lindo, não?
O problema com essa forma de autenticação é que bastaria o usuário editar o próprio _cookie_ e alterar o conteúdo para se tornar administrador do site, burlando todo o sistema de segurança.

### Session Hijacking (Sequestro de Sessão)

Certo, essa foi uma falha bem besta, mas e se em vez de `admin=0`, o _cookie_ fosse `PHPSESSID=somesessionid`, _cookie_ identificador de uma sessão legítima?

Basta alguém conseguir ler esse _cookie_, que terá acesso à conta atrelada à sessão. Esse ataque é chamado de **Session Hijacking** ou Sequestro de Sessão.

Não tem como evitar que alguém que tenha acesso físico ao seu computador com o navegador aberto na página obtenha sua sessão, mas se ele chegou a esse ponto ele já tem controle total.

O que é possível é evitar que pessoas mal intencionadas obtenham sua sessão por meio de outros ataques, como **MITM (Man-In-The-Middle**), **XSS (Cross-Site-script)**. O primeiro ataque é descrito basicamente com o atacante entrando no meio da conexão não encriptada (HTTP) e lendo todo o tráfego entre você e o site, incluindo os _cookies_ enviados e sua sessão. O segundo ataque resume-se no atacante injetar código na página de aluguma forma (!!!!!Ler mais sobre XSS), esse código injetado pode ler e modificar o conteúdo dos _cookies_ armazenados.

## Remediações

* Ataque MITM: criptografar a conexão, usando HTTPS (Ler mais)
* Ataque XSS: definir os _cookies_ com a política HTTP-Only (Ler mais)

## Extras

### CSP
CSP - Content Security Policy - é um _header_ na conexão HTTP ou HTTPS que indica ao navegador diversas medidas de segurança, visando à blindagem contra XSS.

#  [ Continuar Escrevendo ]
### CORS

# [ Escrever ]


## Fontes
https://klauslaube.com.br/2012/04/05/entendendo-os-cookies-e-sessoes.html

---

Mais coisas:
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

https://developer.mozilla.org/en-US/docs/Tools

---
