# desafio-dio-sistema-bancario
Desafio de projeto da plataforma [DIO](https://web.dio.me/) - Construindo um sistema bancário em Python

## Objetivo:

Criar um sistema bancário com as 3 operações: sacar, depositar e visualizar o extrato bancário.

## Requisitos:

* Utilizar a linguagem **Python**

### 1. Operação de Depósito

* Depositar valores positivos
* Armazenar todas operações de depósito para listar no extrato

### 2. Operação de Saque

* Limitar a quantidade de saques diários em 3
* Limitar o valor de cada operação de saque em R$ 500,00
* Caso não tenha saldo em conta, informar que a operação não poderá ser realizada
* Armazenar todas operações de saque para listar no extrato

### 3. Operação de Extrato

* Listar todas as operações de Depósito e Saques realizadas na conta
* No fim da listagem, mostrar o saldo atual da conta
* Se o extrato estiver em branco, mostrar mensagem informando que não foram realizadas movimentações
* Exibir valores no formato: ***R$ xxx.xx***


Código:

```python

saldo = 0.00
extrato = []
saques = 0
SAQUES_MAX_QTD = 3
SAQUES_MAX_VALOR = 500.00

opcao = -1
while opcao!=0:
    opcao = int(input(">> Opcoes 1.Deposito 2.Saque 3.Extrato 0.Sair: "))

    if opcao==1:
        valor = float(input("Informe o valor do depósito: "))
        if valor > 0:
            saldo += valor
            extrato.append(f"Deposito: R$ {valor:.2f}")
        else:
            print("Valor de depósito inválido.")

    elif opcao==2:
        valor = float(input("Informe o valor do saque: "))
        if saques > SAQUES_MAX_QTD:
            print(f"Quantidade de saques excedeu o limite diário.")
        elif valor > SAQUES_MAX_VALOR:
            print(f"Valor excedeu o limite por saque.")
        elif valor > saldo:
            print("Não será possível realizar esta operação por falta de saldo.")
        elif valor > 0:
            saldo -= valor
            extrato.append(f"Saque: R$ {valor:.2f}")
            saques -= 1
        else:
            print("Valor de saque inválido.")

    elif opcao==3:
        print("\n" + " EXTRATO ".center(40, "="))
        if len(extrato)==0:
            print("Não foram realizadas movimentações.")
        else:
            for m in extrato:
                print(m)
            print(f"\nSaldo atual: R$ {saldo:3.2f}")
        print("=".center(40, "="), end="\n")

    elif opcao ==0:
        break

    else: 
        print("Operação inválida, tente novamente")

```
