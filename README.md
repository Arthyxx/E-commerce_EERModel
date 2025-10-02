# 📦 Modelo EER - E-commerce

Este repositório contém o **modelo EER (Enhanced Entity-Relationship)** de um sistema de **E-commerce**, desenvolvido como parte de um desafio prático.  
O objetivo é representar de forma clara as entidades, relacionamentos e regras de negócio essenciais para um E-commerce.

---

## 📝 Descrição do Projeto

O modelo contempla os principais elementos de um ambiente de **E-commerce**, incluindo clientes, pedidos, produtos, fornecedores, estoques, vendedores terceiros, entregas e formas de pagamento.

Além disso, foram aplicados refinamentos solicitados no desafio:
- **Cliente PJ e PF** → Um cliente pode ser Pessoa Física **ou** Pessoa Jurídica, nunca os dois ao mesmo tempo.  
- **Pagamento** → Pode ter cadastrada mais de uma forma de pagamento (ex.: Boleto, Cartão, Dois Cartões).  
- **Entrega** → Possui status e código de rastreio associados ao pedido.  

---

## 📊 Estrutura do Modelo

### Entidades principais
- **Cliente**
  - `idCliente` (PK)  
  - `Nome`  
  - `Endereço`  
  - `CPF` / `CNPJ`  
  - `TipoCliente` ENUM('PF','PJ')  

- **Pedido**
  - `idPedido` (PK)  
  - `Status` (ENUM)  
  - `Descrição`  
  - FK para **Cliente**  

- **Produto**
  - `idProduto` (PK)  
  - `Categoria`  
  - `Descrição`  
  - `Valor`  

- **Fornecedor**
  - `idFornecedor` (PK)  
  - `Razão Social`  
  - `CNPJ`  

- **Entrega**
  - `idEntrega` (PK)  
  - `Status` (ENUM)  
  - `Código de Rastreio`  
  - FK para **Pedido**

---

### Relacionamentos principais
- **Pedido ↔ Produto**  
  Relação N:M modelada pela tabela `RelacaoPedidoProduto` com atributo `Quantidade`.

- **Fornecedor ↔ Produto**  
  Relação N:M pela tabela `DisponibilizandoProduto`.

- **Estoque ↔ Produto**  
  Relação N:M pela tabela `Estoque_has_Produto`.

- **TerceiroVendedor ↔ Produto**  
  Relação N:M pela tabela `ProdutosPorVendedor`.

---

## 🚀 Como usar este projeto
1. Clone o repositório.  
2. Abra o modelo no seu **MySQL Workbench** ou ferramenta de modelagem EER.  
3. Analise as entidades, relacionamentos e constraints aplicadas.  
4. Utilize como base para implementação de um banco de dados relacional para e-commerce.

---

## 📌 Tecnologias
- MySQL Workbench (Modelagem EER)
- SQL

---

## 👨‍💻 Autor
Projeto desenvolvido como parte de desafio educacional da **DIO - Digital Innovation One**.  
