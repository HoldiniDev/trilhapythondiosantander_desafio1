# trilhapythondiosantander_desafio1
Primeiro desafio do Bootcamp Python Santander - Criando um Sistema Bancário com Python

"""
DESAFIO #1 - CRIAR UM SISTEMA BANCÁRIO

PREMISSAS:
1. Criar um sistema bancário que realize as seguintes operações: Saque, Depósito e Extrato - OK;
2. Trabalhar apenas com 1 usuário - não precisando informar dados de agência e conta - OK;
3. Todos os depósitos devem ser armazenados em uma variável, não podendo receber valores negativos - OK;
4. O sistema deve permitir realizar 3 saques diários com limite máximo de R$ 500,00 por saque - OK;
5. Caso o usuário não tenha saldo suficiente, exibir uma mensagem que não foi possível realizar o saque por falta de saldo - OK;
6. Todoso os saques devem ser armazenados em uma variável - OK.
7. Os depósitos e saques serão exibidos na operação de Extrato - ok
8. A operação de Extrato deverá listar todos os saques e depósitos realizados e o saldo anterior e atual da conta.

Data da versão 1: 25/06/2025
Autor: Gabriel S.

"""

menu = """
################ SISTEMA BANCÁRIO 1.0 ################
    1. [d] Depósito
    2. [s] Saque
    3. [e] Extrato
    4. [f] Finaliza
######################################################    
"""

## Inicializa as variaveis
saldo = 0
count = 0
extrato_depositos = """
######################################################
                EXTRATO DA CONTA
######################################################


"""

## Exibe o menu inicial
print(menu)

## Insere a opção desejada
while True:
    opcao = input(str('Digite a opção desejada: '))

## Classifica a opcao

    ## BLOCO DEPÓSITO
    if opcao.upper() == 'D':
        print('Você escolheu a opção Depósito')
        valor = int(input('Digite o valor a ser depositado'))
        if valor <= 0:
            print('Você inseriu um valor não permitido para depósito, tente novamente...')
            valor = int(input('Digite o valor a ser depositado'))
        saldo += valor
        print(f'Você depositou {valor} e seu saldo é de R$ {saldo}')

        extrato_depositos += 'Depósito .................... R$ ' + str(valor) + '\n'

    ## BLOCO SAQUE
    elif opcao.upper() == 'S':
        valor = 0
        print('Você escolheu a opção Saque')
        if count > 2:
            print('Você excedeu o número de saques diários em sua conta')
            break
        valor = int(input('Digite o valor a ser sacado'))
        if (valor <= 0 or valor > 500):
            print('Você inseriu um valor incorreto para o saque, tente novamente...')
            break
        elif valor > saldo:
            print('Saldo insuficiente, tente um valor menor...')
            break

        extrato_depositos += 'Saque    .................... R$ ' + str(valor) + '\n'

        saldo -= valor
        print(f'Você sacou {valor} e seu saldo é de R$ {saldo}')

    ## BLOCO EXTRATO
    elif opcao.upper() == 'E':
        print('Você escolheu a opção Extrato')
        extrato_depositos += '\nSaldo    .................... R$ ' + str(saldo) + '\n'
        print(extrato_depositos)

    ## BLOCO FINALIZA SESSÃO
    elif opcao.upper() == 'F':
        print('Fim da Execução, volte sempre')
        break

    ## BLOCO OPÇÃO INVÁLIDA
    elif opcao.upper not in ('D', 'S', 'E', 'F'):
        print('Opção Invalida')
