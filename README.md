class Banco:
    def __init__(self):
        self.saldo = 0.0
        self.depositos = []
        self.saques = []
        self.num_saques = 0

    def depositar(self, valor):
        if valor <= 0:
            print("Valor inválido para depósito.")
            return

        self.saldo += valor
        self.depositos.append(valor)
        print(f"Depósito de R$ {valor:.2f} realizado com sucesso.")

    def sacar(self, valor):
        if self.num_saques >= 3:
            print("Limite diário de saques atingido.")
            return

        if valor <= 0:
            print("Valor inválido para saque.")
            return

        if valor > 500.0:
            print("Limite de saque por operação é de R$ 500.00.")
            return

        if self.saldo < valor:
            print("Saldo insuficiente para saque.")
            return

        self.saldo -= valor
        self.saques.append(valor)
        self.num_saques += 1
        print(f"Saque de R$ {valor:.2f} realizado com sucesso.")

    def visualizar_extrato(self):
        print("Extrato:")
        print("-" * 30)
        print("Depósitos:")
        for deposito in self.depositos:
            print(f"R$ {deposito:.2f}")
        print("-" * 30)
        print("Saques:")
        for saque in self.saques:
            print(f"R$ {saque:.2f}")
        print("-" * 30)
        print(f"Saldo atual: R$ {self.saldo:.2f}")


# Exemplo de uso do sistema bancário

banco = Banco()

# Depositar R$ 1000.00
banco.depositar(1000.00)

# Sacar R$ 300.00
banco.sacar(300.00)

# Sacar R$ 700.00 (ultrapassa o limite de saque por operação)
banco.sacar(700.00)

# Sacar R$ 400.00
banco.sacar(400.00)

# Sacar R$ 200.00
banco.sacar(200.00)

# Tentar sacar R$ 100.00 (limite diário de saques atingido)
banco.sacar(100.00)

# Visualizar extrato
banco.visualizar_extrato()
