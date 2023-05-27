### GUIA DE UTILIZAÇÃO DA APLICAÇÃO
- O primeiro passo é instalar os módulos Node necessários para rodar a aplicação, para isso basta digitar o seguinte código no terminal `npm install`. _É necessário estar na pasta do projeto para que o código funcione de maneira adequada._
- O segundo passo é iniciar um container no Docker que servirá de host para o banco de dados Mongo. Para iniciar este container, digite o comando `docker run --name “nome do banco” --volume /save/mongo:/data/db -p 27017:27017 -d mongo` no terminal. _Lembre-se de estar na pasta do projeto antes de digitar o comando._
-  **Sistema operacional Windows:** antes de rodar o código é necessário abrir o Docker Desktop, portanto é necessário ter este programa instalado na máquina.
-  **Sistema operacional Linux:** basta rodar o código com o Docker instalado na máquina.
- Com os módulos Node instalados e com o container Docker rodando, basta usar o código `npm run dev` para subir o servidor. Se tudo estiver certo, a mensagem _"🚗Server is runing on http://localhost:3000"_ deverá aparecer no terminal.
- Como não há um cliente, para fazer as requisições em nosso servidor web é necessário utilizar uma aplicação auxiliar, neste caso será utilizado **Postman**, portanto é necessário ter esse aplicativo instalado em sua máquina.
- Com o servidor rodando, o próximo passo é abrir uma nova requisição (request) no Postman.
#### SERVIÇOS
##### Adicionar nova categoria
método post no endereço: http://localhost:3000/categories
raw: json
##### Listar categorias existentes
método get no endereço: http://localhost:3000/categories
##### Adicionar novo produto
método post no endereço: http://localhost:3000/products
form-data
##### Listar produtos existentes
método get no endereço: http://localhost:3000/products
##### Listar produtos existentes filtrando por categoria
método get no endereço: http://localhost:3000/"id-da-categoria-desejada"/products
##### Adicionar novo pedido
método post no endereço: http://localhost:3000/orders
raw: json
##### Listar pedidos
método get no endereço: http://localhost:3000/orders
##### Deletar um pedido
método delete no endereço http://localhost:3000/"id-do-pedido-que-se-deseja-deletar"/orders