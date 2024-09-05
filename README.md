# Atividade-POO---Conta-Corrente
Estudo


class ContaCorrente {  
  double saldo;

  ContaCorrente(this.saldo);

  void sacar(double valor) {
    if (valor > saldo) {
      print('Saque negado, saldo em conta corrente menor do que o valor de saque!');
    } else {
      saldo -= valor;
      print('Saque realizado com sucesso! Saldo atual: \$${saldo}');
    }
  }

  void depositar(double valor) {
    saldo += valor;
    print("Depósito realizado com sucesso! Saldo atual: \$${saldo}");
  }
}

class ContaEspecial extends ContaCorrente {
  double limite;

  ContaEspecial(double saldo, this.limite) : super(saldo);

  @override
  void sacar(double valor) {
    if (valor > saldo + limite) {
      print("Saque negado, valor maior do que saldo + limite!");
    } else {
      saldo -= valor;
      print("Saque realizado com sucesso! Saldo atual: \$${saldo}");
    }
  }
}

class Cliente {
  String nome;
  ContaCorrente conta;

  Cliente(this.nome, this.conta);
}

void main() {
  
  Cliente cliente01 = Cliente('Beatriz', ContaCorrente(5000));
  Cliente cliente02 = Cliente('Rodrigo', ContaEspecial(18000, 5000));

 
  print('${cliente01.nome} - Conta Corrente:');
  cliente01.conta.depositar(1000);
  cliente01.conta.sacar(200);
  cliente01.conta.sacar(500);

 
  print('${cliente02.nome} - Conta Especial:');
  cliente02.conta.depositar(1000);
  cliente02.conta.sacar(200);
  cliente02.conta.sacar(5000);  
}
