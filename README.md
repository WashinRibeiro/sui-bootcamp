# 📝 Todo List - Sui Bootcamp

Sistema de gerenciamento de tarefas construído na blockchain Sui usando Move.

## 🚀 Deployment

### Mainnet
- **Package ID:** `0x2e8b6684ea085b24742c7582f838427ef3dc6a5ffccaba915fe8abe0eede5663`
- **Explorer:** [Suiscan](https://suiscan.xyz/mainnet/object/0x2e8b6684ea085b24742c7582f838427ef3dc6a5ffccaba915fe8abe0eede5663)
- **Move Registry:** [View Package](https://www.moveregistry.com/package/0x2e8b6684ea085b24742c7582f838427ef3dc6a5ffccaba915fe8abe0eede5663)

### Devnet
- **Package ID:** `0x3b09363f683e28db190b39eb022643b46038bce8f90cd4b64b7288396acd46ae`
- **Explorer:** [Suiscan Devnet](https://suiscan.xyz/devnet/object/0x3b09363f683e28db190b39eb022643b46038bce8f90cd4b64b7288396acd46ae)

## 📋 Funcionalidades

- ✅ Criar nova lista de tarefas (`new`)
- ✅ Adicionar item à lista (`add_item`)
- ✅ Remover item por índice (`remove`)
- ✅ Deletar lista completa (`delete`)

## 🛠️ Tecnologias

- **Sui Move** - Linguagem de programação para smart contracts
- **Sui Blockchain** - Blockchain de alta performance
- **Move 2024 Edition** - Versão mais recente do Move

## 📦 Estrutura do Projeto

```
sui-bootcamp/
├── todo_list/
│   ├── sources/
│   │   └── todo_list.move
│   ├── Move.toml
│   └── Move.lock
├── LICENSE
└── README.md
```

## 🔧 Instalação e Uso

### Pré-requisitos

- [Sui CLI](https://docs.sui.io/build/install) instalado
- Carteira Sui configurada

### Build do Projeto

```bash
cd todo_list
sui move build
```

### Publicar na Devnet

```bash
# Configurar devnet
sui client new-env --alias devnet --rpc https://fullnode.devnet.sui.io:443
sui client switch --env devnet

# Obter tokens de teste
sui client faucet

# Verificar saldo
sui client gas

# Publicar
sui client publish --gas-budget 100000000
```

### Publicar na Mainnet

```bash
# Configurar mainnet
sui client new-env --alias mainnet --rpc https://fullnode.mainnet.sui.io:443
sui client switch --env mainnet

# Verificar saldo
sui client gas

# Publicar
sui client publish --gas-budget 100000000
```

## 📖 Como Usar

### Criar uma nova lista

```bash
sui client call \
  --package 0x2e8b6684ea085b24742c7582f838427ef3dc6a5ffccaba915fe8abe0eede5663 \
  --module todo_list \
  --function new \
  --gas-budget 10000000
```

### Adicionar um item

```bash
sui client call \
  --package 0x2e8b6684ea085b24742c7582f838427ef3dc6a5ffccaba915fe8abe0eede5663 \
  --module todo_list \
  --function add_item \
  --args <TODO_LIST_OBJECT_ID> "Minha primeira tarefa" \
  --gas-budget 10000000
```

### Remover um item

```bash
sui client call \
  --package 0x2e8b6684ea085b24742c7582f838427ef3dc6a5ffccaba915fe8abe0eede5663 \
  --module todo_list \
  --function remove \
  --args <TODO_LIST_OBJECT_ID> 0 \
  --gas-budget 10000000
```

## 📝 Estrutura do Código

```move
public struct TodoList has key, store {
    id: UID,
    items: vector<String>,
}

// Criar nova lista
public fun new(ctx: &mut TxContext)

// Adicionar item
public fun add_item(list: &mut TodoList, item: String)

// Remover item por índice
public fun remove(list: &mut TodoList, index: u64)

// Deletar lista
public fun delete(list: TodoList)
```

## 🔗 Links Úteis

- [Documentação Sui](https://docs.sui.io/)
- [Move Book](https://move-book.com/)
- [Sui Examples](https://github.com/MystenLabs/sui/tree/main/examples)
- [Move Registry](https://www.moveregistry.com/)

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

⭐ Desenvolvido durante o Sui Bootcamp
