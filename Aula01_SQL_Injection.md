# SQL Injection

É uma vulnerabilida web que permite o atacante interferir nas _queries_ (consultas) feitas para o banco de dados de certa aplicação. 

Em geral, o atacante consegue visualizar dados armazenados no bando de dados que não pertencem a ele (informação de outros usuários, dados da aplicação, senhas etc.). Além disso, pode ser que o atacante consiga modificar e deletar dados do DB e, em casos mais extremos, escalar o ataque para comprometer o funcionamento do back-end da aplicação ou performar um ataque DoS. De forma similar, ele pode subverter a lógica de certas aplicações e, por exemplo, passar pelo portal de login de algum site sem ter uma conta.

## Tipos de SQL Injections e exemplos

Vulnerabilidades desse tipo apresentam-se nas mais diferentes formas. Para cada situação de ataque, é possível que haja uma abordagem diferente.

Usaremos como base os exemplos da [Portswigger](https://portswigger.net/web-security/sql-injection), a fim de explicar um pouco sobre diferentes tipos de SQL Injections.

### Exemplo 1: modificando uma query para obter dados adicionais
Considere uma aplicação que distribui seus produtos em categorias. Quando o usuário clica na categoria "Presentes", o navegador manda uma requisição para o servidor da forma:
```
https://insecure-website.com/products?category=Gifts
```

Em seguida, a aplicação fará uma consulta no banco de dados, buscando os produtos da categoria "Presentes". A _query_ utilizada seria, por exemplo:
``` SQL
SELECT * FROM products WHERE category = 'Gifts'
```

Essa consulta quer obter todas as informações (*), ou seja, todas as colunas da base de dados, referentes à tabela "products" nas quais a categoria do produto ("category" é uma das colunas) é "Gifts".

Considerando que a aplicação não implementa defesas contra SQL Injections, um atacante poderia construir uma entrada do tipo `Gifts'+OR+1=1--` e colocá-la na URL:
```
https://insecure-website.com/products?category=Gifts'+OR+1=1--
```

Isso resultado na query:
``` SQL
SELECT * FROM products WHERE category = 'Gifts' OR 1=1--'
```
_Obs.: o `+` transforma-se em espaço_

Nesse caso, a consulta quer obter todas as informações (*) da tabela de produtos ("products"), mas só da categoria "Gifts" **ou 1 = 1**. Num primeiro momento isso pode parecer estranho, mas essa query está buscando todas as informações da tabela de produtos de **todos** os produtos, porque a condição para um produto ser selecionado pela consulta é que ele deve ser da categoria "Gifts" ou **1 deve ser igual à 1, o que sempre é verdade!**. Dessa forma, o atacante recebe como resposta todas as informações da tabela produtos.

Além disso, note que há um `--` ao final da entrada do atacante. Isso representa, em certos bancos de dados (e nesse caso), um comentário. Logo, tudo que estiver escrito após isso será considerado um comentário. Isso é necessário para que a _query_ termine com o código do atacante e ignore todo o resto. Por exemplo, se a consulta fosse 
``` SQL
SELECT * FROM products WHERE category = '<entrada_do_atacante>' AND (price < 100)
```

Se o resto da consulta (`' AND (price < 100)`) não for comentado, o atacante não obterá tudo que quer ou a consulta dará erro. Entretanto, se houver um `--` ao final da entrada, não haverá problemas (`blabla' OR 1=1 --`): 
``` SQL
SELECT * FROM products WHERE category = 'blabla' OR 1=1 --' AND (price < 100)
```

### Exemplo 2: acessando uma conta de administrador sem saber a senha

Consider an application that lets users log in with a username and password. If a user submits the username wiener and the password bluecheese, the application checks the credentials by performing the following SQL query:

``` SQL
SELECT * FROM users WHERE username = 'wiener' AND password = 'bluecheese'
```

If the query returns the details of a user, then the login is successful. Otherwise, it is rejected.

Here, an attacker can log in as any user without a password simply by using the SQL comment sequence -- to remove the password check from the WHERE clause of the query. For example, submitting the username administrator'-- and a blank password results in the following query:

``` SQL
SELECT * FROM users WHERE username = 'administrator'--' AND password = ''
```

This query returns the user whose username is administrator and successfully logs the attacker in as that user.

## Mais:
- [SQL Injection UNION Attack](https://portswigger.net/web-security/sql-injection/union-attacks)


https://portswigger.net/web-security/sql-injection

https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/

https://www.w3schools.com/sql/sql_injection.asp

https://owasp.org/www-community/attacks/SQL_Injection

https://www.acunetix.com/websitesecurity/sql-injection/