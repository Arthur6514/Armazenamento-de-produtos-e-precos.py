🛒 Analisador de Preços em Python

Este é um script simples em Python desenvolvido para coletar nomes e preços de produtos, realizando cálculos estatísticos e filtragem de dados em tempo real.

🚀 Funcionalidades

O programa permite ao usuário cadastrar diversos produtos e, ao encerrar, apresenta:

Total de produtos cadastrados.

Média de preço de todos os itens.

Identificação do(s) produto(s) mais caro(s) e mais barato(s).

Contagem de produtos que custam mais de R$ 1.000,00.

🛠️ Tecnologias Utilizadas

Python 3

Biblioteca time

Métodos de lista (append, sum, max, min)

📋 Como executar

Certifique-se de ter o Python instalado.

Execute o script no terminal:

python Armazenamento-de-produtos-e-precos.py


💻 Código Fonte

Abaixo está a implementação completa. Note que a indentação (os espaços no início das linhas) é o que faz o código funcionar corretamente:

from time import sleep

# Declaração de variáveis
produtos = list()
precos = list()
continuar = 'S'
c = c1 = 0
media = 0.0

# Estrutura do código
while True:
    produtos.append(str(input('Digite o nome do produto: ')))
    precos.append(float(input('Digite o preço do produto: ')))
    continuar = str(input('Deseja continuar? [S/N] ')).upper()
    
    while continuar not in ['S', 'N']:
        continuar = str(input('Resposta inválida. Digite novamente: ')).upper()
    
    print()
    c += 1
    media = sum(precos) / len(precos)

    if continuar == 'N':
        print('Encerrando...')
        sleep(1)
        print('PROGRAMA ENCERRADO!')
        break

print()

# Apresentação dos dados
print(f'Quantidade de produtos cadastrados: {c}')
print(f'Média dos preços: {media:.2f}')
print('Produtos mais caros: ', end='')

produtoMaisCaro = max(precos)
for i in range(0, len(precos)):
    if (precos[i]) == produtoMaisCaro:
        print(produtos[i], end=' ')

print('\nProdutos mais baratos: ', end='')

produtoMaisBarato = min(precos)
for i in range(0, len(precos)):
    if (precos[i]) == produtoMaisBarato:
        print(produtos[i], end=' ')

for preco in precos:
    if (preco > 1000.00):
        c1 += 1

print(f'\nQuantidade de produtos que custam mais de R$ 1000.00: {c1}')
