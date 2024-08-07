
# 😎 Projeto de Programação Web II
Este projeto foi desenvolvido como parte da disciplina de Programação Web II. O objetivo é implementar um sistema de cadastro de produtos, categorias e marcas, com funcionalidades de carrinho de compras.


# 🔬 Tecnologias Utilizadas

- PHP
- JavaScript (jQuery)
- CSS
- MySQL

     
  # 🏠 Estrutura do Projeto
  
- `carrinho.php`: Página do carrinho de compras.
- `categoria.php`: Página para cadastro de categorias.
- `index.php`: Página inicial que lista produtos.
- `insere-categoria.php`: Script para inserir uma nova categoria no banco de dados.
- `insere-marca.php`: Script para inserir uma nova marca no banco de dados.
- `insere-produto.php`: Script para inserir um novo produto no banco de dados.
- `marca.php`: Página para cadastro de marcas.
- `pedido.php`: Página que mostra o resumo do pedido.
- `produtos.php`: Página para cadastro de produtos.
- `controller/`: Diretório contendo os scripts PHP que controlam as interações com o banco de dados.
- `css/`: Diretório contendo os arquivos CSS.
- `js/`: Diretório contendo os arquivos JavaScript.

##### Método: Inserir Categoria
- `insere-categoria.php`
```php
include('controller/conexao.php');
$descricao = $_POST['descricao'];
$cad_categoria = "INSERT INTO categoria(DESCRICAO) VALUES ('$descricao')";
if(mysqli_query($mysqli, $cad_categoria)){
    echo "<h1>Categoria cadastrada com sucesso! </h1></br>";
}else{
    echo "Erro: " . $cad_categoria . "</br>" . mysqli_error($mysqli);
}
mysqli_close($mysqli);
```
#### Exemplo de uso: Acesse categoria.php, preencha o formulário com a descrição da categoria e clique em "Cadastrar".

### Método: Inserir Marca

- `insere-marca.php`


```
include('controller/conexao.php');
$descricao = $_POST['descricao'];
$cad_marca = "INSERT INTO marca(DESCRICAO) VALUES ('$descricao')";
if(mysqli_query($mysqli, $cad_marca)){
    echo "<h1>Marca cadastrada com sucesso! </h1></br>";
}else{
    echo "Erro: " . $cad_marca . "</br>" . mysqli_error($mysqli);
}
mysqli_close($mysqli);
```

#### Exemplo de uso: Acesse marca.php, preencha o formulário com a descrição da marca e clique em "Cadastrar".



# 🤠Autor
(https://github.com/miguelitto16)
