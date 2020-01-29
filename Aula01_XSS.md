# XSS

Cross-Site Scripting, ou XSS, é um ataque realizado em páginas web com o objetivo de inserir nelas código malicioso. O código é executado do lado do cliente, ou seja, pelo navegador e pode ser muito prejudicial, pois ele age como se o usuário estivesse executando as ações.

O código pode ser inserido de diversas formas, seja por parâmeros na url, campos de pesquisa, informações de perfil, comentários, basicamente onde der para escrever existe a possibilidade da vulnerabilidade existir.

Se um usuário acessar uma página de um site de banco que sofre ataque de XSS, o código malicioso pode roubar informações da conta, roubar a sessão (permitindo que o atacante use a conta da vítima) ou até mesmo fazer operações financeira em nome da vítima.

Geralmente, a vulnerabilidade permite a injeção de código HTML, ou seja, tags \<h1>, \<span>, \<script>.

A última tag é a mais perigosa, pois permite a execução de código javascript, permitindo ao atacante se passar pelo usuário, acarretando nos riscos acima descritos.

Sabendo disso, alguns sites filtram a tag \<script>, removendo elas do input. Isso, entretanto, não é suficiente, pois há diversas outras maneiras de executar scripts dentro de uma página, seguem alguns exemplos:

\<IMG SRC=”javascript:alert(‘XSS’);”> \
\<iframe %00 src="&Tab;javascript:prompt(1)&Tab;"%00> \
\<sVg><scRipt %00>alert&lpar;1&rpar; {Opera} \
\&#34;&#62;<h1/onmouseover='\u0061lert(1)'>%00 \
[Ler mais](https://github.com/pgaijin66/XSS-Payloads/blob/master/payload.txt)

## Tipos de XSS

### Refletida (Reflected)

Nesse ataque, o código malicioso não está armazenado no servidor, mas sim inserido na página da vítima temporariamente.

Um exemplo clássico desse tipo de XSS é um site que exibe, de alguma forma, um conteúdo digitado na url

Exemplo 1: https://<span></span>localhost/busca?q=<script>alert(document.cookie)</script>

Exemplo 2: \
![Exemplo2](https://i.imgur.com/tyCSWFd.png) \
Ao clicar em 'Search', o exemplo 1 é retomado


### Persistente (Stored)

O Stored XSS, ao contráio do reflected, guarda o código malicioso no servidor, o que o torna especialmente mais nocivo.

Um exemplo de situação em que ele pode estar presente é em um sistema de comentários. Nesse sistema, o atacante poderia inserir seu código malicioso, e todos que o lessem estariam executando.

### DOM Based



## Fontes
https://www.welivesecurity.com/br/2017/07/07/vulnerabilidade-cross-site-scripting/
https://pt.pmgacademy.com/blog/artigos/tudo-sobre-xss
