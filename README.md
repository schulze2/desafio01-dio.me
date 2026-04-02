# Sistema Bancário 🏦

Desafio proposto pela **DIO.me** para implementar um sistema bancário básico em Python utilizando conceitos de Programação Orientada a Objetos (POO).

## 📋 Descrição

Este projeto implementa um sistema bancário com funcionalidades de gerenciamento de clientes, contas correntes, depósitos, saques e histórico de transações. O sistema segue os princípios de POO com uso de classes abstratas, herança e encapsulamento.

## 🎯 Funcionalidades

- **Gerenciamento de Clientes**: Criar e manter dados de clientes (Pessoa Física)
- **Contas Correntes**: Criar contas com limite de saque e limite diário de operações
- **Depósitos**: Realizar depósitos em contas de clientes
- **Saques**: Realizar saques com validação de saldo e limite
- **Histórico de Transações**: Registrar e exibir todas as movimentações
- **Menu Interativo**: Interface de linha de comando para operações bancárias

## 🏗️ Estrutura do Projeto

```
desafio01/
├── desafio v1.py       # Versão 1: Apenas as classes base
├── desafio v2.py       # Versão 2: Com menu interativo
└── README.md          # Este arquivo
```

## 📚 Classes Implementadas

### **Cliente**
Classe base para representar clientes do banco.

**Atributos:**
- `endereco`: Endereço do cliente
- `contas`: Lista de contas associadas

**Métodos:**
- `realizar_transacao(conta, transacao)`: Realiza uma transação na conta
- `adicionar_conta(conta)`: Adiciona uma nova conta ao cliente

### **PessoaFisica**
Herda de `Cliente` e representa uma pessoa física.

**Atributos adicionais:**
- `nome`: Nome completo
- `data_nascimento`: Data de nascimento (dd-mm-aaaa)
- `cpf`: CPF (documento de identificação)

### **Conta**
Classe base para contas bancárias.

**Atributos:**
- `saldo`: Saldo da conta (privado)
- `agencia`: Número da agência (padrão: "0001")
- `numero`: Número da conta
- `cliente`: Cliente associado à conta
- `historico`: Histórico de transações

**Métodos:**
- `sacar(valor)`: Realiza um saque
- `depositar(valor)`: Realiza um depósito
- `nova_conta()`: Método de classe para criar nova conta

### **ContaCorrente**
Herda de `Conta` e adiciona limite de saque e restrição diária de saques.

**Atributos adicionais:**
- `limite`: Limite de saque por operação (padrão: R$500)
- `limite_saques`: Número máximo de saques por dia (padrão: 3)

### **Transacao (Abstrata)**
Classe abstrata que define a interface para transações.

**Métodos abstratos:**
- `valor`: Propriedade que retorna o valor da transação
- `registrar(conta)`: Registra a transação na conta

### **Saque**
Implementa transação de saque.

### **Deposito**
Implementa transação de depósito.

### **Historico**
Mantém registro de todas as transações.

**Atributos:**
- `transacoes`: Lista com histórico de transações

**Métodos:**
- `adicionar_transacao(transacao)`: Adiciona uma transação ao histórico

## 🚀 Como Usar

### Usando a Versão 1 (Classes)
Execute o arquivo para validar a estrutura das classes:
```bash
python desafio\ v1.py
```

### Usando a Versão 2 (Menu Interativo)
Execute para usar o sistema completo:
```bash
python desafio\ v2.py
```

### Menu de Operações
```
[d] - Depositar
[s] - Sacar
[e] - Extrato
[nc] - Nova conta
[lc] - Listar contas
[nu] - Novo usuário
[q] - Sair
```

## 📝 Exemplo de Uso

1. **Criar um novo usuário:**
   - Selecione a opção `[nu]`
   - Informe CPF, nome, data de nascimento e endereço

2. **Criar uma conta:**
   - Selecione a opção `[nc]`
   - Informe o CPF do cliente

3. **Realizar um depósito:**
   - Selecione a opção `[d]`
   - Informe o CPF e o valor

4. **Realizar um saque:**
   - Selecione a opção `[s]`
   - Informe o CPF e o valor (respeitando limite e limite diário)

5. **Consultar extrato:**
   - Selecione a opção `[e]`
   - Informe o CPF

6. **Listar contas:**
   - Selecione a opção `[lc]`

## ⚙️ Requisitos de Sistema

- Python 3.7+
- Nenhuma dependência externa

## 🔍 Validações Implementadas

- ✅ Saque apenas com saldo suficiente
- ✅ Saque respeitando limite diário (3 saques)
- ✅ Saque respeitando limite de valor (R$500)
- ✅ Depósito apenas com valores positivos
- ✅ Verificação de cliente antes de operações
- ✅ Histórico completo com data e hora

## 📌 Observações

- Cliente pode ter múltiplas contas (funcionalidade implementada mas parcialmente no menu v2)
- Todas as operações são registradas no histórico com timestamp
- O sistema valida entrada de dados (conversão para float)
- Interface amigável com feedback de operações

## 🎓 Conceitos de POO Aplicados

- **Herança**: `PessoaFisica` herda de `Cliente`, `ContaCorrente` herda de `Conta`
- **Polimorfismo**: Métodos abstratos em `Transacao` implementados em `Saque` e `Deposito`
- **Encapsulamento**: Atributos privados (`_saldo`, `_numero`, etc.) com properties
- **Abstração**: Classe abstrata `Transacao` define interface
- **Composição**: `Cliente` possui `Conta`, `Conta` possui `Historico`

## 🔄 Fluxo de Dados

```
Menu → Operação → Validação → Transação → Histórico → Feedback
```

## 📧 Autor

Desenvolvido como desafio da plataforma **DIO.me**

---

**Última atualização:** 02/04/2026
