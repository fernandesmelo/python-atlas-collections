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

## 📁 Estrutura do Projeto

```
Semana5/
├── aula05.ipynb          # Notebook principal com todo o código
└── README.md            # Este arquivo
```

## 🚀 Como Usar

### 1. Inicialização da Classe

```python
from pymongo.mongo_client import MongoClient
from pymongo.server_api import ServerApi

# Criar instância da classe
car_db = CarDatabase(uri)

# Conectar ao banco
car_db.conectar_banco("concessionaria_db")
```

### 2. Criar Coleções

```python
# Criar coleção simples
car_db.criar_colecao_carros("carros_esportivos")

# Criar coleção com validação de schema
car_db.criar_colecao_com_schema("carros_validados", schema_carros)
```

### 3. Adicionar Carros

```python
# Adicionar um carro
carro = {
    "marca": "Ferrari",
    "modelo": "F8 Tributo",
    "ano": 2023,
    "preco": 2500000,
    "disponivel": True
}
car_db.adicionar_carro("carros_esportivos", carro)

# Adicionar múltiplos carros
car_db.adicionar_multiplos_carros("carros_esportivos", lista_carros)
```

### 4. Buscar Carros

```python
# Buscar todos os carros
car_db.buscar_carros("carros_esportivos")

# Buscar com filtros
car_db.buscar_carros(
    "carros_esportivos",
    filtro={"disponivel": True, "preco": {"$lt": 2000000}},
    campos_projecao={"marca": 1, "modelo": 1, "preco": 1, "_id": 0}
)
```

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

## 🔍 Exemplos de Uso

### Exemplo 1: Gerenciar Carros Esportivos

```python
# Criar coleção
car_db.criar_colecao_carros("carros_esportivos")

# Adicionar carros
carros_esportivos = [
    {
        "marca": "Ferrari",
        "modelo": "F8 Tributo",
        "ano": 2023,
        "preco": 2500000,
        "potencia_cv": 720,
        "disponivel": True
    }
]
car_db.adicionar_multiplos_carros("carros_esportivos", carros_esportivos)
```

### Exemplo 2: Busca Avançada

```python
# Buscar carros disponíveis abaixo de R$ 2.000.000
car_db.buscar_carros(
    "carros_esportivos",
    filtro={
        "disponivel": True,
        "preco": {"$lt": 2000000}
    }
)
```

## 📋 Schema de Validação

O projeto inclui validação de schema para garantir integridade dos dados:

```python
schema_carros = {
    "bsonType": "object",
    "required": ["marca", "modelo", "ano", "preco"],
    "properties": {
        "marca": {"bsonType": "string"},
        "modelo": {"bsonType": "string"},
        "ano": {"bsonType": "int", "minimum": 1900, "maximum": 2030},
        "preco": {"bsonType": "number", "minimum": 0},
        "disponivel": {"bsonType": "bool"}
    }
}
```

## 🛡️ Tratamento de Erros

O código inclui tratamento completo de erros:
- Verificação de conexão com o Atlas
- Validação de existência de coleções
- Captura de exceções em todas as operações
- Mensagens informativas com emojis

## 📝 Executando o Projeto

1. **Clone ou baixe o projeto**
2. **Abra o arquivo `aula05.ipynb` no Jupyter Notebook ou VS Code**
3. **Execute as células na ordem sequencial:**
   - Instalar pymongo
   - Importar bibliotecas e definir classe
   - Conectar ao banco
   - Executar exemplos de uso

## 🤝 Contribuição

Para contribuir com o projeto:
1. Faça um fork do repositório
2. Crie uma branch para sua feature
3. Faça commit das mudanças
4. Abra um Pull Request

## 📞 Suporte

Em caso de dúvidas ou problemas:
- Verifique se o pymongo está instalado corretamente
- Confirme se as credenciais do MongoDB Atlas estão corretas
- Execute as células na ordem correta
- Verifique a conexão com a internet

## 📄 Licença

Este projeto foi desenvolvido para fins educacionais como parte do curso de MongoDB Atlas com Python.

---

**Desenvolvido por**: Laércio Fernandes  
**Data**: Setembro 2025  
**Versão**: 1.0
