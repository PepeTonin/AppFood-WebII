# API - Serviço de pedido de comida em restaurante
## Descrição da aplicação

A aplicação consiste em uma API (Interface de Programação de Aplicação) que pode ser utilizada por clientes para realizar pedidos em um restaurante. O estabelecimento, por sua vez, pode cadastrar categorias de alimentos e produtos que serão disponibilizados para os clientes realizarem os pedidos.

---
### Guia de utilização da aplicação
- O primeiro passo é instalar os módulos Node necessários para rodar a aplicação, para isso basta digitar o seguinte código no terminal `npm install`. _É necessário estar na pasta do projeto para que o código funcione de maneira adequada._
- O segundo passo é iniciar um container no Docker que servirá de host para o banco de dados Mongo. Para iniciar este container, digite o comando `docker run --name “nome do banco” --volume /save/mongo:/data/db -p 27017:27017 -d mongo` no terminal. _Lembre-se de estar na pasta do projeto antes de digitar o comando._
-  **Sistema operacional Windows:** antes de rodar o código é necessário abrir o Docker Desktop, portanto é necessário ter este programa instalado na máquina.
-  **Sistema operacional Linux:** basta rodar o código com o Docker instalado na máquina.
- Com os módulos Node instalados e com o container Docker rodando, basta usar o código `npm run dev` para subir o servidor. Se tudo estiver certo, a mensagem _"🚗Server is runing on http://localhost:3000"_ deverá aparecer no terminal.
- Como não há um cliente, para fazer as requisições em nosso servidor web é necessário utilizar uma aplicação auxiliar, neste caso será utilizado **Postman**, portanto é necessário ter esse aplicativo instalado em sua máquina.
- Com o servidor rodando, o próximo passo é realizar requisições na API usando essa aplicação auxiliar, para isso, abra uma nova requisição (request) no Postman. Nessa página poderemos fazer requisições ao nosso servidor.
### Serviços disponíveis na aplicação
#### Adicionar nova categoria
Para adicionar uma nova categoria é necessário realizar uma requisição do tipo **POST** no endereço: **http://localhost:3000/categories**. No corpo da requisição é necessário conter um JSON seguindo a seguinte estutura:
```
{
	"name": " 'nome-da-categoria' ",
	"icon": " 'icone-da-categoria(pode ser um emoji)' "
}
```
#### Listar categorias existentes
Para listar as categorias existentes basta realizar uma requisição do tipo **GET** no endereço: **http://localhost:3000/categories**. O servidor irá retornar os dados de todas as categorias disponíveis na aplicação, incluindo o _id_, que é incuído pelo serviço de banco de dados que é utilizado pela API. 
#### Adicionar novo produto
Para adicionar um novo produto é necessário realizar uma requisição do tipo **POST** no endereço: **http://localhost:3000/products**. No corpo da requisição é necessário conter um tipo de dado que no aplicativo Postman é denominado _"form-data"_, que seria uma espécie de formulário, este deve ser estruturado da seguinte maneira:

|KEYS|VALUES|
|-|-|
|name|'nome-do-produto' |
|description|'descrição-do-produto' |
|image|**arquivo contendo a imagem do produto** *|
|price|'preço-do-produto'|
|category|'id-da-categoria-do-produto' **|
\* no Postman, é necessário alterar de 'text' para 'file' e então basta adicionar o arquivo contendo a imagem do produto neste campo.
\** basta listar as categorias existentes e copiar o 'id' da categoria desejada para este campo.
#### Listar produtos existentes
método get no endereço: http://localhost:3000/products
#### Listar produtos existentes filtrando por categoria
método get no endereço: http://localhost:3000/"id-da-categoria-desejada"/products
#### Adicionar novo pedido
método post no endereço: http://localhost:3000/orders
raw: json
#### Listar pedidos
método get no endereço: http://localhost:3000/orders
#### Deletar um pedido
método delete no endereço http://localhost:3000/"id-do-pedido-que-se-deseja-deletar"/orders
