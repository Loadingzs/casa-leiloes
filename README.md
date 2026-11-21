# 🔨 Casa de Leilões — Cadastro e venda de produtos

Aplicação desktop de estudo desenvolvida em **Java Swing e MySQL** para cadastrar produtos, consultar o catálogo e registrar vendas por alteração de status.

## Funcionalidades

- Cadastro de produto com nome e valor.
- Listagem de produtos cadastrados.
- Registro de venda pelo ID do produto.
- Consulta dos produtos com status `Vendido`.
- Validação de campos no cadastro e de valor numérico inteiro.

O escopo implementado está concentrado em produtos e vendas. Cadastro de clientes e disputa de lances são possibilidades de evolução.

## Tecnologias

Java · Swing · JDBC · MySQL · Apache Ant · NetBeans

O projeto está configurado com `javac.source=18` e `javac.target=18`. Utilize um JDK compatível com Java 18 e com a configuração da IDE.

## Como executar

### 1. Clonar e abrir

```bash
git clone https://github.com/Loadingzs/casa-leiloes.git
cd casa-leiloes
```

Abra a pasta como projeto no NetBeans.

### 2. Preparar o MySQL

O repositório não inclui um script SQL. Para uma base local nova, execute o esquema mínimo usado por `ProdutosDAO`:

```sql
CREATE DATABASE IF NOT EXISTS uc11 CHARACTER SET utf8mb4;
USE uc11;

CREATE TABLE produtos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(255) NOT NULL,
    valor INT NOT NULL,
    status VARCHAR(30) NOT NULL
);
```

O valor é tratado como inteiro pelo código atual; não há suporte a centavos nesse campo.

### 3. Configurar a conexão

Em `src/conectaDAO.java`, ajuste a URL JDBC, usuário e senha para seu MySQL local. O banco indicado atualmente é `uc11`.

O diretório `lib/` contém conectores MySQL. Nas propriedades do projeto, confira as referências; prefira um único driver compatível com sua instalação, evitando carregar versões diferentes simultaneamente.

### 4. Iniciar

No NetBeans, selecione **Limpar e Construir** e execute a classe principal `cadastroVIEW`.

Com Apache Ant instalado e as dependências resolvidas, a compilação também pode ser iniciada com:

```bash
ant clean jar
```

## Estrutura

```text
casa-leiloes/
├── src/
│   ├── cadastroVIEW.java   # Entrada e cadastro
│   ├── listagemVIEW.java   # Consulta e venda
│   ├── vendasVIEW.java     # Produtos vendidos
│   ├── ProdutosDTO.java    # Dados do produto
│   ├── ProdutosDAO.java    # Operações SQL
│   └── conectaDAO.java     # Conexão JDBC
├── lib/                   # Drivers MySQL
├── nbproject/             # Configuração NetBeans
└── build.xml              # Build Ant
```

## Verificação manual

1. Cadastre um produto com valor inteiro.
2. Confira sua presença na listagem.
3. Registre a venda e verifique a alteração de status.
4. Abra a consulta de vendidos e confirme o registro.

Ainda não há testes automatizados. Como evolução, o projeto pode receber valores monetários decimais, configuração externa de conexão e testes das operações de persistência.

## Autor

**Maykon Dias** · [GitHub](https://github.com/Loadingzs) · [LinkedIn](https://www.linkedin.com/in/maykondias/)
