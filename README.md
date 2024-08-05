# Sistema de Carrinho de Compras

Este projeto é um sistema de carrinho de compras desenvolvido como parte do curso de Programação Web II. O sistema inclui funcionalidades de cadastro e visualização de produtos, categorias e marcas.

## Arquivos do Projeto

### 1. `carrinho.php`
Exibe o conteúdo do carrinho de compras.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Carrinho</title>
  <link rel="stylesheet" href="css/style.css" media="screen" title="no title" charset="utf-8">
  <script type="text/javascript" src="js/jquery-2.1.4.min.js"></script>
  <script type="text/javascript" src="js/script.js"></script>
</head>
<body>
  <header>
    <div class="center">
      <h1>Programação Web II - Carrinho</h1>
      <a href="index.php">Inicial</a>
    </div>
  </header>
  <section id="produtos">
    <div class="center">
      <?php require_once('controller/carrinho-busca.php'); ?>
    </div>
  </section>
</body>
</html>
```
### 2. `categoria.php`
Formulário para cadastro de categorias.

```<?php
include_once('controller/conexao.php');
?>
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="utf-8">
  <title>Cadastro de categoria</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <header>
    <div class="center">
      <h1>Cadastro de produto</h1>
      <a href="index.php" target="_self">Voltar</a>
    </div>
  </header>
  <section id="produtos">
    <form action="insere-categoria.php" method="post">
      <label for="">Descrição:</label>
      <input type="text" name="descricao">
      <input type="submit" value="Cadastrar">
    </form>
  </section>
</body>
</html>
```

### 3. `index.php`
Página inicial que exibe os produtos.

```html

<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Produtos</title>
  <link rel="stylesheet" href="css/style.css" media="screen" title="no title" charset="utf-8">
  <script type="text/javascript" src="js/jquery-2.1.4.min.js"></script>
  <script type="text/javascript" src="js/script.js"></script>
</head>
<body>
  <header>
    <div class="center">
      <h1 style="text-align: center">Programação Web II - Pedido de compra</h1>
      <a href="carrinho.php" target="_blank">Carrinho</a>
    </div>
  </header>
  <section id="produtos">
    <div class="center">
      <?php require_once('controller/produtos-busca.php'); ?>
    </div>
  </section>
</body>
</html>
```

### 4. `insere-categoria.php`
Processa o cadastro de uma nova categoria.


```<?php
include('controller/conexao.php');

$descricao = $_POST['descricao'];

echo "<h3>Descrição: $descricao </h3></br>";

$cad_categoria = "INSERT INTO categoria(DESCRICAO) VALUES ('$descricao')";

if (mysqli_query($mysqli, $cad_categoria)) {
    echo "<h1>Categoria cadastrada com sucesso! </h1></br>";
} else {
    echo "Erro: " . $cad_categoria . "</br>" . mysqli_error($mysqli);
}

mysqli_close($mysqli);
?>
```

### 5. `insere-marca.php`
Processa o cadastro de uma nova marca.


```<?php
include('controller/conexao.php');

$descricao = $_POST['descricao'];

echo "<h3>Descrição: $descricao </h3></br>";

$cad_marca = "INSERT INTO marca(DESCRICAO) VALUES ('$descricao')";

if (mysqli_query($mysqli, $cad_marca)) {
    echo "<h1>Marca cadastrada com sucesso! </h1></br>";
} else {
    echo "Erro: " . $cad_marca . "</br>" . mysqli_error($mysqli);
}

mysqli_close($mysqli);
?>
```

6. insere-produto.php
Processa o cadastro de um novo produto.


<?php
include_once('controller/conexao.php');

$categoria = $_POST['seleciona_categoria'];
$marca = $_POST['seleciona_marca'];
$nome_produto = $_POST['nome'];
$descricao = $_POST['descricao'];
$estoque = $_POST['estoque'];
$preco = $_POST['preco'];

$grava_produto = "INSERT INTO produtos(`IDCATEGORIA`, `IDMARCA`, `NOME`, `DESCRICAO`, `ESTOQUE`, `PRECO`) VALUES ('$categoria','$marca','$nome_produto','$descricao','$estoque','$preco')";

$result_gravacao = mysqli_query($mysqli, $grava_produto);

if (mysqli_affected_rows($mysqli) != 0) {
    echo "
    <META HTTP-EQUIV=REFRESH CONTENT = 'O;URL=produtos.php'>
    <script type=\"text/javascript\">
    alert('Produto cadastrado com sucesso');
    </script>
    ";
} else {
    echo "
    <META HTTP-EQUIV=REFRESH CONTENT = 'O;URL=produtos.php'>
    <script type=\"text/javascript\">
    alert('Produto não cadastrado');
    </script>
    ";
}
?>
