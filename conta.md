
menu = '''
------

[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair

------
\n'''

saldo = 0
limite = 500
numero_saques = 0
LIMITE_SAQUES = 3

extrato = '''extrato atual'''

while True:
      

    opcao = int(input(menu))

    if opcao == 1:
        valor_dep = float(input("Quanto deseja depositar:   "))
        
        if valor_dep > 0:
             saldo += valor_dep
             extrato += (f"Depósito: R$ {valor_dep:.2f} \n")
             print(f"O {valor_dep:.2f} está sendo depositado!")
        
        else:
            print("Operação falhou! O valor informado é inválido.")


    elif opcao == 2:
         valor_sac = float(input("Quanto deseja sacar: "))
         
         excedeu_saldo = valor_sac > saldo

         excedeu_limite = valor_sac > limite

         excedeu_saques = numero_saques >= LIMITE_SAQUES

         if excedeu_saldo:
                print("Operação falhou! Você não tem saldo suficiente.")

         elif excedeu_limite:
             print("Operação falhou! O valor do saque excede o limite.")

         elif excedeu_saques:
             print("Operação falhou! Número máximo de saques excedido.")

         elif valor_sac > 0:
             saldo -= valor_sac
             extrato += f"Saque: R$ {valor_sac:.2f}\n"
             numero_saques += 1
             print(f"R$ {valor_sac:.2f} sendo sacado!")

         else:
             print("Operação falhou! O valor informado é inválido.")

    elif opcao == 3:
        print("\n ================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\n Saldo: R$ {saldo:.2f}")
        print("============================================")

    elif opcao == 4:
         break
    
    else:
        print("Operação inválida, por favor selecionae novamente a operação.")
    
