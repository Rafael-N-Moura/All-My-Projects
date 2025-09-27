# Visão Geral

Budega Online é o maior projeto que eu desenvolvi até então. A ideia surgiu quando meu pai abriu um pequeno comércio no começo da pandemia, o meu objetivo era prover um meio aos clientes de realizarem suas compras sem a necessidade de frequentarem o estabelecimento físico. Para o desenvolvimento utilizei o Firebase e Provider como gerenciador de estado. Mesmo sendo um app só, várias funcionalidades são restritas à aqueles registrados como administradores. Dessa forma, a aplicação se comporta como se existisse um app para os clientes e outro para o gerente, mas em um só.

# Telas

## Tela de Login e Tela de Registro

São telas simples com lógicas simples. Nesse contexto, o que temos são basicamente Cards contendo TextFormFields com seus devidos códigos de validação. O cadastro, login com e-mail e senha, além da recuperação de senha foram bastantes facilitados pelos métodos que já existem no Firebase Auth. Por outro lado, o login com Facebook demandou um processo extenso de configuração, apesar do package Flutter Facebook Login fazer parte do serviço, ainda foi necessário que um tempo fosse gasto no site do Facebook para desenvolvedores. Especialmente, tive problemas com a configuração das chaves de acesso quando o app foi publicado na Google Play. Porém, todos esses problemas foram resolvidos.

<img src="https://user-images.githubusercontent.com/68339043/149008369-79ffa15d-228d-4319-9f1e-1a4383856c99.jpg" width="30%"></img> <img src="https://user-images.githubusercontent.com/68339043/149008539-0a304f35-0401-4c90-81c8-a33fbf7f299d.jpg" width="30%"></img> 

## Telas relacionadas aos produtos

Acessando o drawer e selecionando a opção "Produtos" os clientes têm acesso a uma tela com todos os produtos criados. A tela de produtos consiste basicamente de uma ListView que leva em conta uma lista filtrada a partir dos produtos que são buscados do Firebase. O filtro funciona a partir da pesquisa que pode ser feita pelo usuário tocando no ícone de lupa na parte de actions do AppBar. Os produtos são buscados do Firebase quando o ProductManager é instaciado, o que quer dizer que uma alteração só sera vista pelos clientes quando o app for reiniciado, essa opção foi escolhida visando diminuir às requisições ao banco de dados, levando em consideração que os custos são cobrados por uso e também levando em consideração que o esperado é que os produtos sejam cadastrados todos de uma vez no começo e não sejam editados com frequência. A terceira imagem represetna como a lista muda quando uma pesquisa é feita.

Tocando nos cards dos produtos a um usuário normal só é permitido visualizar as informações básicas do mesmo e adicionar ao carinho, já a um usuário registrado como administrador é possiível editar as informações do produto ou deletá-lo. Quando um produto é deletado, ele não é excluído do banco de dados e sim marcado com uma tag, dessa forma, problemas são evitados caso um cliente tenha comprado um produto antes dele ser apagado por um administrador, já que o produto permanecerá no seu histórico de pedidos. Todo o código pode ser encontrado no repositório cujo link está no final desse arquivo.

Quando um produto é criado os packages Image Picker e Image Cropper foram utilizados para permitir a seleção da imagem. Nesse contexto, é feito o upload da imagem para o Storage do Firebase e o link é vinculado ao produto. Várias imagens podem ser relacionadas ao mesmo produto e o package Carousel Pro foi utilizado para mostrá-las aos usuários.

<img src="https://user-images.githubusercontent.com/68339043/149051106-5bda3094-42aa-44a6-8d28-7ce73c1d4346.jpg" width="30%"></img> <img src="https://user-images.githubusercontent.com/68339043/149051162-4fe5381e-046c-463b-8029-2588234aec6a.jpg" width="30%"></img> <img src="https://user-images.githubusercontent.com/68339043/149051183-407c9460-112b-42e0-8092-96d71aaf973e.jpg" width="30%"></img> <img src="https://user-images.githubusercontent.com/68339043/149051235-99970c32-296b-4f89-aaec-1071aa87f79c.jpg" width="30%"></img> <img src="https://user-images.githubusercontent.com/68339043/149051256-6a933843-aa64-431e-8e97-6fadf7643229.jpg" width="30%"></img> <img src="https://user-images.githubusercontent.com/68339043/149051285-e175991e-0afa-4d1d-a830-1c31de512f7a.jpg" width="30%"></img> 

# Links

* [Playstore](https://play.google.com/store/apps/details?id=br.com.rnmoura.projeto_budega)
* [Repositório](https://github.com/Rafael-N-Moura/Projeto-Loja)
