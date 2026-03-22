rom rich import print
from rich.panel import Panel

class Churrasco:
    consumo_padrao = 0.400 
    preco_kg = 50.00

    def __init__(self, titulo, quant):
        self.titulo = titulo
        self.participantes = int(quant) 

    def __str__(self):
        return f"Esse é o {self.titulo} com {self.participantes} pessoas participando."

    def calcular_qtd_carne(self):
        return self.participantes * self.consumo_padrao

    def calcular_custo_total(self):
        return self.calcular_qtd_carne() * self.preco_kg

    def calcular_custo_individual(self):
        
        if self.participantes == 0:
            return 0
        return self.calcular_custo_total() / self.participantes

    def analisar(self):
       
        conteudo = (
            f"Analisando: [bold]{self.titulo}[/bold]\n"
            f"Convidados: {self.participantes}\n"
            f"Consumo por pessoa: {self.consumo_padrao:.3f}kg | Preço/Kg: R$ {self.preco_kg:.2f}\n"
            f"----------------------------------------\n"
            f"Recomendação de compra: [green]{self.calcular_qtd_carne():.3f}kg[/green]\n"
            f"Custo Total: [yellow]R$ {self.calcular_custo_total():,.2f}[/yellow]\n"
            f"Custo por Pessoa: [cyan]R$ {self.calcular_custo_individual():,.2f}[/cyan]"
        )

        painel = Panel(conteudo, title="Resumo do Churrasco", expand=False)
        print(painel)



nome_evento = input("Dê um nome para o churrasco: ")
qtd_pessoas = input("Quantas pessoas irão participar? ")


c1 = Churrasco(nome_evento, qtd_pessoas)
c1.analisar()
