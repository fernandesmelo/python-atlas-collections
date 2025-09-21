# 🚗 Sistema de Gerenciamento de Carros - MongoDB Atlas

Este projeto demonstra como criar e gerenciar coleções no MongoDB Atlas usando Python, com foco em um sistema de concessionária de carros.

## 📋 Descrição do Projeto

O projeto implementa uma classe `CarDatabase` que permite:
- Conectar ao MongoDB Atlas
- Criar novas coleções para diferentes tipos de carros
- Adicionar carros individuais ou em lote
- Buscar carros com filtros personalizados
- Criar coleções com validação de schema

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**
- **PyMongo** - Driver oficial do MongoDB para Python
- **MongoDB Atlas** - Banco de dados NoSQL na nuvem
- **Jupyter Notebook** - Ambiente de desenvolvimento interativo

## 📦 Instalação

### Pré-requisitos

- Python 3.7 ou superior
- Conta no MongoDB Atlas
- Jupyter Notebook ou VS Code com extensão Python

### Instalação das dependências

```bash
pip install pymongo
```

## 🔧 Configuração

1. **Configure sua string de conexão do MongoDB Atlas:**
   ```python
   uri = "mongodb+srv://seu_usuario:sua_senha@cluster.mongodb.net/?retryWrites=true&w=majority"
   ```

2. **Substitua os dados de conexão pelos seus próprios:**
   - Nome de usuário
   - Senha
   - Nome do cluster

## 📊 Funcionalidades Implementadas

### Métodos da Classe CarDatabase

| Método | Descrição |
|--------|-----------|
| `__init__(uri)` | Inicializa conexão com MongoDB Atlas |
| `conectar_banco(nome_banco)` | Conecta ao banco especificado |
| `criar_colecao_carros(nome_colecao)` | Cria nova coleção para carros |
| `adicionar_carro(nome_colecao, dados_carro)` | Adiciona um carro à coleção |
| `adicionar_multiplos_carros(nome_colecao, lista_carros)` | Adiciona múltiplos carros |
| `buscar_carros(nome_colecao, filtro, campos_projecao)` | Busca carros com filtros |
| `criar_colecao_com_schema(nome_colecao, schema)` | Cria coleção com validação |

### Tipos de Carros Implementados

- **Carros Esportivos**: Ferrari, Lamborghini, Porsche
- **Carros Populares**: Toyota, Honda
- **Carros com Validação**: Schema obrigatório para campos essenciais

## 🛡️ Tratamento de Erros

O código inclui tratamento completo de erros:
- Verificação de conexão com o Atlas
- Validação de existência de coleções
- Captura de exceções em todas as operações

## 📝 Executando o Projeto

1. **Clone ou baixe o projeto**
2. **Abra o arquivo `aula05.ipynb` no Jupyter Notebook ou VS Code**
3. **Execute as células na ordem sequencial:**
   - Instalar pymongo
   - Importar bibliotecas e definir classe
   - Conectar ao banco
   - Executar exemplos de uso
