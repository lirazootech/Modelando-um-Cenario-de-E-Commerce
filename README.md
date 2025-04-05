# Modelando o Cenário de E-Commerce

## 📋 **Descrição do Projeto**  
Este projeto tem como objetivo modelar e implementar um sistema de E-Commerce usando boas práticas de modelagem de dados. A ideia é criar um banco de dados estruturado que gerencie clientes, produtos, vendedores, fornecedores, pedidos, entregas e formas de pagamento, com relacionamentos claros entre essas entidades.

---

## 📐 **Estrutura Conceitual**  
A modelagem segue os seguintes conceitos principais:

- **Cliente:** Representa pessoas físicas ou jurídicas cadastradas na plataforma para realizar pedidos.  
- **Produto:** Itens disponíveis para venda na plataforma. Eles podem ser fornecidos por empresas ou vendidos por vendedores autônomos.  
- **Pedido:** É gerado pelos clientes e vinculado aos produtos adquiridos, formas de pagamento e informações de entrega.  
- **Entrega:** Refere-se ao processo logístico que acompanha o status e rastreamento dos pedidos.  
- **Fornecedor:** Empresas responsáveis pelo abastecimento dos produtos na plataforma.  
- **Vendedor Autônomo:** Usuários independentes que utilizam a plataforma para vender produtos próprios.  
- **Forma de Pagamento:** Métodos de pagamento oferecidos, como Pix, cartão de crédito e boleto bancário.

---

## 🛠️ **Entidades e Relacionamentos**  

### **Entidades**
1. **Cliente:**  
   Inclui informações como nome, CPF/CNPJ, endereço e telefone.  

2. **Produto:**  
   Contém nome, descrição, preço e estoque, e está associado a fornecedores e vendedores autônomos.  

3. **Fornecedor:**  
   Empresas que fornecem os produtos disponíveis na plataforma.  

4. **Vendedor Autônomo:**  
   Usuários independentes que vendem produtos na plataforma.  

5. **Pedido:**  
   Registra as compras realizadas pelos clientes, vinculando os itens adquiridos, a forma de pagamento e o processo de entrega.  

6. **Entrega:**  
   Acompanha o transporte e status de cada pedido.  

7. **Forma de Pagamento:**  
   Gerencia os métodos de pagamento disponíveis.  

8. **Item_Pedido:**  
   Entidade associativa que vincula produtos aos pedidos, incluindo quantidade adquirida e valores por item.  

9. **Vendedor_Produto:**  
   Entidade associativa que gerencia o relacionamento N:M entre vendedores autônomos e produtos.

---

### **Relacionamentos**
- **Cliente gera Pedido (1:N)**  
- **Pedido contém Item_Pedido (1:N)**  
- **Produto é fornecido por Fornecedor (N:1)**  
- **Produto é vendido por Vendedor Autônomo (N:M)** *(via Vendedor_Produto)*  
- **Pedido utiliza Forma de Pagamento (1:N)**  
- **Pedido gera Entrega (1:N)**  

---

## 📦 **Tecnologias Utilizadas**  
- **MySQL:** Banco de dados relacional para gerenciar tabelas e relacionamentos.  
- **Workbench:** Ferramenta gráfica para modelagem e execução de comandos SQL.  

---

## 💡 **Arquitetura do Banco de Dados**  
As tabelas possuem características como:  
- **Chaves primárias auto incrementadas:** Identificadores únicos.  
- **Chaves estrangeiras:** Para garantir integridade referencial entre as tabelas.  
- **Tipos de dados otimizados:** Uso de VARCHAR, DECIMAL, DATETIME, etc.  
- **Estrutura escalável:** Suporte para futuras expansões e ajustes.

---

## 📄 **Comandos Importantes**

### Exemplo: Criação de tabelas com chaves primárias e estrangeiras
```sql
CREATE TABLE Cliente (
    ID_Cliente INT NOT NULL AUTO_INCREMENT,
    Nome VARCHAR(150) NOT NULL,
    CPF_CNPJ VARCHAR(18) NOT NULL,
    Endereco VARCHAR(255),
    Telefone VARCHAR(15),
    PRIMARY KEY (ID_Cliente)
);

CREATE TABLE Produto (
    ID_Produto INT NOT NULL AUTO_INCREMENT,
    Nome VARCHAR(100),
    Descricao TEXT,
    Preco DECIMAL(10,2),
    Quantidade_em_Estoque INT,
    ID_Fornecedor INT,
    PRIMARY KEY (ID_Produto),
    FOREIGN KEY (ID_Fornecedor) REFERENCES Fornecedor(ID_Fornecedor)
);
```
Exemplo: Relacionamento N:M entre Vendedor Autônomo e Produto
```sql
CREATE TABLE Vendedor_Produto (
    ID_VendedorProduto INT AUTO_INCREMENT PRIMARY KEY,
    ID_Vendedor INT NOT NULL,
    ID_Produto INT NOT NULL,
    Preco_Ofertado DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (ID_Vendedor) REFERENCES Vendedor_Autonomo(ID_Vendedor),
    FOREIGN KEY (ID_Produto) REFERENCES Produto(ID_Produto)
);
```
🌟 **Contribuições Sinta-se à vontade para sugerir melhorias ou compartilhar suas ideias!**

  <p align="center">
  Copyright © 2024. Desenvolvido com 🧡 por <a  href="https://lirazootech.vercel.app/">Thays Lira</a>.
  </p>
