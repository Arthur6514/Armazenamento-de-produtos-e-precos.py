from time import sleep

#declaração de variáveis

produtos = list()
precos = list()
continuar = 'S'
c = c1 = 0
media = 0.0

#estrutura do código

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

#Apresentação dos dados

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
