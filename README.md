# Python-Desafio-DIO
Desafio do curso de Formação Python Developer

Desafio do sistema bancário

menu_inicial = """
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair
=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3
print("Seja bem vindo!")
while True:

    operacao = input("Escolha a operação que deseja realizar: " + menu_inicial)

    if operacao == "d":
        valor = float(input("Digite o valor que deseja depósitar: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
            print ("Depósito realizado com sucesso.")
            print ("Saldo após a operação: ")
            print (saldo)

        else:
            print("Operação falhou! Valor inválido.")

    elif operacao == "s":
        valor = float(input("Informe o valor do saque: "))

        if valor > saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif valor > limite:
            print("Operação falhou! O valor do saque excede o limite diário de saque.")

        elif numero_saques >= LIMITE_SAQUES:
            print("Operação falhou! Número máximo diário de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1
            print ("Saque realizado, Saldo restante na conta: ")
            print (saldo)

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif operacao == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif operacao == "q":
        print("Até a próxima")
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.") 
